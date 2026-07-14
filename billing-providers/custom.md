# Tracking Sales via our API

FirstPromoter allows you to track sales, refunds, upgrades and cancellations through our API.

## Setting Up

To get started, you will need to first set up an endpoint from which you will receive webhook events from your billing provider. Once you are receiving these events on your server, you can then make a request to FirstPromoter to track sales when these events are received.

~~~markdown [g1:Manual]

1. Get your API key from your Settings > Integrations tab > manage API Keys > create a new key or use the existing key you have.
2. Get your Account ID from the Settings > Integrations tab as well.
3. On your backend, you will need to make a POST request to the `https://v2.firstpromoter.com/api/v2/track/sale` endpoint we provide, together with the following parameters.

```plaintext {noCopy}
Parameter     Required                  Description

email         yes if uid is null        email of the lead/sign-up
event_id      yes                       transaction or charge ID.
amount        yes (in cents)            the total sale amount in cents
uid           yes if email is null      uid of the lead added on signup tracking.
plan          no                        customer plan ID from the billing provider.
tid           no                        visitor tracking id.
ref_id        no                        default referral id of the promoter.
```

**For the full list click [here](https://docs.firstpromoter.com/api-reference-v2/api-admin/tracking-api/sales)**

4. The full code will look like this.

```js {noCopy}

//backend.js
const axios = require(&apos;axios&apos;);
...
//this code can go into your payment flow
// to make this cleaner you can extract it into a function

const email = &apos;example@example.com&apos; //replace with actual email
const amount = 1000; //actual amount from payment, e.g., $10.00 is 1000 cents
const event_id = &quot;43eb-83e9-374ea4600556&quot; // actual event id from payment

const params = {
  email: email,
  amount: amount,
  event_id: event_id
};

axios
  .post(&quot;https://v2.firstpromoter.com/api/v2/track/sale&quot;, params, {
    headers: {
      &quot;Content-Type&quot;: &quot;application/json&quot;,
      &quot;Authorization&quot;: &quot;Bearer your_token_here&quot;,
      &quot;Account-ID&quot;: &quot;your_account_id_here&quot;
    },
  })
  .then(function (response) {
    //any action if the request is successful
    console.log(JSON.stringify(response.data));
  })
  .catch(function (error) {
    //any action if the request fails
    console.log(error);
  });

```
~~~

~~~markdown [g1:AI Prompt]

If you'd rather not wire this up by hand, copy the prompt below and paste it into an AI coding tool (e.g. Claude Code) working on this project. Before using it, grab your **API key** and **Account ID** from your FirstPromoter dashboard under **Settings > Integrations** (create a new API key if you don't have one yet).

1. Copy the prompt below.
2. Replace `YOUR_API_KEY` and `YOUR_ACCOUNT_ID` with the values from your dashboard.
3. Paste it into the AI tool's chat/terminal and send it.

```text
Add server-side sale tracking for FirstPromoter to this project&apos;s billing/payment webhook handler.

Find (or create) the endpoint that receives webhook events from our billing provider. In the handler for a successful charge/payment event, make a POST request to https://v2.firstpromoter.com/api/v2/track/sale with a JSON body containing:

- email: the customer&apos;s email (use uid instead if email isn&apos;t available)
- amount: the total sale amount in cents
- event_id: the transaction or charge ID from the billing provider
- plan: (optional) the customer&apos;s plan ID from the billing provider
- tid: (optional) the visitor tracking id, if available

Send these headers with the request:

- Content-Type: application/json
- Authorization: Bearer YOUR_API_KEY
- Account-ID: YOUR_ACCOUNT_ID

Make this call only after confirming the payment succeeded, and don&apos;t let a failure of this request break the webhook handler&apos;s normal response.
```
~~~
