![Stripe Checkout](/images/stripe-checkout-logo.png)

# Tracking using Stripe Checkout

This guide is for users using [Stripe Checkout feature](https://stripe.com/en-ro/payments/checkout), you should have a checkout page similar to [this](https://b.stripecdn.com/docs-statics-srv/assets/overview.6a4ea4b380bea93a5be8a820f3eb7c35.gif). Otherwise, select our JavaScript option.

## Main tracking script

For most websites, you can simply insert the script on the public `index.html` file so it will be available to all your pages.

1. Find your main index file (index.html, index.php).
2. Locate the `<head>` tag: The `<head>` tag is typically at the top of your  document, right after the opening `<html>` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag `</head>`
4. Save your changes and publish.

```html
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("click");
</script>
<script src="https://cdn.firstpromoter.com/fpr.js" async></script>
```

@[trackingtest]("click")

## Referral tracking script

After setting up the main tracking script on your website we set two cookies `_fprom_ref` and `_fprom_tid`. The value of the `_fprom_tid` is a unique identifier created that links the current user session to an affiliate.

To track referrals from Stripe Checkout you'll need to pass the visitor id (tid) to Stripe checkout session using fp_tid parameter set in the metadata in the stripe checkout session.

For this setup we have two main ways of getting the integration to work

1. By using cookies on the server side.
2. By using a hidden field to pass the data from the frontend.

### Option 1 Using cookies directly

1. Grab the `_fprom_tid` cookie on the server side.
2. In your backend code for stripe set the fp_tid in the metadata.

Doing this may vary depending on your setup below is an example for node js

```Javascript
//server-side.js
 
const cookieParser = require('cookie-parser'); 
app.use(cookieParser());
app.post('/create-checkout-session', async (req, res) => {
   const tid = req.cookies['_fprom_tid'];

   const session = await stripe.checkout.sessions.create({   
      ...
      success_url: 'https://example.com/success',
      cancel_url: 'https://example.com/cancel',
      metadata: {
        fp_tid: tid
      }
   })

   res.json({ id: session.id });
});
```

### Option 2 Using a hidden input on your form on the frontend

1. On your Stripe checkout form  add this hidden input field `<input type="hidden" id="fp_tid" name="fp_tid">`.

2. Your form should now look like this

   ```html {noCopy}
         <form action="/charge" method="post" id="payment-form">
        ...
        <input type="hidden" id="fp_tid" name="fp_tid">
        <button class="btn-Stripe">Submit Payment</button>
      </form>
    ```

3. Add the below script to your head section of your website.

   ```html
   <script>
    window.onload = function () {
        var tid = window.FPROM && window.FPROM.data.tid;
        if (tid) {
            //get the element by the id and set the value
            document.getElementById('fp_tid').value = tid;
        }
    }
    </script>
   ```

4. Get the fp_tid on the backend.

   ```Javascript
        //server-side.js
        ...
        const bodyParser = require("body-parser");
        app.use(bodyParser.json());

        app.post('/create-checkout-session', async (req, res) => {
        const tid = req.body.fp_tid;

        const session = await stripe.checkout.sessions.create({
            ...
            success_url: '<https://example.com/success>',
            cancel_url: '<https://example.com/cancel>',
            metadata: {
                fp_tid: tid
            }
        })

        res.json({ id: session.id });
        });
   ```

@[trackingtest]("referral")
