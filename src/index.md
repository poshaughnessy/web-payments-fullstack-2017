title: Web Payments
output: public/index.html
theme: peter-theme
controls: true

--

![Web](images/game-art/web-goldcoins.svg)
![Payments](images/game-art/payments-silvercoins.svg)
## and the future of online purchases

<div class="contact">
  <p>Peter O'Shaughnessy</p>
  <p class="social">[@poshaughnessy](https://twitter.com/poshaughnessy)</p>
  <p class="social">[@samsunginternet](https://twitter.com/samsunginternet)</p>
</div>

-- img-with-caption five-images

![Very long form 1](images/very-long-checkout-form-1.png) ![Very long form 2](images/very-long-checkout-form-2.png) ![Very long form 3](images/very-long-checkout-form-3.png) ![Very long form 4](images/very-long-checkout-form-4.png) ![Very long form 5](images/very-long-checkout-form-5.png)

#### &ldquo;I just want to buy some socks&rdquo; 😱

--

## 66% fewer conversions on mobile than desktop

<div class="caption">Source: [Google Chrome](https://twitter.com/chromiumdev/status/796809709281939456)</div>

-- img-with-caption

![Cart abandoment reasons](images/cart-abandonment-reasons-trans.png)

<div class="caption">[baymard.com/lists/cart-abandonment-rate](https://baymard.com/lists/cart-abandonment-rate)</div>

-- img-with-caption bg-fade-more what-if

## What if your browser could help?

* <strong><em>For users:</em></strong> simple & secure experience
* <strong><em>For web devs:</em></strong> ready-to-use UI!

<div class="credit">By [Marc Falardeau](https://www.flickr.com/photos/49889874@N05/5645164344)</div>

-- bg-white

[![Payment Request API spec](images/payment-request-api-spec.png)](https://www.w3.org/TR/payment-request/)

-- bg-fade socks-stack

## 1. Our first sock sale

<h3 class="pun">&ldquo;Getting our <strong>foot</strong> in the door&rdquo;</h3>

<div class="credit">By [Gus Greeper](https://www.flickr.com/photos/gusgreeper/8329453791)</div>

--

![Sock sale](images/payment-request-socks-simple.png)

--

```javascript
if (window.PaymentRequest) {
  // We're good to go...
} else {
  // Alas! Use your legacy checkout form...
}
```

--

```javascript
var methodData = var methodData = [{
  // NB. To support older format, include networks here 
  supportedMethods: ['basic-card'],
  data: {
    // Examples. Others are available too!
    supportedNetworks: ['visa', 'mastercard', 'amex']
  }
}];

var details = {
  total: {
    label: 'Socks', 
    amount: {currency: 'GBP', value: '12.00'}
  }
};
```
--

```javascript
// Show the payment UI and handle the result

new PaymentRequest(methodData, details)
  .show()
  .then(function(uiResult) {
    myPaymentProcessor(uiResult);
  })
  .catch(function(error) {
    myErrorHandler(error);
  });
```

--

<video src="videos/socks-megastore-simple.mp4" controls></video>

<div class="caption">[samsunginter.net/examples/socks-megastore/after-simple/](http://samsunginter.net/examples/socks-megastore/after-simple/) &middot; [youtu.be/ruuJr30FCTw](https://youtu.be/ruuJr30FCTw)</div>

-- bg-fade socks-drawer

## 2. Adding customisations

<h3 class="pun">&ldquo;Thinking outside the <strong>socks</strong>&rdquo;</h3>

<div class="credit">By [Nikol Lohr](https://www.flickr.com/photos/sugarpants/5349120073)</div>

--

```javascript
var details = {
  displayItems: [
    {
      label: "Socks",
      amount: { currency: "GBP", value : "12.00" },
    },
    {
      label: "Loyalty discount",
      amount: { currency: "GBP", value : "-1.00" },
    }
  ],
  total: {
    label: 'Total', 
    amount: {currency: 'GBP', value: '11.00'}
  },
  ...
```
  
--

```javascript
  ...
  shippingOptions: [
    {
      id: 'standard',
      label: 'Standard shipping',
      amount: {currency: 'GBP', value: '1.50'},
      selected: true
    }
  ]
};
```

--

```javascript
var options = {
  requestPayerName: true,
  requestPayerEmail: true,
  requestPayerPhone: true,
  requestShipping: true
};

new PaymentRequest(methodData, details, options)
  ...
```

--

<video src="videos/socks-megastore-options.mp4" controls></video>

<div class="caption">[samsunginter.net/examples/socks-megastore/after-options/](http://samsunginter.net/examples/socks-megastore/after-options/) &middot; [youtu.be/BjEPBvn03i4](https://youtu.be/BjEPBvn03i4)</div>

-- browser-support three-images

## Browser support

<table>
  <tr>
    <td>![Chrome](images/chrome.png)</td>
    <td>![Samsung Internet](images/sbrowser5.0.png)</td>
    <td>![Edge Preview](images/edge.png)</td>
  </tr>
  <tr>
    <td>Chrome for Android v53+</td>
    <td>Samsung Internet v5.0+</td>
    <td>Edge Preview</td>
  </tr>
</table>

<div class="caption">[caniuse.com/#feat=payment-request](http://caniuse.com/#feat=payment-request)</div>

-- img-with-header

![Chrome desktop UI](images/chrome-desktop-socks.png)

<h4 class="pun">&ldquo;Good things are <strong>afoot</strong> on the desktop&rdquo;</h4>

<div class="caption">Currently [behind flags](https://twitter.com/poshaughnessy/status/841425232875286529) in Chrome Canary</div>

-- align-top img-with-caption

![Samsung Internet icon on homescreen](images/samsung-internet-beta-phone-blur.png)

<h3 class="pun">&ldquo;A <strong>shoe-in</strong> for your homescreen?</h3>

[bit.ly/samsung-internet-open-beta](http://bit.ly/samsung-internet-open-beta)

-- bg-white img-with-caption payment-gateways

### Payment Gateways

![Payment parties](images/web-payments-parties.png)

<p class="pun">&ldquo;You might <strong>knit</strong> to know this...&rdquo;</p>

-- logos bg-white

### Supporters include...

<div class="flex">![Groupon](images/groupon.png) ![Mobify](images/mobify.png) ![Shopify](images/shopify.png) ![Washington Post](images/washingtonpost.png) ![WePay](images/wepay.png) ![Woo Commerce](images/woocommerce.png) ![WWF](images/wwf.png)</div>

<h3 class="pun">&ldquo;Not just socks!&rdquo;</h3>

-- img-with-header

![Polykart](images/polykart.png)

<h3 class="pun">&ldquo;A lock, <strong>sock</strong> and barrel example&rdquo;</h3>

<div class="caption">[polykart-credential-payment.appspot.com](https://polykart-credential-payment.appspot.com/)</div>

--

## Future possibilities...

<h3 class="pun">&ldquo;It <strong>wool</strong> be great!&rdquo;</h3>

* Gift cards / coupons
* Mobile payment app integrations
* Credentials/tokenisation standardisation?

-- further-resources

## Further resources

<h3 class="pun">&ldquo;Following the same <strong>thread</strong>...&rdquo;</h3>

* [bit.ly/how-to-take-web-payments](medium.com/samsung-internet-dev/how-to-take-payments-on-the-web-with-the-payment-request-api-a523f6fc7c1f)
* [bit.ly/payment-request-api-guide](https://developers.google.com/web/fundamentals/discovery-and-monetization/payment-request/)
* [bit.ly/payment-request-updates](https://developers.google.com/web/updates/2017/01/payment-request-updates)
* [bit.ly/can-make-payment-sample](http://bit.ly/can-make-payment-sample)
* [bit.ly/wepay-integration-docs](http://bit.ly/wepay-integration-docs)

-- bg-fade socks-pile

# Thanks!

<h2 class="pun">&ldquo;Shoe wants to ask a question?&rdquo;</h2>

<div class="contact">
  <h3> [@poshaughnessy](https://twitter.com/poshaughnessy) </h3>
  <h3> [@samsunginternet](https://twitter.com/samsunginternet) </h3>
</div>

<div class="credit">By [darkmoon](https://www.flickr.com/photos/darkmoon/3572345244)</div>
