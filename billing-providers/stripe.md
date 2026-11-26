# Connecting FirstPromoter with Stripe

FirstPromoter allows you to automatically track sales, refunds, upgrades and cancellations from Stripe.

## Setting Up

To get started, you need to follow the below steps:

1. Click on the "Connect Stripe" Button. This will take you to the Stripe marketplace, requesting you to install FirstPromoter.
2. Select your Stripe account and install the app.
3. After the installation is completed, you will be redirected back to this page to finish the setup.

## Switching between test and live mode on Stripe

To switch between test mode and live mode on Stripe you will need to **disconnect and reconnect** to the desired mode.

![stripe environment switch guide](https://gitlab.com/api/v4/projects/55002365/repository/files/images%2Fstripe-environment-switch-guide.gif/raw?ref=main)

## Skipping specific payments

Some Stripe payments should not count as sales, for example a small charge that checks a new card, a hold that is released straight away, or an internal top-up. To have FirstPromoter ignore a payment, add `fp_skip_tracking` to its metadata with the value `true` (`1` and `yes` also work).

Where to add the metadata:

- **One-time charges:** on the PaymentIntent, when you create it. Stripe copies it to the charge. For Stripe Checkout, use `payment_intent_data.metadata`.
- **Subscription invoices:** on the invoice, or on the subscription.

```js {noCopy}
const paymentIntent = await stripe.paymentIntents.create({
  amount: 100,
  currency: &apos;usd&apos;,
  customer: &apos;cus_123&apos;,
  capture_method: &apos;manual&apos;,
  description: &apos;Card verification&apos;,
  metadata: { fp_skip_tracking: &apos;true&apos; },
});
```

When a one-time charge has the flag, FirstPromoter ignores the charge and any refund of it. The referral is not changed and no commission is created. The flag is also respected when you import previous sales from Stripe.

**Important:** add the metadata when you create the payment. FirstPromoter reads it from Stripe as soon as the payment is made, so metadata added later is not picked up. Only flag payments that should never earn commission.
