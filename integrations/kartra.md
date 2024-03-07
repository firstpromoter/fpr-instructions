![Kartra](https://gitlab.com/api/v4/projects/55002365/repository/files/images%2Flogos%2Fkartra.png/raw?ref=main)

# Adding FirstPromoter to your Kartra website

To get the best results, make sure you add the following script globally on the HEAD section of every public or marketing page on your website.

## Main tracking script

1. On your Kartra dashboard, go to all funnels page
2. Click on your funnel
3. Go to settings on the top right of your funnel page
4. Add the following script inside the HEAD TRACKING CODE container

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

@[trackingtest]("click")

## Referral tracking script

1. Go to "All Funnels" page.
2. Click on your preferred funnel.
3. Click "Edit Page" for the page you want to add the scripts to.
4. Click on Settings on the top navigation and select Tracking code.
5. Add the below scripts and save.

```html
&lt;script&gt;
  function set_fprom(){
    console.log(&apos;loaded&apos;);
    jQuery(document).on(&apos;mousedown touchstart&apos;,&apos;.one_click_one_price_checkout,.js_next_step_button,.kartra_optin_submit_btn,.js_kartra_language_submit_payment&apos;, function(){
      fpr(&quot;referral&quot;,{email: jQuery(&apos;input[name=&quot;email&quot;]&apos;).val(), uid:&quot;&quot;})
    });
  }

  if (window.attachEvent){
    window.attachEvent(&apos;onload&apos;, set_fprom);
  } else{
    window.addEventListener(&apos;load&apos;, set_fprom, false);
  }
&lt;/script&gt;
```

@[trackingtest]("referral")
