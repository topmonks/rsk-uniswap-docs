# Getting Started

{% hint style="info" %}
These docs are still being worked on. Some parts may be unfinished
{% endhint %}

Based on the [Uniswap](https://uniswap.org/) protocol RSKswap provides an interface for seamless exchange of ERC20 tokens on RSK. By eliminating unnecessary forms of rent extraction and middlemen it allows faster, more efficient exchange. Where it makes tradeoffs, decentralization, censorship resistance, and security are prioritized.

RSKswap is open source and functions as a public good. There is no central token or platform fee. No special treatment is given to early investors, adopters, or developers. Token listing is open and free. All smart contract functions are public and all upgrades are opt-in.

This site will serve as a project overview for RSKswap - explaining how it works, how to use it, and how to build on top of it. These docs are actively being worked on and more information will be added on an ongoing basis.

## Features

* Add support for any ERC20 token using the RSKswap [factory](https://github.com/Uniswap/contracts-vyper/blob/master/contracts/uniswap_factory.vy)
* [Join liquidity pools](frontend-integration/pool.md#add-liquidity) to collect fees on RBTC-ERC20 pairs
* Liquidity-sensitive automated pricing using [constant product formula](https://github.com/runtimeverification/verified-smart-contracts/blob/uniswap/uniswap/x-y-k.pdf)
* Trade [RBTC for any ERC20](frontend-integration/swap.md#eth-erc20-trades) without wrapping
* Trade any [ERC20 for any ERC20](frontend-integration/swap.md#erc20-to-erc20) in a single transaction
* Trade and transfer to a different address in a single transaction
* Lowest gas cost of any decentralized exchange
* Support for private and custom exchanges
* Buy ERC20 tokens from any wallet using ENS
* [Partially verified](https://github.com/runtimeverification/verified-smart-contracts/tree/uniswap/uniswap) smart contracts written in Vyper
* Mobile-optimized open source [frontend implementation](https://github.com/Uniswap/uniswap-frontend)  

## Resources

* [Defi for Bitcoin](https://developers.rsk.co/defi/index.html)
* [Github](https://github.com/Uniswap)
* [Whitepaper](https://hackmd.io/s/HJ9jLsfTz)

## How it works

RSKswap is made up of a series of RBTC-ERC20 exchange contracts. There is exactly one exchange contract per ERC20 token. If a token does not yet have an exchange it can be created by anyone using the RSKswap factory contract. The factory serves as a public registry and is used to look up all token and exchange addresses added to the system.

Each exchange holds reserves of both RBTC and its associated ERC20 token. Anyone can become a liquidity provider on an exchange and contribute to its reserves. This is different than buying or selling; it requires depositing an equivalent value of both RBTC and the relevant ERC20 token. Liquidity is pooled across all providers and an internal "pool token" \(ERC20\) is used to track each providers relative contribution. Pool tokens are minted when liquidity is deposited into the system and can be burned at any time to withdraw a proportional share of the reserves.

Exchange contracts are automated market makers between an RBTC-ERC20 pair. Traders can swap between the two in either direction by adding to the liquidity reserve of one and withdrawing from the reserve of the other. Since RBTC is a common pair for all ERC20 exchanges, it can be used as an intermediary allowing direct ERC20-ERC20 trades in a single transaction. Users can specify a recipient address if they want to receive purchased tokens at a different address from the one used to make a transaction.

![ERC20 to ERC20 trades in RSKswap](.gitbook/assets/erc20-to-erc20.png)

RSKswap uses a "constant product" market making formula which sets the exchange rate based off of the relative size of the RBTC and ERC20 reserves, and the amount with which an incoming trade shifts this ratio. Selling RBTC for ERC20 tokens increases the size of the RBTC reserve and decreases the size of the ERC20 reserve. This shifts the reserve ratio, increasing the ERC20 token's price relative to RBTC for subsequent transactions. The larger a trade relative to the total size of the reserves, the more price slippage will occur. Essentially, exchange contracts use the open financial market to decide on the relative value of a pair and uses that as a market making strategy.

A small liquidity provider fee \(0.3%\) is taken out of each trade and added to the reserves. While the RBTC-ERC20 reserve ratio is constantly shifting, fees makes sure that the total combined reserve size increases with every trade. This functions as a payout to liquidity providers that is collected when they burn their pool tokens to withdraw their portion of total reserves. Guaranteed arbitrage opportunities from price fluctuations should push a steady flow of transactions through the system and increase the amount of fee revenue generated.

Since RSKswap is entirely on-chain, prices can change between when a transaction is signed and when it is included in a block. Traders can bound price fluctuations by specifying the minimum amount bought on sell orders, or the maximum amount sold on buy orders. This acts as a limit order that will automatically cancel if it is not filled. It is also possible to set transaction deadlines which will cancel orders if they are not executed fast enough.

The reason only one exchange per token can be registered to the factory is to encourage providers to pool their liquidity into a single reserve. However, RSKswap has built in support for ERC20-to-ERC20 trades using the public pools from the factory on one side of the transaction and custom, user-specified pool on the other. Custom pools could have fund managers, use alternate pricing mechanisms, remove liquidity provider fees, integrate complex three dimensional fomo-based ponzi-schemes and more. They just need to implement the RSKswap interface and accept RBTC as an intermediary asset. Custom pools do not have the same safety properties as the public ones. It is recommended users only interact with audited, open-source smart contracts.

Upgrading censorship resistant, decentralized smart contracts is difficult. If significant improvements are made to the system a new version will be released. Liquidity providers can choose between moving to the new system or staying in the old one. If possible, new versions will be backwards compatible and able to trade ERC20-to-ERC20 with the old versions similar to a custom pool.

## How to use it

The RSKswap smart contracts live on RSK. Anyone can interact with them directly.

The RSKswap frontend is an open source interface designed to improve user experience when interacting with the smart contracts. Anyone can use the source code to host an interface, or build their own. Hosted interfaces are independent of RSKswap, and should comply with their jurisdictional laws and regulations.

### List of interfaces

* [rskswap.prod.tmcloud.io](https://rskswap.prod.tmcloud.io/)

