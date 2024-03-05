![Thinkific](/images/thinkific-logo.png)

# Adding FirstPromoter to ThriveCart

To get the best results for tracking on Thinkific it is ideal to set this up on all the marketing pages.

&nbsp;

## Main tracking script

1. Go to "Settings".
2. Select Code & Analytics.
3. Add the script below in "Site footer code" section.

```html
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("click");
</script>
<script src="https://cdn.firstpromoter.com/fpr.js" async></script>
```

@[trackingtest]("click")

## Referral tracking script

Thinkific provides two ways with which you can set things up.

### Tracking Referrals from orders

If you want to track orders kindly follow the below steps.

1. Go to Settings.
2. Select Code & analytics.
3. Find the  Order tracking code section.
4. Add the below scripts.

```html
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("referral",{email:"{{billing_email}}"});
</script>
<script src="https://cdn.firstpromoter.com/fpr.js" async></script>
```

### Tracking Referrals on Signup

If you want to track sign-ups kindly follow the below steps.

1. Go to Settings.
2. Select Code & analytics.
3. Find the Signup tracking code section.
4. Add the below scripts.

```html
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("referral",{email:"{{email}}"});
</script>
<script src="https://cdn.firstpromoter.com/fpr.js" async></script>
```

@[trackingtest]("referral")
