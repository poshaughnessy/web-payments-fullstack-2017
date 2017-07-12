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

-- img-with-caption five-images valign-top bg-sadmario

![Very long form 1](images/very-long-checkout-form-1.png) ![Very long form 2](images/very-long-checkout-form-2.png) ![Very long form 3](images/very-long-checkout-form-3.png) ![Very long form 4](images/very-long-checkout-form-4.png) ![Very long form 5](images/very-long-checkout-form-5.png)

<div class="credit">[Travis Estell](https://www.flickr.com/photos/taestell/27988335225)</div>

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

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

-- bg-marioblock bg-fade what-if

### What if...

![Saved details](images/payment-request-remembered-details.png)

<div class="caption">Your browser could securely remember your payment & shipping details?</div>

<div class="credit">[Leandro Amato](https://www.flickr.com/photos/grunge/2829427342)</div>

-- bg-marioblock bg-fade what-if

### What if...

![Fingerprint scan](images/fingerprint-s8.png)

<div class="caption">You could confirm the payment with your fingerprint or iris scan?</div>

<div class="credit">[Leandro Amato](https://www.flickr.com/photos/grunge/2829427342)</div>

-- img-with-caption bg-insertcoin bg-fade

# Web Payments

<div class="caption">[www.w3.org/Payments/WG/](https://www.w3.org/Payments/WG/)</div>

<div class="credit">[Jan W](https://www.flickr.com/photos/63883151@N07/8486121888)</div>

--

[![Payment Request API spec](images/payment-request-api-spec.png)](https://www.w3.org/TR/payment-request/)

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

-- gold-coins bg-mariocoin1 bg-fade

## 1. Our first sale

![Gold coins](images/game-art/goldcoin2/coins-less.svg)

<div class="credit">[Aviery Edison](https://www.flickr.com/photos/kylemhayes/3746664569)</div>

--

![Sock sale](images/payment-request-socks-simple.png)

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

--

```javascript
if (window.PaymentRequest) {
  // We're good to go...
} else {
  // Alas! Use your legacy checkout form...
}
```

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

--

```javascript
var methodData = [{
  // NB. To support older format, include networks here 
  supportedMethods: ['basic-card'],
  data: {
    // Examples. Others are available too!
    supportedNetworks: ['visa', 'mastercard', 'amex']
  }
}];
```

--

```javascript
var details = {
  total: {
    label: 'Socks', 
    amount: {currency: 'GBP', value: '12.00'}
  }
};
```

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

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

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

--

<video src="videos/socks-megastore-simple.mp4" controls></video>

<div class="caption">[samsunginter.net/examples/socks-megastore/after-simple/](http://samsunginter.net/examples/socks-megastore/after-simple/)</div>

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

-- gold-coins bg-mariocoin2 bg-fade

## 2. Adding options

![More gold coins](images/game-art/goldcoin2/coins-more.svg)

<div class="credit">[Kent Brewster](https://www.flickr.com/photos/kentbrew/2550957151)</div>

--

```javascript
var details = {
  displayItems: [
    ...
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

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>
  
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

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

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

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

--

<video src="videos/socks-megastore-options.mp4" controls></video>

<div class="caption">[samsunginter.net/examples/socks-megastore/after-options/](http://samsunginter.net/examples/socks-megastore/after-options/)</div>

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

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
</div>

<div class="caption">[caniuse.com/#feat=payment-request](http://caniuse.com/#feat=payment-request)</div>

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

-- browser-support three-images

### Also in the Working Group...

<div class="container">
  <div>
    ![Firefox](images/firefox.png)
    <p>Mozilla</p>
  </div>
  <div>
    ![Safari](images/safari.png)
    <p>Apple</p>
  </div>
  <div>
    ![Facebook](images/facebook.png)
    <p>Facebook</p>
  </div>
</div>

<div class="caption">[And many more](https://www.w3.org/2004/01/pp-impl/83744/status)</div>

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

-- img-with-header

![Chrome desktop UI](images/chrome-desktop-socks.png)

<div class="caption">Desktop Chrome</div>

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

-- img-with-header

![DeX UI](images/dex-desktop-socks.png)

<div class="caption">Samsung DeX</div>

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

<!-- img-with-caption payment-gateways-->
<!--### Payment Gateways-->
<!--![Payment parties](images/web-payments-parties.png)-->
<!--<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>-->

<!-- logos -->
<!-- ### Supporters include... -->
<!-- TODO switch this for a couple of individual examples e.g. Monzo? -->
<!-- <div class="flex">![Groupon](images/groupon.png) ![Mobify](images/mobify.png) ![Shopify](images/shopify.png) ![Washington Post](images/washingtonpost.png) ![WePay](images/wepay.png) ![Woo Commerce](images/woocommerce.png) ![WWF](images/wwf.png)</div> -->
<!-- <div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div> -->

<!-- img-with-header-->
<!--![Polykart](images/polykart.png)-->
<!--<div class="caption">[polykart-credential-payment.appspot.com](https://polykart-credential-payment.appspot.com/)</div>-->
<!--<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>-->

-- img-with-header

### Real example: Monzo 

![Monzo Payment Request](images/monzo2.png)

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

-- bg-marioblock bg-fade what-if

## What's next?

<div class="credit">[Leandro Amato](https://www.flickr.com/photos/grunge/2829427342)</div>

-- two-images mobile-app-integrations

### Payment app integrations

![Android Pay](images/android-pay.png)
![Samsung Pay](images/samsung-pay.png)

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

-- img-with-header payment-handler-api

### Payment Handler API

![Payment Handler API](images/payment-handler-api.png)

<div class="caption">[bit.ly/payment-handler-api](http://bit.ly/payment-handler-api)</div>

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>

<!-- -- -->
<!-- ### Lots More... -->
<!-- * Payment Method Manifest -->
<!-- * Basic Credit Transfer Payment -->
<!-- * Tokenised Card Payment -->
<!-- * Web Payments HTTP API 1.0 -->
<!-- <div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div> -->

-- thanks bg-mariohooray

# Thanks!

![Spinning coin](images/game-art/goldcoin/coin-spin.gif)

Please leave feedback on this talk!

[bit.ly/peter-fullstack-17](https://bit.ly/peter-fullstack-17)

<p style="margin-top: 2em;">Follow us for webby goodness!</p>

<div class="contact">
  <h3 class="social"> [@poshaughnessy](https://twitter.com/poshaughnessy) </h3>
  <h3 class="social"> [@samsunginternet](https://twitter.com/samsunginternet) </h3>
</div>

<div class="credit">[Laurence Vagner](https://www.flickr.com/photos/redisdead/2165783016)</div>

-- further-resources

## Further resources

* [github.com/w3c/payment-request-info](https://github.com/w3c/payment-request-info)
* [github.com/w3c/payment-request-info/wiki/FAQ](https://github.com/w3c/payment-request-info/wiki/FAQ)
* [medium.com/samsung-internet-dev/how-to-take-payments-on-the-web-with-the-payment-request-api-a523f6fc7c1f](medium.com/samsung-internet-dev/how-to-take-payments-on-the-web-with-the-payment-request-api-a523f6fc7c1f)
* [developers.google.com/web/fundamentals/discovery-and-monetization/payment-request/](https://developers.google.com/web/fundamentals/discovery-and-monetization/payment-request/)

<div class="credit">[Ray Che](https://www.flickr.com/photos/rayche1989/5203972988)</div>