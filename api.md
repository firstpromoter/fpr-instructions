![API](/images/api-logo.png)

# Integrating FirstPromoter with your website using our API

&nbsp;

## Main tracking script

For most websites and JavaScript frameworks, you can simply insert the script on the public `index.html` file so it will be available when the website or framework loads.

1. Find your main index file (index.html, index.php).
2. Locate the `<head>` tag: The `<head>` tag is typically at the top of your  document, right after the opening `<html>` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag `</head>`
4. Save your changes and publish.

```html
&lt;script&gt;(function(w){w.fpr=w.fpr||function(){w.fpr.q = w.fpr.q||[];w.fpr.q[arguments[0]==&apos;set&apos;?&apos;unshift&apos;:&apos;push&apos;](arguments);};})(window);
fpr(&quot;init&quot;, {cid:&quot;==cid=here==&quot;}); 
fpr(&quot;click&quot;);
&lt;/script&gt;
&lt;script src=&quot;https://cdn.firstpromoter.com/fpr.js&quot; async&gt;&lt;/script&gt;
```

@[trackingtest]("click")

## Referral tracking script

To track referrals using the API you'll need to have access to the browser cookies. With the main tracking script in place there are 2 cookies we set when you visit the referral link. _fprom_tid and _fprom_ref booth cookies can bee used in making your API request however to prevent multiple tracking always use the _fprom_tid which has a check to see if a browser session has already been tracked.

1. Get your API key from your Settings > Integrations tab.
2. On your backend, retrieve the _fprom_tid cookie.

```js {noCopy}
//backend.js
const cookieParser = require('cookie-parser'); 
...
app.use(cookieParser());
const tid = req.cookies['_fprom_tid'];
```

3. With the cookie retrieved, make a POST request to the API endpoint `https://firstpromoter.com/api/v1/track/signup`  together with the following parameters.

```txt
Parameter     Required                  Description

email         yes if uid is null        email of the lead/sign-up
uid           yes if email is null      user id of the user in your database
tid           yes if ref_id is null     visitor tracking id.
ref_id        yes if tid is null        default referral id of the promoter.
ip            no                        IP of the visitor

```

**Note:** the request content type for our API is not JSON, it's `application/x-www-form-urlencoded`

4. The full code will look like this.

```Javascript {noCopy}

//backend.js
const axios = require('axios');
...
//this code can go into your sign up flow
// to make this cleaner you can extract it into a function

let email = '<example@example.com>'; //replace with actual email
let tid = req.cookies['_fprom_tid'];

let data = `email=${email}&tid=${tid}`;

let config = {
    method: 'post',
    url: '<https://firstpromoter.com/api/v1/track/signup>',
    headers: {
        'Content-Type': 'application/x-www-form-urlencoded',
        'x-api-key': 'YOUR API KEY HERE',
    },
    data : data
};

axios(config)
    .then(function (response) {
    //any action if the request is successful
    console.log(JSON.stringify(response.data));
    })
    .catch(function (error) {
    //any action if the request fails
    console.log(error);
});
```

@[trackingtest]("referral")