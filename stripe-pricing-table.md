![Stripe Pricing Table](/images/stripe-pricing-table-logo.png)

# Adding FirstPromoter when using Stripe pricing table

To get the best results for tracking on when using stripe pricing tables, add the scripts to all pages where stripe pricing tables are available.

&nbsp;

## Tracking script

1. Find the section on your website where you can add scripts, preferably in the head section of your website.
2. Add the bellow code to the head section.

```html
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("click");
</script>
<script src="https://cdn.firstpromoter.com/fpr.js" async></script>
<script>
  function getFPTid() {
    return window.FPROM && window.FPROM.data.tid;
  }
  window.onload = function() {
  var stripePTable = document.getElementsByTagName('stripe-pricing-table')[0];
  stripePTable.setAttribute("client-reference-id",getFPTid())
  }
</script>
```

@[trackingtest]("click")

@[trackingtest]("referral")
