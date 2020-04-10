# Factory API

## initializeFactory

{% tabs %}
{% tab title="Smart Contract" %}
```javascript
initializeFactory(template: address)
```
{% endtab %}

{% tab title="Web3" %}
```javascript
factoryContract.methods.initializeFactory(template).send()
```
{% endtab %}
{% endtabs %}

| Parameter | Description |
| :--- | ---: |
| template | RSK address of exchange template |

## createExchange

{% tabs %}
{% tab title="Smart Contract" %}
```javascript
createExchange(token: address): address
```
{% endtab %}

{% tab title="Web3" %}
```javascript
factoryContract.methods.initializeFactory(token).send()
```
{% endtab %}
{% endtabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| token | address | RSK address of an ERC20 token |

| Returns |  |
| :--- | ---: |
| address | RSK address of a RSKswap exchange |

## getExchange

{% tabs %}
{% tab title="Smart Contract" %}
```javascript
@constant
getExchange(token: address): address
```
{% endtab %}

{% tab title="Web3" %}
```javascript
factoryContract.methods.getExchange(token).call()
```
{% endtab %}
{% endtabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| token | address | RSK address of an ERC20 token |

| Returns |  |
| :--- | ---: |
| address | RSK address of a RSKswap exchange |

## getToken

{% tabs %}
{% tab title="Smart Contract" %}
```javascript
@constant
getToken(exchange: address): address
```
{% endtab %}

{% tab title="Web3" %}
```javascript
factoryContract.methods.getToken(exchange).call()
```
{% endtab %}
{% endtabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| exchange | address | RSK address of a RSKswap exchange |

| Returns |  |
| :--- | ---: |
| address | RSK address of an ERC20 token |

## getTokenWithId

{% tabs %}
{% tab title="Smart Contract" %}
```javascript
@constant
getTokenWithId(token_id: uint256): address
```
{% endtab %}

{% tab title="Web3" %}
```javascript
factoryContract.methods.getTokenWithId(token_id).call()
```
{% endtab %}
{% endtabs %}

| Parameter | Type | Description |
| :--- | :--- | ---: |
| token\_id | uint256 | RSKswap ID for an ERC20 token |

| Returns |  |
| :--- | ---: |
| address | RSK address of an ERC20 token |

