![Stripe Buy Links](/images/stripe-buy-links-logo.png)

# Adding FirstPromoter when using Stripe buy links

To get the best results for tracking on when using stripe buy links, add the scripts to all pages where **stripe buy links** are available.

&nbsp;

## Tracking script

1. Find the section on your website where you can add scripts,  preferably in the head section of your website.
2. Add the bellow code to the head section.

***NB: If you are using your custom domain with stripe, you will need to change the link in the code from https://buy.stripe.com/ to what is used for your domain.***

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
    function initializeFPRBuyLinks() {
      console.log("initialized fpr on buy links");
      setTimeout(function () {
        var buyStripeLinks = document.querySelectorAll(
          'a[href^="https://buy.stripe.com/"]'
        );
        buyStripeLinks.forEach(function (link) {
          // Get current url
          var oldBuyStripeUrl = link.getAttribute("href"); 
          // Get the tid
          var tid = getFPTid();
          if (tid) {
            var url = new URL(oldBuyStripeUrl);
            url.searchParams.set('client_reference_id', tid);
            link.setAttribute("href", url.toString());
          }
        });
      }, 800);
    }
    if (window.attachEvent) {
      window.attachEvent("onload", initializeFPRBuyLinks);
    } else {
      window.addEventListener("load", initializeFPRBuyLinks, false);
    }
  </script>
```

@[trackingtest]("click")

@[trackingtest]("referral")
