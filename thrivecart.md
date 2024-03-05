![ThriveCart](/images/thrivecart-logo.png)

# Adding FirstPromoter to ThriveCart

To get the best results for tracking on ThriveCart it is ideal to set this up on all the marketing pages even if you use ThriveCart only for checkout

&nbsp;

## Main tracking script

1. On your ThriveCart dashboard, go to product settings.
2. Select checkout tab.
3. Select tracking tab.
4. On the first field: "All pages: Paste tracking code to add to all of this product's pages" add the code below and save.

***If you use landing/marketing pages outside ThriveCart you will need to add the script to all the pages on your website.***

```html
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("click");
</script>
<script src="https://cdn.firstpromoter.com/fpr.js" async></script>
```

@[trackingtest]("click")

## Referral tracking script

1. Go to Settings.
2. Select  Checkout tab.
3. Enable the “Do you want to add tracking code to your checkout pages” option if it is not enabled already.
4. Add the script below in the second field: **“Checkout pages: Paste tracking code to add only to your checkout page”**

```html
<script> 
function set_fprom(){
    $(document).on('mousedown touchstart','div[data-widget-id="internal-core_fields_buy_button"]', function(){
      fpr("referral",{email: $('input[name="customer.email"]').val(), uid:""})
    });
 }
if (window.attachEvent){
  window.attachEvent('onload', set_fprom);
}else{
  window.addEventListener('load', set_fprom, false);
}
</script>
```

5. Add the script below into the 3rd field **"Main product: Paste tracking code to add if the customer purchases the main product".**

```html
<script>
 fpr("referral",{email: _thrive_order.customer.email})
</script> 
```

@[trackingtest]("referral")
