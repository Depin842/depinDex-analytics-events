# Depin Dex Labs Analytics Events


The `depin-dex-analytics-events` package is a [npm package](https://www.npmjs.com/package/depin-dex-analytics-events) of constants used as the inputs into our [depin-dex-analytics](https://www.npmjs.com/package/depin-dex-analytics) package.

## Installation

Install via `npm` or `yarn`.

```bash
yarn add depin-dex-analytics-events
```

```bash
npm i --save depin-dex-analytics-events
```

## Adding Events

Events are composed of an event name, event properties, and user properties. Event names, event properties, and property values are defined by enumerations in this repository to ensure ensure that event logging is not prone to misspelling, inconsistency, repetition, or unexpected logged values.

This README will go over how to design, name, organize, and test your event names, event properties, and property values.

Here is a short illustrative example of what events will look like in code once defined:

```javascript
// Event names example
export enum NFTBuyEvents {
  NFT_BUY_ADDED = 'NFT Buy Bag Added',
  NFT_BUY_BAG_CHANGED = 'NFT Buy Bag Changed',
  NFT_BUY_BAG_REFUNDED = 'NFT Buy Bag Refunded',
  NFT_BUY_BAG_SIGNED = 'NFT Buy Bag Signed',
  NFT_BUY_BAG_SUCCEEDED = 'NFT Buy Bag Succeeded',
}

// Event properties example
export enum WalletEventProperties {
    WALLET_ADDRESS = 'wallet_address',
    TO_ADDRESS = 'to_address',
    TIMESTAMP_EPOCH_SECONDS = 'timestamp_epoch_seconds',
}

// Property values example
export enum DocsSentiment {
  NEGATIVE_SENTIMENT = 'Negative Sentiment',
  NEUTRAL_SENTIMENT = 'Neutral Sentiment',
  POSITIVE_SENTIMENT = 'Positive Sentiment',
}

## Testing Events

For rapid development, a convenience flow is available that allows you to do the following in a single command:
- create a tarball copy of the latest events
- copy this tarball to the specified project
- install this package in the specified project

To set this up, define the following environment variables (in your bash/zsh profile or as desired):
```bash
export ANALYTICS_IMPLEMENTING_REPO_PATH={PATH}
export ANALYTICS_IMPLEMENTING_REPO_INSTALL={npm|yarn}
```
Once set up, run the following command to run the sequence above:

```bash
yarn tarball:install
```

This flow also clears your `tmp` cache only for yarn, ensuring yarn install times are not degraded after testing your analytics changes.

When you're done testing, undo the changes so you don't commit the temporary file to remote:

### Manually Installing

To test generate a tarball of the new test package and install it directly, using the following command:

```bash
yarn tarball
```

This will generate a `depin-dex-analytics-events-dev.tgz` including your changes and a `0.0.1` package version number.

To install it in your implementing repo, copy/move the tarball to the top level of your implementing repo and then run the following commands:

```bash
# yarn
yarn cache clean
yarn add file:depin-dex-analytics-dev.tgz

# npm
npm install depin-dex-analytics-dev.tgz
```
