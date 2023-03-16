# MINERDPAY---API-MERCADO-PAGO
SIMPLES CODIGO PARA PAGAMENTOS AUTOMATICO VIA MERCADO PAGO 

npm install mercadopago 
npm install qrcode

IMPORTAR MODULO PARA SEU INDEX.JS 


EXEMPLO DE CASE PASSANDO VALORES E GERANDO PAGAMNETO


case 'pagto':
    const value = parseFloat(q);
    if (value <= 0) {
 conn.sendMessage(from, 'Por favor, insira um valor válido para o pagamento.');
 return;
    }
    const mp_payment = new payment(access_token_mp);
    const payment_result = await mp_payment.create_payment(value);
  
    conn.sendMessage(from, {
 text: `𝑴𝑰𝑵𝑬𝑹𝑫 𝑷𝑨𝒀 -  Sistema de Pagamentos.

 💷Valor a pagar estar correto? (confirme antes de pagar)
  
 💷Efetue o pagamento no valor de R$ ${value.toFixed(2)} usando o pix copia e cola abaixo:👇
   \`\`\`
   ${payment_result.copy_paste}
   \`\`\`
   💸💸💸💸💸💸💸💸💸💸  
 `
    });
  
    const interval = setInterval(async () => {
 const paymentStatus = await mp_payment.check_payment();
 if (paymentStatus.status === 'approved') {
   clearInterval(interval);
   conn.sendMessage(from, 'Pagamento confirmado!');
   // Faça o que você precisa fazer aqui após a confirmação do pagamento
 }
    }, 5000);
    break;
    
    
    USO DA CASE 
    
    /pagto 10
    
    RESULTADO 
    
    𝑴𝑰𝑵𝑬𝑹𝑫 𝑷𝑨𝒀 -  Sistema de Pagamentos.

 💷Valor a pagar estar correto? (confirme antes de pagar)
  
 💷Efetue o pagamento no valor de R$ 10.00 usando o pix copia e cola abaixo:👇
 
 
00020126580014br.gov.bcb.pix0136b76aa9c2-2ec4-4110-954e-ebfe34f05b61520400005303986540510.005802BR5908cVpJUcsb6009Sao Paulo62230519mpqrinter13133621796304C364
    
    
