![SamCart](/images/logos/samcart.png)

# Adding FirstPromoter to Samcart

To get the best results for tracking on SamCart it is ideal to set this up on all the marketing pages even if you use SamCart only for checkout.

## Main tracking script

1. On your SamCart dashboard, go to the advanced settings tab of your product.
2. Add the below script to the first "Embed HTML / Scripts in Header"
3. Save your changes.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

@[trackingtest]("click")

## Referral tracking script

1. Go back to the advanced settings tab of your product.
2. Find the “Fire pixel/script after order is completed” section.
3. Add the below scripts and save.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
&lt;script&gt;fpr(&quot;referral&quot;,{email:&quot;##email##&quot;})&lt;/script&gt;
```

@[trackingtest]("referral")