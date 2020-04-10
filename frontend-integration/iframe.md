# iFrame Integration

RSKswap can be used within other sites as an iframe. An iframe shows an exact version of the exchange site and can have custom prefilled settings.

## Why You May Want This

Integrating the RSKswap site directly into your web application can be useful for a variety of reasons.

Exchange site allows users to buy, sell, send, or provide liquidity for ERC20 tokens. An iframe integration may be useful if your application provides services around these ERC20 tokens. \(For example, users can buy RIF through a RSKswap iframe on your site, then allow users to lend that DAI on your site\).

It can also be useful if your application requires users to acquire some token in order to use some service \(For example, allow users to buy "REP" token so they can engage in prediction markets on the Augur Dapp\).

## iframe vs. custom UI

One benefit of an iframe integration is that the your site will automatically keep up with any improvements/additions to the exchange site. After the initital integration is setup no further work is needed to pull in updates as the exchange site is updated over time.

## Live Example

An example of an Iframe integration can be found on the FOAM site [https://map.foam.space/](https://map.foam.space/#/at/?lng=-74.0045300&lat=40.6771800&zoom=5.00)

To see the Iframe click the dropdown in the top right and click "get foam".

![Foam Iframe Example](../.gitbook/assets/foamiframe.png)

## Add To Your Site

To include a RSKswap iframe within your site just add an iframe element within your website code and link to the RSKswap exchange.

Linking to a RBTC &lt;-&gt; DAI swap page would look something like this. To link to a token of your choice replace the address after "outputCurrency" with the token address of the token you want to link to.

```text
<iframe
  src="https://rskswap.prod.tmcloud.io/swap?outputCurrency=0x89d24a6b4ccb1b6faa2625fe562bdd9a23260359"
  height="660px"
  width="100%"
  style="
    border: 0;
    margin: 0 auto;
    display: block;
    border-radius: 10px;
    max-width: 600px;
    min-width: 300px;
  "
  id="myId"
/>
```

You can customize the selected page, selected custom tokens and more using URL query parameters. See [Linking](frontend-integration/linking.md) for more.

