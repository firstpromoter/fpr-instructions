![API](https://gitlab.com/api/v4/projects/55002365/repository/files/images%2Flogos%2Fapi.png/raw?ref=main)

# Integrating FirstPromoter with your website using our API

## Main tracking script

For most websites and JavaScript frameworks, you can simply insert the script on the public `index.html` file so it will be available when the website or framework loads.

1. Find your main index file (index.html, index.php).
2. Locate the `&lt;head&gt;` tag: The `&lt;head&gt;` tag is typically at the top of your  document, right after the opening `&lt;html&gt;` tag.
3. Add the below code into the head section of your website before. Preferably before the closing head tag `&lt;/head&gt;`
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

const email = '<example@example.com>'; //replace with actual email
const tid = req.cookies['_fprom_tid'];

const params = new URLSearchParams();
params.append("email", email);
params.append("tid", tid);

axios
    .post("https://firstpromoter.com/api/v1/track/signup", params, {
      headers: {
        "Content-Type": "application/x-www-form-urlencoded",
        "x-api-key": "ae686284ba57be4acf2bed3ef94516d9",
      },
    })
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
