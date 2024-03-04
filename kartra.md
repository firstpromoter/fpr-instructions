![Kartra](/images/kartra-logo.png)

# Adding FirstPromoter to your Kartra website

To get the best results, make sure you add the following script globally on the HEAD section of every public or marketing page on your website.

&nbsp;

## Main tracking script

1. On your Kartra dashboard, go to all funnels page
2. Click on your funnel
3. Go to settings on the top right of your funnel page
4. Add the following script inside the HEAD TRACKING CODE container

```html
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("click");
</script>
<script src="https://cdn.firstpromoter.com/fpr.js" async></script>
```

@[trackingtest]("click")

## Referral tracking script

1. Go to "All Funnels" page.
2. Click on your preferred funnel.
3. Click "Edit Page" for the page you want to add the scripts to.
4. Click on Settings on the top navigation and select Tracking code.
5. Add the below scripts and save.

```html
<script>
  function set_fprom(){
    console.log('loaded');
    jQuery(document).on('mousedown touchstart','.one_click_one_price_checkout,.js_next_step_button,.kartra_optin_submit_btn,.js_kartra_language_submit_payment', function(){
      fpr("referral",{email: jQuery('input[name="email"]').val(), uid:""})
    });
  }

  if (window.attachEvent){
    window.attachEvent('onload', set_fprom);
  } else{
    window.addEventListener('load', set_fprom, false);
  }
</script>
```

@[trackingtest]("referral")
