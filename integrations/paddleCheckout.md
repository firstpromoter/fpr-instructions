# Tracking using Paddle checkout

## Main tracking script

To get the best results, make sure you add the following script on the HEAD section of every public or marketing page on your website.

1. Find the page / file you want to add the scripts to.
2. Locate the `&lt;head&gt;` tag: The `&lt;head&gt;` tag is typically at the top of your  document, right after the opening `&lt;html&gt;` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag `&lt;/head&gt;`
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

If you have a sign-up page or opt in page it will be ideal to track the referral from that section when the sign up process is successful. For that flow we suggest you use our JavaScript option. This process is for the use case where you want to track referrals after payment is successful or completed.


~~~markdown [g1:Paddle Billing]
1. Find the `Paddle.Checkout.open()` function.
2. For the best results we suggest setting the `tid` value and the email on the customData object in the `Paddle.Checkout.open()` function. Below is what your code will look like.
3. The email can be removed/ignored if it is not available. We will use the customer id from paddle instead.


```html 
&lt;script&gt;
function getFPTid() {     
    return window.FPROM && window.FPROM.data.tid;   
}

Paddle.Checkout.open({
    ...
    customData: {
        &quot;fp_tid&quot;: getFPTid(),
        &quot;email&quot;:&quot;user email goes here&quot;
    }
})
&lt;/script&gt;
```

Alteratively you can use Paddles eventCallback function to send the referral details when the payment is successful. Below is what your code will look like.

```html 
&lt;script&gt;
Paddle.Initialize({
    ...
    eventCallback: function (eventData) {
        if (eventData.name === &quot;checkout.completed&quot;) {
            var email = eventData.data.customer.email;
            var uid = eventData.data.customer.id;
            fpr(&quot;referral&quot;, { email, uid })
        }
    }
})
&lt;/script&gt;
```
~~~

~~~markdown [g1:Paddle Classic]
1. Find the `Paddle.Checkout.open()` function.
2. For the best results we suggest setting the `tid` value and the email on the customData object in the `Paddle.Checkout.open()` function. Below is what your code will look like.
3. The email can be removed/ignored if it is not available. We will use the customer id from paddle instead.

```html 
&lt;script&gt;
function getFPTid() {     
    return window.FPROM && window.FPROM.data.tid;   
}

Paddle.Checkout.open({
    settings: {
        theme: &quot;light&quot;,
    },
    product:XXXXXXX,
    customData: {
        &quot;fp_tid&quot;: getFPTid(),
        &quot;email&quot;:&quot;user email goes here&quot; 
    }
});
&lt;/script&gt;
```

Alteratively you can use Paddles eventCallback function to send the referral details when the payment is successful. Below is what your code will look like.

```html
&lt;script&gt;
Paddle.Setup({ 
    ....,
    eventCallback:function(data){
     if (data.event === &quot;Checkout.Complete&quot;) {
       const email = data.eventData.user.email;
       const  uid = data.eventData.user.id;
       fpr(&quot;referral&quot;,{email,uid});
     }
    }
});
&lt;/script&gt;
```
~~~


@[trackingtest]("referral")
