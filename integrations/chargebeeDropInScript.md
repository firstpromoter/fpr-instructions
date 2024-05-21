# Integrating FirstPromoter with Chargebee drop-in script

To get the best results for tracking, It is ideal to set this up on all the marketing or landing pages.
**Please note that this setup is only used when using the Drop-In Chargebee script (the popup not hosted page)**

This integration requires you to set the webhooks and create a hidden custom field named `tid`. Click [here to check the setup guide](/integration/chargebee?onboarding=true&integrate=true) if you don't have it set already.

## Main tracking script

For most websites, you can simply insert the script on the public `index.html` file so it will be available to all your pages.

1. Find your main index file (index.html, index.php).
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

1. Find the pages where you have set up the drop-in script from Chargebee.
2. Add the below scripts to the page.
***Make sure the Main tracking script from previous step is also on the page.***

```html
&lt;script&gt;

  function getFPTid() {
    return window.FPROM &amp;&amp; window.FPROM.data.tid;
  }

  var chargebeeTrackFunc=function(fprom) {
    var tid = getFPTid();
    if(!tid) return;
    var chargebeeInstance;
    try{
      chargebeeInstance = Chargebee.getInstance(); 
    }
    catch(err){};
    if (tid &amp;&amp; chargebeeInstance){ 
        var cart = chargebeeInstance.getCart();
        cart.setCustomer({cf_tid:tid}); 
    }else 
    if (tid){
      document.addEventListener(&quot;DOMContentLoaded&quot;,function(){chargebeeTrackFunc(fprom)});
    }
  };
  fpr(&apos;onReady&apos;,chargebeeTrackFunc)
&lt;/script&gt;
```

@[trackingtest]("referral")
