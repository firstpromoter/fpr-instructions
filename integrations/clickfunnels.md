# Adding FirstPromoter to your ClickFunnels website

Setting up FirstPromoter with ClickFunnels mainly requires you to add a predesigned script to get started

## Tracking script

### Adding the scripts to your ClickFunnels website

1. Go to your ClickFunnels Dashboard.
2. Select sites > Overview > Customize > Select Settings in the top bar > show code.

![clickfunnels menu screenshot](https://gitlab.com/api/v4/projects/55002365/repository/files/images%2Fscreenshots%2Fclickfunnels-settings.png/raw?ref=main "")

**For specific funnels pages**

Select Sites > Pages > Funnel Pages > click on the page you want to add the scripts to > Select Settings in the top bar > show code

1. Copy and paste the below code into the head tracking code section

```html
&lt;script&gt;(function (w) {
      w.fpr = w.fpr || function () {
         w.fpr.q = w.fpr.q || [];
         w.fpr.q[arguments[0] == 'set' ? 'unshift' : 'push'](arguments);
      };
   })(window);
   fpr(&quot;init&quot;, {cid: &quot;==cid=here==&quot;});
   fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.clickfunnels.js&quot; async&gt;&lt;/script&gt;
```

### Test Click Tracking

@[trackingtest]("click")

### Test Referral Tracking

@[trackingtest]("referral")
