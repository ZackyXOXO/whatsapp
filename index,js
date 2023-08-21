const { Client } = require('whatsapp-web.js')
const qrcode = require('qrcode-terminal')
const quotable = require('quotable')
const translate = require('translate')
const client = new Client();

client.on('qr', (qr) => {
    qrcode.generate(qr, {small : true});
})

client.on('ready', () => {
    console.log('client Siap')
})

client.on('message' ,async  (msg) => {
    if (msg.body == 'ping'){
        msg.reply('pong')
    } else if (msg.body.startsWith("!sticker") && msg.hasMedia && msg.type === "image") {
        const sticker = await msg.downloadMedia();
        client.sendMessage(msg.from, sticker, { sendMediaAsSticker: true });
      } else if (msg.body === 'kata hari ini'){
        const aNewQuote = await quotable.getRandomQuote();
        //console.log(aNewQuote.content)};
        msg.reply( aNewQuote.content + " " + "-" + " " + aNewQuote.author )}
})

client.initialize();