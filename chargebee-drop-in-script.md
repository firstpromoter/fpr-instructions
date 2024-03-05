![ChargeBeeDropInScript](/images/chargebee-drop-in-script-logo.png)

# Integrating FirstPromoter with Chargebee drop in script

To get the best results for tracking, It is ideal to set this up on all the marketing or landing pages.
**Please note that this setup is only used when using the Drop-In Chargebee script (the popup not hosted page)**

&nbsp;

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

1. Find the pages where you have set up the drop-in script from Chargebee.
2. Add the below scripts to the page.
***Make sure the Main tracking script from previous step is also on the page.***

```html
<script>
  var chargebeeTrackFunc=function(fprom) {
    var tid = fprom.tid;
    var chargebeeInstance;
    try{
      chargebeeInstance = Chargebee.getInstance(); 
    }
    catch(err){};
    if (tid && chargebeeInstance){ 
        var cart = chargebeeInstance.getCart();
        cart.setCustomer({cf_tid:tid}); 
    }else 
    if (tid){
      document.addEventListener("DOMContentLoaded",function(){chargebeeTrackFunc(fprom)});
    }
  };
  fpr('onReady',chargebeeTrackFunc)
</script>
```

@[trackingtest]("referral")
