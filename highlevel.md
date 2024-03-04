![HighLevel](/images/high-level-logo.png)

# Adding FirstPromoter to your Highlevel website

Integrating FirstPromoter with your HighLevel setup is a breeze. It requires one set of predefined scripts which should be added to the head section of your website or funnels.

&nbsp;

## Tracking script

### Adding the scripts to your HighLevel website

1. Go to the Dashboard
2. Click on Sites on the left sidebar
3. Select the websites Tab if you want to add to the full website, or the funnels tab to add to a specific funnel.

    ![image.png](images/screenshots/highlevel-menu.png "")
  
4. Click on the 3 dot menu icon on your preferred website or funnel and select Edit
5. On the Panel, select the settings tab and find the head tracking code section.
6. Copy and paste the below code into the head tracking code section

```html [g1:Default]
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.0/jquery.min.js" integrity="sha256-1IKHGl6UjLSIT6CXLqmKgavKBXtr0/jJlaGMEkh+dhw=" crossorigin="anonymous"></script>
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("click");
</script>
<script src="https://cdn.firstpromoter.com/fpr.highlevel.js" async></script>
```

```html [g1:With Stripe Buy Links]
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.0/jquery.min.js" integrity="sha256-1IKHGl6UjLSIT6CXLqmKgavKBXtr0/jJlaGMEkh+dhw=" crossorigin="anonymous"></script>
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("click");
</script>
<script src="https://cdn.firstpromoter.com/fpr.highlevel.js" async></script>
<script>
function getFPTid(){return window.FPROM && window.FPROM.data.tid}function initializeFPRBuyLinks(){setTimeout(function(){document.querySelectorAll('a[href^="https://buy.stripe.com/"]').forEach(function(t){var e=t.getAttribute("href"),i=getFPTid();i&&((e=new URL(e)).searchParams.set("client_reference_id",i),t.setAttribute("href",e.toString()))})},800)}var stateCheck=setInterval(()=>{"complete"===document.readyState&&(clearInterval(stateCheck),initializeFPRBuyLinks())},100);
</script>
```

### Test Click Tracking

@[trackingtest]("click")

### Test Referral Tracking

@[trackingtest]("referral")
