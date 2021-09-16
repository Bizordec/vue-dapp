# Vue Dapp

Vue 3 composable and components library for building Dapps with ethers.js.

- 👀 [Demo](https://vue-dapp-demo.netlify.app/)
- 🌏 [Documentation(v0.4.0)](https://vue-dapp-docs.netlify.app/)


## Features
- TypeScript for safe and efficient development.
- [Ethers](https://docs.ethers.io/v5/) for interacting with Ethereum.
- [Multicall2](https://github.com/makerdao/multicall) for calling multiple constant function call into one request.


## Quick Start

Install dependencies:

```bash
npm install --save ethers vue-dapp

yarn add ethers vue-dapp
```

Add dependencies to your main.ts:

```javascript
import { VueDapp } from 'vue-dapp'

const app = createApp(App)

app.use(VueDapp, {
  infuraId: '', // for enabling WalletConnect
})
...
```

Add the global component to your App.vue:

```vue
<vdapp-board />
```

Use wallet or board from your .vue files:

```javascript
import { defineComponent } from 'vue'
import { useBoard, useEthers, useWallet } from 'vue-dapp'

export default defineComponent({
  name: 'App',
  setup() {
    const { open } = useBoard()
    const { status, disconnect, error } = useWallet()
    const { address, isActivated } = useEthers()
    

    return {
      address,
      status,
      error,
      disconnect,
      open,
    }
  },
})
```

Add CDN in index.html for enabling WalletConnect:

```html
<body>
  <div id="app"></div>

  <!-- this line -->
  <script src="https://cdn.jsdelivr.net/npm/@walletconnect/web3-provider@1.6.5/dist/umd/index.min.js"></script>
  <script type="module" src="/src/main.ts"></script>
</body>
```
(More about [issue of walletconnect](https://github.com/chnejohnson/vue-dapp/issues/3))

## Contributing

You are more than welcome to improve this project.

Just submit your changes via pull request and I will review them before merging.

If you are making a fix on the project, you can use the `main` branch and send a pull request.

If you are adding a new features, please create a new branch with a name describing your feature (`my-new-feature`), push to your branch and then submit a pull request.

## Inspiration
- [useDapp: Framework for rapid Dapp development.](https://github.com/EthWorks/useDApp)
- [vue-tailwind-ethereum-template](https://github.com/ScopeLift/vue-tailwind-ethereum-template)
- [web3Modal: A single Web3 / Ethereum provider solution for all Wallets](https://github.com/Web3Modal/web3modal)
- [vue3-eth: Vue3 library for building Dapps in an ES module environment](https://github.com/samatechtw/vue3-eth)

## License

[MIT](https://opensource.org/licenses/MIT)

Copyright (c) 2021-present, Johnson Chen