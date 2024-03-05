![Stripe Pricing Table](/images/logos/stripe_logo.png)

# Adding FirstPromoter when using Stripe pricing table

To get the best results for tracking on when using stripe pricing tables, add the scripts to all pages where stripe pricing tables are available.

## Tracking script

1. Find the section on your website where you can add scripts, preferably in the head section of your website.
2. Add the bellow code to the head section.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
&lt;script&gt;
&nbsp; function getFPTid() {
&nbsp; &nbsp; return window.FPROM &amp;&amp; window.FPROM.data.tid;
&nbsp; }
  window.onload = function() {
  var stripePTable = document.getElementsByTagName(&apos;stripe-pricing-table&apos;)[0];
  stripePTable.setAttribute(&quot;client-reference-id&quot;,getFPTid())
  }
&lt;/script&gt;
```

@[trackingtest]("click")

@[trackingtest]("referral")
