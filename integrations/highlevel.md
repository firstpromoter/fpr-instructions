# Adding FirstPromoter to your HighLevel website

Integrating FirstPromoter with your HighLevel setup is a breeze. It requires one predefined set of scripts which should be added to the head section of your website or funnels.

## Tracking script

### Adding the scripts to your HighLevel website

1. Go to the Dashboard.
2. Click on "Sites" in the left sidebar.
3. Select the "Websites" tab if you want to add to the full website, or the "Funnels" tab to add to a specific funnel.

![highlevel menu](https://gitlab.com/api/v4/projects/55002365/repository/files/images%2Fscreenshots%2Fhighlevel-menu.png/raw?ref=main "")
  
4. Click on the three-dot menu icon on your preferred website or funnel and select "Edit."
5. In the top panel, select the "Settings" tab and find the "Head Tracking Code" section.
6. Copy and paste the code below into the "Head Tracking Code" section.
7. If you use stripe payment links where you have links like `https://buy.stripe.com/` on your website, select the `With Stripe payment links` tab.

```html [g1:Default]
&lt;script src=&quot;https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.0/jquery.min.js&quot; integrity=&quot;sha256-1IKHGl6UjLSIT6CXLqmKgavKBXtr0/jJlaGMEkh+dhw=&quot; crossorigin=&quot;anonymous&quot;&gt;&lt;/script&gt;
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.highlevel.js&quot; async&gt;&lt;/script&gt;
```

```html [g1:With Stripe payment links]
&lt;script src=&quot;https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.0/jquery.min.js&quot; integrity=&quot;sha256-1IKHGl6UjLSIT6CXLqmKgavKBXtr0/jJlaGMEkh+dhw=&quot; crossorigin=&quot;anonymous&quot;&gt;&lt;/script&gt;
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.highlevel.js&quot; async&gt;&lt;/script&gt;
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
        var oldBuyStripeUrl = link.getAttribute(&quot;href&quot;);
        var tid = getFPTid();
        if (tid) {
          var url = new URL(oldBuyStripeUrl);
          url.searchParams.set(&apos;client_reference_id&apos;, tid);
          link.setAttribute(&quot;href&quot;, url.toString());
        }
      });
    }, 1000);
  }
  var stateCheck = setInterval(() =&gt; {
    if (document.readyState === &quot;complete&quot;) {
      clearInterval(stateCheck);
      initializeFPRBuyLinks();
    }
  }, 100);
&lt;/script&gt;

```

### Test Click Tracking

@[trackingtest]("click")

### Test Referral Tracking

@[trackingtest]("referral")
