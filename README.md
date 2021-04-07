# Verizon HTML Promo Email

## Project Context

Context: This is a fully customizable HTML Newsletter Email / Template written from scratch. I've setup data entry points that allow anybody to only change the image files and descriptions. This way, the same template can be used and rotated in an HTML email marketing campaign.

The styling has been written with Sass. The Sass is then compiled and the images are minified for optimal performance into a master HTML file. The master index.html has everything compiled to inline HTML in order to work in all email clients. 😎

## What was learned

- Pixel Perfect Design Replication
- How to set variables and @mixins for brand consistent code
- How to set a JS data file to easily change data for email campaigns
- Create proper table layouts for image and summary sections
- Writing reusable code for minimal editing when changing content

## Technologies

Project is created with:

- HTML
- CSS
- SASS
- Javascript
- Gulp
- Json

## See the email below!

[Link to HTML Newsletter Email](https://github.com/Rallanvila/Verizon-Promo-Email)

## Build Commands

Run `npm start` to kick off the build process. A new browser tab will open with a server pointing to your project files.

Run `npm run build` to inline your CSS into your HTML along with the rest of the build process.

Run `npm run litmus` to build as above, then submit to litmus for testing. _AWS S3 Account details required (config.json)_

Run `npm run mail` to build as above, then send to specified email address for testing. _SMTP server details required (config.json)_

Run `npm run zip` to build as above, then zip HTML and images for easy deployment to email marketing services.

### Speeding Up Your Build

If you create a lot of emails, your build can start to slow down, as each build rebuilds all of the emails in the
repository. A simple way to keep it fast is to archive emails you no longer need by moving the pages into `src/pages/archive`.
You can also move images that are no longer needed into `src/assets/img/archive`. The build will ignore pages and images that
are inside the archive folder.

## Litmus Tests (config.json)

Testing in Litmus requires the images to be hosted publicly. The provided gulp task handles this by automating hosting to an AWS S3 account. Provide your Litmus and AWS S3 account details in the `example.config.json` and then rename to `config.json`. Litmus config, and `aws.url` are required, however if you follow the [aws-sdk suggestions](http://docs.aws.amazon.com/AWSJavaScriptSDK/guide/node-configuring.html) you don't need to supply the AWS credentials into this JSON.

```json
{
	"aws": {
		"region": "us-east-1",
		"accessKeyId": "YOUR_ACCOUNT_KEY",
		"secretAccessKey": "YOUR_ACCOUNT_SECRET",
		"params": {
			"Bucket": "elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
		},
		"url": "https://s3.amazonaws.com/elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
	},
	"litmus": {
		"username": "YOUR_LITMUS@EMAIL.com",
		"password": "YOUR_ACCOUNT_PASSWORD",
		"url": "https://YOUR_ACCOUNT.litmus.com",
		"applications": [
			"ol2003",
			"ol2007",
			"ol2010",
			"ol2011",
			"ol2013",
			"chromegmailnew",
			"chromeyahoo",
			"appmail9",
			"iphone5s",
			"ipad",
			"android4",
			"androidgmailapp"
		]
	}
}
```

## Manual email tests (config.json)

Similar to the Litmus tests, you can have the emails sent to a specified email address. Just like with the Litmus tests, you will need to provide AWS S3 account details in `config.json`. You will also need to specify to details of an SMTP server. The email address to send to emails to can either by configured in the `package.json` file or added as a parameter like so: `npm run mail -- --to="example.com"`

```json
{
	"aws": {
		"region": "us-east-1",
		"accessKeyId": "YOUR_ACCOUNT_KEY",
		"secretAccessKey": "YOUR_ACCOUNT_SECRET",
		"params": {
			"Bucket": "elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
		},
		"url": "https://s3.amazonaws.com/elasticbeanstalk-us-east-1-THIS_IS_JUST_AN_EXAMPLE"
	},
	"mail": {
		"to": ["example@domain.com"],
		"from": "Company name <info@company.com",
		"smtp": {
			"auth": {
				"user": "example@domain.com",
				"pass": "12345678"
			},
			"host": "smtp.domain.com",
			"secureConnection": true,
			"port": 465
		}
	}
}
```

For a full list of Litmus' supported test clients(applications) see their [client list](https://litmus.com/emails/clients.xml).

**Caution:** AWS Service Fees will result, however, are usually very low do to minimal traffic. Use at your own discretion.
