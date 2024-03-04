![Kickpages](/images/kick-pages-logo.png)

# Adding FirstPromoter to Kickpages

To get the best results, make sure you add the following script globally on the HEAD section of every public or marketing page on your website.

&nbsp;

## Main tracking script

1. On your Kickpages dashboard, go to the  projects page
2. Hover on the settings icon under the profile picture
3. Select Includes  
4. Add the below scripts to the first field and save

```html
<script>(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]=='set'?'unshift':'push'](arguments);};})(window);
fpr("init", {cid:"==cid=here=="}); 
fpr("click");
</script>
<script src="https://cdn.firstpromoter.com/fpr.js" async></script>
```

@[trackingtest]("click")

## Referral tracking script

1. Go back to the Projects page.
2. Click on your project.
3. Click Edit Page and select Settings on top right.
4. Click on Custom Includes.
5. Add the script in Code for Head Tag.

```html
<script src="https://cdnjs.cloudflare.com/ajax/libs/jquery/2.0.0/jquery.min.js" integrity="sha256-1IKHGl6UjLSIT6CXLqmKgavKBXtr0/jJlaGMEkh+dhw=" crossorigin="anonymous">
</script>
<script>
  function set_fprom(){
    console.log('loaded');
    $(document).on('click',' a[name="btnSubmit"]', function(){
      fpr("referral",{email: $('input[name="orderFormEmail"]').val(), uid:""})
    });
  }
  if (window.attachEvent){
    window.attachEvent('onload', set_fprom);
  }else{
    window.addEventListener('load', set_fprom, false);
  }
</script>
```

@[trackingtest]("referral")