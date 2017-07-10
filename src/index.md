title: Web Payments
output: public/index.html
theme: peter-theme
controls: false

--

![Web](images/game-art/web-goldcoins.svg)
![Payments](images/game-art/payments-goldcoins.svg)
## and the future of online purchases

<div class="contact">
  <p class="social">[@poshaughnessy](https://twitter.com/poshaughnessy)</p>
  <p class="social">[@samsunginternet](https://twitter.com/samsunginternet)</p>
</div>

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

-- img-with-caption five-images

![Very long form 1](images/very-long-checkout-form-1.png) ![Very long form 2](images/very-long-checkout-form-2.png) ![Very long form 3](images/very-long-checkout-form-3.png) ![Very long form 4](images/very-long-checkout-form-4.png) ![Very long form 5](images/very-long-checkout-form-5.png)

#### &ldquo;I just wanna buy something&rdquo;

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

-- bg-goomba valign-top

## 69% of shopping carts are abandoned

<div class="caption">Source: [Baymard Institute](https://baymard.com/lists/cart-abandonment-rate)</div>

<div class="credit">[Flavio Ensiki](https://www.flickr.com/photos/flavouz/5086859227)</div>

-- bg-booghost valign-top

## 84% abandonment rate on mobile

<div class="caption">Source: [Cloud.IQ via econsultancy.com](https://econsultancy.com/blog/64343-checkout-abandonment-mobile-ux-examples-to-help-boost-conversions/)</div>

<div class="credit">[Fujoshi Bijou](https://www.flickr.com/photos/fujoshi/4277809127)</div>

-- img-with-caption

![Cart abandoment reasons](images/cart-abandonment-reasons-trans.png)

<div class="caption">[baymard.com/lists/cart-abandonment-rate](https://baymard.com/lists/cart-abandonment-rate)</div>

-- img-with-caption bg-bowser bg-fade

## Web Payments to the rescue

--

[![Payment Request API spec](images/payment-request-api-spec.png)](https://www.w3.org/TR/payment-request/)

-- gold-coins bg-mariocoin1 bg-fade

## 1. Our first sale

![Gold coins](images/game-art/goldcoin2/coins-less.svg)

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

<div class="caption">[samsunginter.net/examples/socks-megastore/after-simple/](http://samsunginter.net/examples/socks-megastore/after-simple/)</div>

-- gold-coins bg-mariocoin2 bg-fade

## 2. Adding options

![More gold coins](images/game-art/goldcoin2/coins-more.svg)

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

<div class="caption">[samsunginter.net/examples/socks-megastore/after-options/](http://samsunginter.net/examples/socks-megastore/after-options/)</div>

-- browser-support four-images

## Browser support

<div class="container">
    <div>
      ![Chrome](images/chrome.png)
      <p>Chrome desktop beta (v53+ with flag)</p>
    </div>
    <div>
      ![Chrome for Android](images/chrome-android.png)
      <p>Chrome for Android v53+</p>
    </div>
    <div>
      ![Samsung Internet](images/sbrowser5.4.png)
      <p>Samsung Internet v5.0+</p>
    </div>
    <div>
      ![Edge Preview](images/edge.png)
      <p>Edge v15+</p>
    </div>
  </tr>
  <tr>
</div>

<div class="caption">[caniuse.com/#feat=payment-request](http://caniuse.com/#feat=payment-request)</div>

-- img-with-header

![Chrome desktop UI](images/chrome-desktop-socks.png)

<div class="caption">Here's how it looks on desktop</div>

-- img-with-header

TODO try on DeX

<div class="caption">And in Samsung DeX</div>

-- img-with-caption payment-gateways

### Payment Gateways

![Payment parties](images/web-payments-parties.png)

-- logos bg-white

### Supporters include...

<div class="flex">![Groupon](images/groupon.png) ![Mobify](images/mobify.png) ![Shopify](images/shopify.png) ![Washington Post](images/washingtonpost.png) ![WePay](images/wepay.png) ![Woo Commerce](images/woocommerce.png) ![WWF](images/wwf.png)</div>

-- img-with-header

![Polykart](images/polykart.png)

<div class="caption">[polykart-credential-payment.appspot.com](https://polykart-credential-payment.appspot.com/)</div>

--

## What's next?

* Mobile payment app integrations
* Payment Handler API
* Gift cards / coupons?
* Credentials/tokenisation standardisation?

-- thanks

# Thanks!

![Spinning coin](images/game-art/goldcoin/coin-spin.gif)

<div class="contact">
  <h3 class="social"> [@poshaughnessy](https://twitter.com/poshaughnessy) </h3>
  <h3 class="social"> [@samsunginternet](https://twitter.com/samsunginternet) </h3>
</div>

-- further-resources

## Further resources

* [bit.ly/how-to-take-web-payments](medium.com/samsung-internet-dev/how-to-take-payments-on-the-web-with-the-payment-request-api-a523f6fc7c1f)
* [bit.ly/payment-request-api-guide](https://developers.google.com/web/fundamentals/discovery-and-monetization/payment-request/)
* [bit.ly/payment-request-updates](https://developers.google.com/web/updates/2017/01/payment-request-updates)
* [bit.ly/can-make-payment-sample](http://bit.ly/can-make-payment-sample)
* [bit.ly/wepay-integration-docs](http://bit.ly/wepay-integration-docs)

