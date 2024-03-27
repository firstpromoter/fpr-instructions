# Integrating FirstPromoter with Recurly Hosted pages

To get the best results for tracking, It is ideal to set this up on all the marketing or landing pages.
**Please note that this setup is only used when using Recurly hosted pages**

## Tracking script

1. Ensure you're passing the `account_code` to the thank-you page after checkout is completed, also referred to as Return or Success URL.
2. Navigate to Configuration > Plans. Click on a plan, then select "Edit" (from top-right "Plan Actions" button).
3. Set a "Return URL After Success" pointing to the thank-you page on your domain.
4. If the link does not include the `{{account_code}}` parameter, add it. The final URL will resemble this: `"https://yourdomain.com/thank-you?account={{account_code}}"`.
5. Repeat this process for all plans you want FirstPromoter to track.
6. Once the previous steps are completed, add the following script to either the thank-you page or the page where Recurly redirects after a successful checkout.

```js
&lt;script&gt;
var url = new URL(window.location.href);
var account = url.searchParams.get(&quot;account&quot;);
fpr(&quot;referral&quot;,{email:&quot;&quot;, uid: account})
&lt;/script&gt;

&lt;script&gt;
var url = new URL(window.location.href);
var account = url.searchParams.get(&quot;account&quot;);
fpr(&quot;referral&quot;,{email:&quot;&quot;, uid: account})
&lt;/script&gt;

```

@[trackingtest]("click")

@[trackingtest]("referral")
