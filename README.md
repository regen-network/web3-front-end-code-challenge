# Web3 Front-end Code Challenge 

This challenge consists of building a React application integrated with [Keplr](https://wallet.keplr.app/) wallet that:

1. **Connects to Keplr** and displays your account balance on the [Regen Redwood Testnet](https://docs.regen.network/ledger/get-started/redwood-testnet.html).  
2. **Allows the user to send REGEN tokens** from their wallet to another address on the Redwood testnet.

**Key technologies**: React, TypeScript, Keplr and [@regen-network/api](https://www.npmjs.com/package/@regen-network/api) for querying and sending tokens.

---

## Setup

We recommend picking one of the [React-powered frameworks](https://react.dev/learn/start-a-new-react-project) popular in the community, though it's also fine if you have a different preferred way of bootstrapping a project.

You need [Keplr browser extension](https://chrome.google.com/webstore/detail/keplr/dmkamcknogkgcdfhhbddcghachkejeap) installed and configured.

---

## App Requirements

### 1. Connect to Keplr

Using the ["Suggest Chain" feature](https://docs.keplr.app/api/guide/suggest-chain) with the parameters below, ensure that the Regen Redwood Testnet is added to the user’s Keplr if it isn’t already. After that, your application should:

- Connect to the Redwood testnet.  
- Retrieve and display the user’s REGEN balance.

```ts
{
  chainId: 'regen-redwood-1',
  chainName: 'Regen Redwood Testnet',
  rpc: 'http://redwood.regen.network:26657/',
  rest: 'http://redwood.regen.network:1317/',
  stakeCurrency: {
    coinDenom: 'REGEN',
    coinMinimalDenom: 'uregen',
    coinDecimals: 6,
  },
  bip44: { coinType: 118 },
  bech32Config: {
    bech32PrefixAccAddr: 'regen',
    bech32PrefixAccPub: 'regenpub',
    bech32PrefixValAddr: 'regenvaloper',
    bech32PrefixValPub: 'regenvaloperpub',
    bech32PrefixConsAddr: 'regenvalcons',
    bech32PrefixConsPub: 'regenvalconspub',
  },
  currencies: [
    {
      coinDenom: 'REGEN',
      coinMinimalDenom: 'uregen',
      coinDecimals: 6,
    },
  ],
  feeCurrencies: [
    {
      coinDenom: 'REGEN',
      coinMinimalDenom: 'uregen',
      coinDecimals: 6,
      gasPriceStep: {
        low: 0.01,
        average: 0.025,
        high: 0.04,
      },
    },

  ],  
  features: ['stargate'],
}
```

---

### 2. Display Current REGEN Balance

Use either:
- [@regen-network/api](https://www.npmjs.com/package/@regen-network/api) (specifically cosmos bank module)
- or [CosmJS](https://github.com/cosmos/cosmjs)

...to query the on-chain balance. Display the user’s REGEN balance in the UI, ideally converting from `uregen` to `REGEN` (e.g., 1,000,000 `uregen` = 1 REGEN).

You can get some testnet token using https://docs.regen.network/ledger/get-started/redwood-testnet.html#testnet-tokens

---

### 3. Send REGEN Tokens

Add a form (or modal) that allows the user to:

- Enter a **recipient address**  
- Enter an **amount** of REGEN to send  
- **Submit** a transaction to transfer tokens

When the user clicks your "Send" button (or however you design it), your app should sign and broadcast the transaction using Keplr’s signer.

---

### 4. Basic UI/UX Requirements

- The page should be responsive. 
- Use a component-based approach in React.  
- Display the current wallet address and balance.  
- Provide a simple form to send tokens, plus success/error feedback.

---

## What We’re Looking For

- Clear React + TypeScript code structure  
- Simple, **clean** UI (no need for fancy styling)  
- **Readable, maintainable** code  
- A working flow for:
  1. Adding Redwood testnet to Keplr (if not already present)  
  2. Connecting with Keplr  
  3. Showing balance  
  4. Sending tokens

---

## Submission

- Put the finished code in a public repository on GitHub (or other hosting platform).  
- Include a `README.md` with clear instructions on how to build & run locally.  
- Send us a link to that repository.

We look forward to seeing your solution. Enjoy coding, and don’t hesitate to let us know if you run into any issues related to the testnet or tooling!
