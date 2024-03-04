![SamCart](/images/samcart-logo.png)

# Adding FirstPromoter to Samcart

To get the best results for tracking on SamCart it is ideal to set this up on all the marketing pages even if you use SamCart only for checkout.

&nbsp;

## Main tracking script

1. On your SamCart dashboard, go to the advanced settings tab of your product.
2. Add the below script to the first "Embed HTML / Scripts in Header"
3. Save your changes.

```html
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("click");
</script>
<script src="https://cdn.firstpromoter.com/fpr.js" async></script>
```

@[trackingtest]("click")

## Referral tracking script

1. Go back to the advanced settings tab of your product.
2. Find the “Fire pixel/script after order is completed” section.
3. Add the below scripts and save.

```html
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("click");
</script>
<script src="https://cdn.firstpromoter.com/fpr.js" async></script>
<script>fpr("referral",{email:"##email##"})</script>
```

@[trackingtest]("referral")