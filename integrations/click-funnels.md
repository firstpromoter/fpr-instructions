![Click Funnels](/images/logos/clickfunnels.png)

# Adding FirstPromoter to your Click Funnels website

Setting up FirstPromoter with Click Funnels mainly requires you to add a predesigned script to get started

&nbsp;

## Tracking script

### Adding the scripts to your Click Funnels website

1. Go to your Click Funnels Dashboard.
2. Select sites > Overview > Customize > Select Settings in the top bar > show code.

![click funnels menu screenshot](/images/screenshots/click-funnels-settings.png "")

**For specific funnels pages**

Select Sites > Pages > Funnel Pages > click on the page you want to add the scripts to >Select Settings in the top bar > show code

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
