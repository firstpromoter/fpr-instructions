![Paddle Checkout](/images/paddle-checkout-logo.png)

# Tracking using Paddle checkout


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

If you have a sign-up page or opt in page it will be ideal to track the referral from that section when the sign up process is successful. For that flow we suggest you use our JavaScript option. This process is for the use case where you want to track referrals after payment is successful or completed.

1. Find your Paddle.Setup() Function.
2. We will need to take advantage of Paddles event Callback function. You can have a function there that sends the payment details when the payment is successful. Below is what a sample request will look like.

```html
<script>
Paddle.Setup({ 
    ....,
    eventCallback:function(data){
     if (data.event === "Checkout.Complete") {
       const email = eventData.data.customer.email;
       const  uid = eventData.data.customer.id;
       fpr("referral",{email,uid});
     }
    }
});
</script>
```

@[trackingtest]("referral")
