# Send a html mail using nodejs

First create your Html mail template here [enginemailer](www.enginemailer.com)

install dependencies 

```js
npm install express nodemailer 
````

Mailer.js

```nodejs

const express = require('express');
const nodemailer = require('nodemailer');


var EmailTemplate = `hi , ${name}` This is an test mail;  // put your html content

app.get('/sendmail', async (req, res) => {
     
     // the values are from frontend 
     var name = req.body.name;
     var email = req.body.email
     
     MailSender(name,email)  


	res.json(paw);
})

function MailSender(name,email){

            var transporter = nodemailer.createTransport({
              service: 'gmail', //put your mail service
              auth: {
                user: 'mail id',
                pass: 'password'
              }
            });
            var mailOptions = {
              from: 'mail id ',
              to: email,
              subject: 'subject of the mail',
              html: EmailTemp  //html mail template
            };

            transporter.sendMail(mailOptions, function(error, info){
              if (error) {
                console.log(error);
              } else {
                console.log('Email sent: ' + info.response);
              }
            });


}
```
