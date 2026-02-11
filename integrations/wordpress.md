# Adding FirstPromoter to your WordPress website

FirstPromoter has a dedicated WordPress plugin that makes it easy to add affiliate tracking to your website. The plugin handles click tracking, referral tracking, and sales tracking with built-in support for WooCommerce, MemberPress, Contact Form 7, OptimizePress, and custom forms.

&nbsp;

## Installing the plugin

1. Log in to your WordPress admin dashboard.
2. Go to **Plugins > Add New**.
3. Search for **"FirstPromoter"** in the search bar.
4. Click **Install Now** and then **Activate**.

Alternatively, you can download the plugin directly from the [WordPress Plugin Directory](https://wordpress.org/plugins/firstpromoter/) and upload it manually via **Plugins > Add New > Upload Plugin**.

&nbsp;

## Base Configuration

Once the plugin is activated, go to **FirstPromoter** in the WordPress admin sidebar to configure it.

### 1. Add your Account ID

Your Account ID (also referred to as your workspace ID) is required for the tracking script to work.

- Go to your FirstPromoter dashboard.
- Navigate to **Settings > Integrations**.
- Copy your **Account ID** and paste it into the **Account ID** field in the plugin settings.

### 2. Add your API Key

The API key is required for most sale tracking features (WooCommerce sales, MemberPress sales, Contact Form 7).

- In your FirstPromoter dashboard, go to **Settings > Integrations > Manage API keys**.
- Copy your **API Key** and paste it into the **API Key** field in the plugin settings.

### 3. Cross-domain tracking (optional)

If you have multiple domains that need to share tracking data, enter them as a comma-separated list in the **Cross-domain tracking** field. For example: `example.com, shop.example.com`

&nbsp;

## WooCommerce Integration

The plugin can automatically track WooCommerce account registrations, checkouts, refunds, and cancellations.

### Signup Tracking

Enable **WooCommerce Signup Tracking** to capture emails when customers register an account or complete a checkout. This does not require an API key.

### Sale Tracking

Enable **WooCommerce Sale Tracking** to automatically send order data (amount, order ID, coupon codes) to FirstPromoter when an order is marked as processing or completed. **This requires an API key.**

The plugin also handles:
- **Refunds** — automatically generates negative commissions when an order is refunded.
- **Cancellations** — tracks when an order is cancelled.

&nbsp;

## MemberPress Integration

Track new member signups and transactions from MemberPress.

### Signup Tracking

Enable **MemberPress Signup Tracking** to capture new member registrations. This works without an API key.

### Sale Tracking

Enable **MemberPress Sale Tracking** to send transaction data to FirstPromoter. **This requires an API key.**

The plugin also supports tracking recurring subscription payments.

***NB: If you are already using FirstPromoter's Stripe integration to track payments, disable MemberPress sale tracking to avoid duplicate sales.***

&nbsp;

## Contact Form 7 Integration

Enable **Contact Form 7 Tracking** to automatically capture form submissions and send them to FirstPromoter. The plugin will auto-detect email fields in your forms.

**This requires an API key.**

&nbsp;

## OptimizePress Integration

Enable **OptimizePress Tracking** to capture form submissions from OptimizePress pages. This works without an API key.

&nbsp;

## Custom Form Tracking

If you use forms that aren't covered by the built-in integrations, you can track them using CSS selectors.

1. Enable **Custom Form Tracking** in the plugin settings.
2. For each form you want to track, provide:
   - A **CSS selector for the form** (e.g., `#my-signup-form` or `.contact-form`)
   - A **CSS selector for the email input field** (e.g., `input[name="email"]` or `#email-field`)
3. You can add multiple form selector pairs using the repeater in the settings page.

The plugin uses a MutationObserver to detect dynamically loaded forms, so this works with forms that are loaded after the initial page load. It also includes a server-side AJAX fallback for cases where ad-blockers may interfere with client-side tracking.

&nbsp;

## Features that require an API Key

| Feature | API Key Required |
|---|---|
| WooCommerce Signup Tracking | No |
| WooCommerce Sale Tracking | Yes |
| MemberPress Signup Tracking | No |
| MemberPress Sale Tracking | Yes |
| Contact Form 7 | Yes |
| OptimizePress | No |
| Custom Form Tracking | No |

&nbsp;

### Test Click Tracking

@[trackingtest]("click")

### Test Referral Tracking

@[trackingtest]("referral")
