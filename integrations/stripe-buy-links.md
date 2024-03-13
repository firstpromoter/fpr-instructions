# Adding FirstPromoter when using Stripe buy links

To get the best results for tracking when using Stripe buy links, add the script to all pages where **Stripe buy links** are available.

## Tracking script

1. Find the section on your website where you can add scripts, preferably in the head section of your website.
2. Add the code below to the head section.

***NB: If you are using your custom domain with stripe, you will need to change the link in the code from <https://buy.stripe.com/> to what is used for your domain.***

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
&lt;script&gt;
    function getFPTid() {
      return window.FPROM &amp;&amp; window.FPROM.data.tid;
    }
    function initializeFPRBuyLinks() {
      console.log(&quot;initialized fpr on buy links&quot;);
      setTimeout(function () {
        var buyStripeLinks = document.querySelectorAll(
          &apos;a[href^=&quot;https://buy.stripe.com/&quot;]&apos;
        );
        buyStripeLinks.forEach(function (link) {
          // Get current url
          var oldBuyStripeUrl = link.getAttribute(&quot;href&quot;); 
          // Get the tid
          var tid = getFPTid();
          if (tid) {
            var url = new URL(oldBuyStripeUrl);
            url.searchParams.set(&apos;client_reference_id&apos;, tid);
            link.setAttribute(&quot;href&quot;, url.toString());
          }
        });
      }, 800);
    }
    if (window.attachEvent) {
      window.attachEvent(&quot;onload&quot;, initializeFPRBuyLinks);
    } else {
      window.addEventListener(&quot;load&quot;, initializeFPRBuyLinks, false);
    }
  &lt;/script&gt;
```

@[trackingtest]("click")

@[trackingtest]("referral")
