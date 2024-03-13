# Adding FirstPromoter to ThriveCart

To get the best results for tracking on ThriveCart, it is ideal to set this up on all the marketing pages, even if you use ThriveCart only for checkout.

## Main tracking script

1. On your ThriveCart dashboard, go to product settings.
2. Select the checkout tab.
3. Select the tracking tab.
4. In the first field "All pages: Paste tracking code to add to all of this product's pages", add the code below and save.

***If you use landing/marketing pages outside ThriveCart, you will need to add the script to all the pages on your website.***

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

@[trackingtest]("click")

## Referral tracking script

1. Go to Settings.
2. Select the Checkout tab.
3. Enable the “Do you want to add tracking code to your checkout pages” option if it is not enabled already.
4. Add the script below in the second field: "Checkout pages: Paste tracking code to add only to your checkout page"

```html
&lt;script&gt; 
function set_fprom(){
    $(document).on(&apos;mousedown touchstart&apos;,&apos;div[data-widget-id=&quot;internal-core_fields_buy_button&quot;]&apos;, function(){
      fpr(&quot;referral&quot;,{email: $(&apos;input[name=&quot;customer.email&quot;]&apos;).val(), uid:&quot;&quot;})
    });
 }
if (window.attachEvent){
  window.attachEvent(&apos;onload&apos;, set_fprom);
}else{
  window.addEventListener(&apos;load&apos;, set_fprom, false);
}
&lt;/script&gt;
```

5. Add the script below into the 3rd field: "Main product: Paste tracking code to add if the customer purchases the main product".

```html
&lt;script&gt;
 fpr(&quot;referral&quot;,{email: _thrive_order.customer.email})
&lt;/script&gt; 
```

@[trackingtest]("referral")
