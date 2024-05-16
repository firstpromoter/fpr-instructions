# Tracking using Stripe Checkout

This guide is for users using [Stripe Checkout feature](https://stripe.com/en-ro/payments/checkout). You should have a checkout page similar to [this](https://b.stripecdn.com/docs-statics-srv/assets/overview.6a4ea4b380bea93a5be8a820f3eb7c35.gif). Otherwise, select our JavaScript option.

## Main tracking script

For most websites, you can simply insert the script on the public `index.html` file so it will be available to all your pages.

1. Find your main index file (index.html, index.php).
2. Locate the `&lt;head&gt;` tag: The `&lt;head&gt;` tag is typically at the top of your document, right after the opening `&lt;html&gt;` tag.
3. Add the code below into the head section of your website, preferably before the closing head tag `&lt;/head&gt;`.
4. Save your changes and publish.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

@[trackingtest]("click")

## Referral tracking script

After setting up the main tracking script on your website, there are two cookies that are created in browser when a user visits the website using a referral link. These are `_fprom_ref` and `_fprom_tid`. The value of the `_fprom_tid` is a unique identifier created that links the current user session to an affiliate.

To track referrals from Stripe Checkout, you'll need to pass the visitor id (tid) to the Stripe checkout session in you app by setting the `fp_tid` parameter in the metadata.

**There are several ways of doing this, however, as an example we will cover 2 ways of setting this up:**

1. By passing the data from your frontend in a request.
2. By using cookies on the server side.


### Option 1: Passing the data from your frontend in a request

For this approach we will:

1. Get the `tid` value and send it as part of a request to the backend.

```js {noCopy}
import axios from axios;
...

function getFPTid() {     
    return window.FPROM && window.FPROM.data.tid;   
}
function submitForm(){
    axios.post("request to backend",{
        ...
        fp_tid: getFPTid(),
    })
}

```

2. On the backend we will retrieve `fp_tid` the tid and make our request to stripe checkout session.

```js {noCopy}
    //express js server-side.js
    ...
    const bodyParser = require("body-parser");
    app.use(bodyParser.json());

    app.post('/create-checkout-session', async (req, res) => {
    const tid = req.body.fp_tid;
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


### Option 2: Using cookies on the server side

For this approach we will:

1. Grab the `fprom_tid` cookie on the server side.
2. Set the `fp_tid` in the metadata on the backend code for Stripe.

*Doing this may vary depending on your setup.* Below is an example for Node.js:

```js {noCopy}
//express js server-side.js
 
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


@[trackingtest]("referral")
