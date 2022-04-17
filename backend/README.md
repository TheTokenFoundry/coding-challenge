# Backend Challenge

The Token Foundry is working on building a B2B model crypto trading application. We want to build an API that listens to a MongoDB document for any new orders that may come in. Once a new order has been marked as completed we need to take our fees out of a user's account. For this coding challenge what we want is for you to build a NodeJS, MongoDB backed API with Express. We want you to have one model that looks like the following in this database
```json
{
  name: String,
  email: String,
  totalCost: Number, // this will be in USD
  amountTraded: Number, // this will be the amount of a currency I bought/sold
  completed: String // enum of success, pending, or failed
  totalAfterFee: Number
  feeAmount: Number // in USD
}
```
You can assume you will always have all of those values besides `totalAfterFee` and `feeAmount` in every document. What we want is to listen to our database for when any trade's completed status goes into "success". When that happens we want to take an enviornment variable known as `FEE_AMOUNT` which for this example will be 0.0035 and we want you to calculate the `totalAfterFee` and `feeAmount` and add that data into the document. Once that is done we want to notify our user that we have taken our fee from their account via email. We would like you to send an email using one of these four providers:

* [Amazon SES](http://aws.amazon.com/ses/) - [Simple Send Documentation](http://docs.aws.amazon.com/ses/latest/APIReference/API_SendEmail.html)
* [SendGrid](https://sendgrid.com/user/signup) - [Simple Send Documentation](https://sendgrid.com/docs/API_Reference/Web_API/mail.html)
* [Mailgun](http://www.mailgun.com) - [Simple Send Documentation](http://documentation.mailgun.com/quickstart.html#sending-messages)
* [SparkPost](https://www.sparkpost.com/) - [Developer Hub](https://developers.sparkpost.com/)

We would prefer to send it with AWS SES but we for this example sometimes it fails and if that is the case we would like to know that it failed and try sending the same email with a new provider and then go down the list. We can assume that at least one of them will succeed. You can draft up your own version of an email to send to the customer letting them know the fee amount, the total after the fee and how much they got and thanking them for their business.

The last thing we want is two endpoints, we need an endpoint for a health check to ensure our api is still running successfully. The other thing we need is an endpoint to check all of the updated documents we have put into our database for the last six hours, we need this route to require an API Key as well (don't worry about the server restarting that is okay if it does and also don't worry about multiple versions of this api running, assume there will only be one up at a time). For the API Key feel free to implement it how you like but please document in the README.md how to call the endpoint successfully. Feel free to use an in memory cache, a redis cache, another mongodb call, etc; to solve that problem.

## Tips

Please don't spend more than two hours on this! 

We are looking for good logging! We want to be able to tell when things fail, when things succeed, we want to be able to know looking at the logs how much the fee amount was, how much the total amount was after the fee, etc;.

We would love to see good API documentation in the README.md about what the endpoints are, what the responses are, if there is anything needed in the request body, what the service is doing etc;

Build it as flexible as possible. This API could be leveraged and added to or changed and we want it to be as flexible as possible to support additional changes.

## How to submit

Please email back the person you got the challenge from with all enviornment variables and a github repo link to your project.