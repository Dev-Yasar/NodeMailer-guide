# Send a html mail using nodejs

First create your Html mail template here [enginemailer](www.enginemailer.com)

[![AGPL License](https://img.shields.io/badge/Made%20by%20%E2%9D%A4%EF%B8%8F-yasar-blue)](http://www.gnu.org/licenses/agpl-3.0)


install dependencies 
```js
npm install express nodemailer 
````

Mailer.js

```js
// reference for packages
const express = require('express');
const nodemailer = require('nodemailer');



// route for send mail
app.get('/sendmail', async (req, res) => {
     
     // the values are from frontend 
     var name = req.body.name;
     var email = req.body.email
     
     MailSender(name,email);


	res.json("email send succesfully :)");
})

function MailSender(name,email){

             var EmailTemplate = `<h1> Hi,${name}` this is an test mail</h1> ;  // put your html content

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
