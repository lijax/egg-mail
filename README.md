# egg-mail



Email smtp client based on emailjs for egg framework

## Install

```bash
$ npm i egg-mail --save
```

Email Plugin for egg, support egg application send email.

This plugin based on [emailjs](https://github.com/eleith/emailjs)

## Configuration

Change `${app_root}/config/plugin.js` to enable email plugin:

```js
exports.email = {
  enable: true,
  package: 'egg-mail',
};
```

Configure email information in `${app_root}/config/config.default.js`:

**Single Client**

```javascript
config.email = {
  username: *your email account*,
  password: *your email password*,
  host: *you email smtp server ip or domain name*,
  sender: *what accout are you use to send email,like:XXX@XXX.com*,
}
```

## Usage

In controller, you can use `app.email.sendEmail` to send email.

```js
// app/controller/home.js

module.exports = app => {
  return class HomeController extends app.Controller {
    async index() {
      const { ctx, app } = this;
      // sendEmail
      ctx.body = await app.email.sendEmail('Title','Content','Reciver','Attachment');
      // ctx.body = await app.email.sendEmail('test','testContent','test@test.com');
    }
  };
};
```

## Example Attachment Array

```
[
  {data:"<html>i <i>hope</i> this works!</html>", alternative:true},
  {path:"path/to/file.zip", type:"application/zip", name:"renamed.zip"}
]
```
more detail please click [here](https://github.com/eleith/emailjs#example-usage---html-emails-and-attachments)

## Questions & Suggestions

Please open an issue [here](https://github.com/zhouzhi3859/egg-mail/issues).

## License

[MIT](LICENSE)
