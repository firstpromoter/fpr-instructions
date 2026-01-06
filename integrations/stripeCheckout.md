# Tracking using Stripe Checkout

This guide is for users using [Stripe Checkout feature](https://stripe.com/en-ro/payments/checkout). You should have a checkout page similar to [this](https://b.stripecdn.com/docs-statics-srv/assets/overview.6a4ea4b380bea93a5be8a820f3eb7c35.gif). Otherwise, select our JavaScript option.

## Main tracking script

For most websites, you can simply insert the script on the public `index.html` file so it will be available to all your pages.

1. Find your main index file (index.html, index.php).
2. Locate the `&lt;head&gt;` tag: The `&lt;head&gt;` tag is typically at the top of your document, right after the opening `&lt;html&gt;` tag.
3. Add the code below into the head section of your website, preferably before the closing head tag `&lt;/head&gt;`.
4. Save your changes and publish.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q =
w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

@[trackingtest]("click")

## Referral tracking script

After setting up the main tracking script on your website, there are two cookies that are created in browser when a user visits the website using a referral link. These are `_fprom_ref` and `_fprom_tid`. The value of the `_fprom_tid` is a unique identifier created that links the current user session to an affiliate.

To track referrals from Stripe Checkout, you'll need to pass the visitor id (tid) to the Stripe checkout session in you app by setting the `fp_tid` parameter in the metadata.

**There are several ways of doing this, however, as an example we will cover 2 ways of setting this up:**

**_Please note that these are just examples, pasting it directly will not work. You will need to edit your code to get it working following these examples._**

1. By passing the tid from the frontend in a request.
2. By using cookies on the server side.

~~~~markdown [g1:Passing the tid from the frontend]

For this approach we will:

1. Get the `tid` value and send it as part of a request to the backend.

```js {noCopy}
import axios from axios;
...

function getFPTid() {
    return window.FPROM &amp;&amp; window.FPROM.data.tid;
}
function submitForm(){
    axios.post(&quot;request to backend&quot;,{
        ...
        fp_tid: getFPTid(),
    })
}

```

2. On the backend we will retrieve `fp_tid` the tid and make our request to stripe checkout session.

```js {noCopy}
    //express js server-side.js
    ...
    const bodyParser = require(&quot;body-parser&quot;);
    app.use(bodyParser.json());

    app.post(&apos;/create-checkout-session&apos;, async (req, res) =&gt; {
    const tid = req.body.fp_tid;
    const session = await stripe.checkout.sessions.create({
        ...
        success_url: &apos;https://example.com/success&apos;,
        cancel_url: &apos;https://example.com/cancel&apos;,
        metadata: {
            fp_tid: tid
        }
    })
    res.json({ id: session.id });
    });
```

Alternatively if you are not checking out instantly but creating the customer in stripe. You can pass the tid as part of the customer metadata

```js {noCopy}
    //express js server-side.js
    ...
    const bodyParser = require(&quot;body-parser&quot;);
    app.use(bodyParser.json());

    app.post(&apos;/create-checkout-session&apos;, async (req, res) =&gt; {
        const tid = req.body.fp_tid;
        const customer = await stripe.customers.create({
            email: &apos;customer@example.com&apos;,
            metadata: {
                fp_tid: tid,
            }
        });
    });
```

~~~~

~~~~markdown [g1:Using cookies]

For this approach we will:

1. Grab the `fprom_tid` cookie on the server side.
2. Set the `fp_tid` in the metadata on the backend code for Stripe.

_Doing this may vary depending on your setup._ Below is an example for Node.js:

```js {noCopy}
//express js server-side.js

const cookieParser = require(&apos;cookie-parser&apos;);
app.use(cookieParser());
app.post(&apos;/create-checkout-session&apos;, async (req, res) =&gt; {
   const tid = req.cookies[&apos;_fprom_tid&apos;];
   const session = await stripe.checkout.sessions.create({
      ...
      success_url: &apos;https://example.com/success&apos;,
      cancel_url: &apos;https://example.com/cancel&apos;,
      metadata: {
        fp_tid: tid
      }
   })
   res.json({ id: session.id });
});

```

Alternatively if creating the customer in stripe and not checking out instantly but. You can pass the tid as part of the customer metadata

```js {noCopy}
    //express js server-side.js
    ...
    const cookieParser = require(&apos;cookie-parser&apos;);
    app.use(cookieParser());
    app.post(&apos;/create-checkout-session&apos;, async (req, res) =&gt; {
    const tid = req.cookies[&apos;_fprom_tid&apos;];
    const customer = await stripe.customers.create({
            email: &apos;customer@example.com&apos;,
            metadata: {
                fp_tid: tid
            }
    });
    res.json({ id: session.id });
});
```
~~~~


@[trackingtest]("referral")
