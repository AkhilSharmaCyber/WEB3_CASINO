<p align="center"><img src="CASINO_DAPP/casino-dapp/public/assets/img/sidebar-icon.png" align="center" width="250"></p>
<h2 align="center">Next.js Web3 casino</h2>

<!-- <p align="center"><b>🎰 Next.js + Material UI + React +  + web3 casino⚡</b></p> -->
[![NODE](https://img.shields.io/badge/NODE-18.12.1_(LTS)-blue)](https://nodejs.org/en/blog/release/v18.12.1)
[![NPM](https://img.shields.io/badge/NPM-8.19.2-blue)](https://www.npmjs.com/package/npm/v/8.19.2)
[![NEXT](https://img.shields.io/badge/NEXT-v13.4.5-blue)](https://www.npmjs.com/package/next/v/13.4.5)
[![LICENSE](https://img.shields.io/badge/LICENSE-MIT-blue)](https://github.com/MiguelGGMM/WEB3_CASINO/blob/master/LICENSE)
[![CHAINLINKDF](https://img.shields.io/badge/CHAINLINK-DATAFEEDS-green)](https://data.chain.link/)
[![CHAINLINKVRF](https://img.shields.io/badge/CHAINLINK-VRF-green)](https://docs.chain.link/vrf/v2/introduction)
[![UNISWAPV3](https://img.shields.io/badge/UNISWAP-V3-green)](https://docs.uniswap.org/contracts/v3/overview)

## About

<p>This is a web3 casino dapp using mainly <a href=https://www.npmjs.com/package/next target="_blank">Next.js</a> and <a href=https://mui.com/material-ui/getting-started/overview/ target="_blank">material UI</a>, in addition to: <a href=https://www.npmjs.com/package/react target="_blank">react</a>, <a href=https://getbootstrap.com/ target="_blank">bootstrap</a>, <a href=https://tailwindcss.com/ target="_blank">tailwind</a>, <a href=https://sass-lang.com/guide/ target="_blank">scss</a>, <a href=https://www.typescriptlang.org/ target="_blank">typescript</a> and <a href=https://www.npmjs.com/package/typechain target="_blank">typechain</a> in order to generate types for contract calls.</p>
<p>About typechain: it's a common problem that <a href=https://www.npmjs.com/package/ethers target="_blank">ethers</a> and <a href=https://www.npmjs.com/package/web3 target="_blank">web3</a> libraries generate dinamically functions from json abi, so you can not use typescript with these libraries (unless you generate the types manually), typechain generates automatically the *.ts files using the SOLIDITY compiler *.json build files (compiler output) solving the problem.</p>
<p>Contracts testing against mainnet and test are also included using <a href=https://www.npmjs.com/package/truffle target="_blank">truffle</a> and <a href=https://www.npmjs.com/package/ganache target="_blank">ganache</a></p>

  
## Webcome to the descentralized WEB3 CASINO!

<p>The objective of this project is PURELY DIDACTIC<p>
<p>Exemplify how blockchain technology can be used to build a totally transparent open source web3 casino, rid of owner priviledges, using trusted third party services like <a href=https://data.chain.link/ target="_blank">chainlink</a> in order to ensure fair bet solving, smart contracts designed and deployed on <a href=https://arbiscan.io/ target="_blank">arbitrum</a> blockchain and leading edge technologies like react, next, bootstrap, tailwind and open source <a href=https://github.com/Uniswap/web3-react/tree/main target="_blank">web3 libraries</a> that allows user authenticate himself, retrive contract data and sign transactions in order to perform bets.</p>

## Vercel deployment

<a href=https://vercel.com/workflow>Vercel</a> enables built-in CI/CD for your frontend project
<img>https://web3-casino.vercel.app/</img>

## CI

We have talked about Vercel built-in CI/CD, however, we are using [vercel CLI](https://github.com/vercel/examples/tree/main/ci-cd/github-actions) because we want full control of our CI/CD workflow, .yml files has been added for preview (dev branch) and production (main branch), code checks like prettier and linter are run in parallel with vercel build, once both finish successfully our built project is deployed on vercel

Also a separated file for CI has been added in order to test the contracts, it is a very simple version, if you want see something more elaborated that includes linter and prettifier for typescript tests files and solidity contracts together with codechecks for gas report and coveralls for solidity coverage.

## Previews and videos

<a href=https://res.cloudinary.com/dxouzehk9/video/upload/v1687902978/web3_casino/won-roulette_xkkdu8.mp4 target="_blank"><picture><img target="_blank" src="https://github.com/MiguelGGMM/WEB3_CASINO/assets/104460442/fa513197-5ae2-495a-a050-e8cb7e3de5a8" /></picture></a>

<a href=https://res.cloudinary.com/dxouzehk9/video/upload/v1687902977/web3_casino/lost-roulette_kvuywe.mp4 target="_blank"><picture><img target="_blank" src="https://github.com/MiguelGGMM/WEB3_CASINO/assets/104460442/23a14359-d5c1-480e-97d6-59743251caf9" /></picture></a>

## How works?

-SOLIDITY directory enables you to test and deploy the web3 casino smart contracts, there is mainly 2 contracts, one is used for casino treasury where users deposit eth for bets and 
eth collected is stored, this contract exists for scalability and security reasons, will allows you to add new contracts that could be developed in near future and independently of how much contracts/games your casino have users will have to deposit their eth using always the same contract.  
-There is some fee applied on users bet (5%) that will be used to buy LINK against uniswapV3 liquidity pool and fund chainlink subscription automatically for VRF (Verifiable Randomness Function -> bet solving).  
-If bet solving takes too much users also can cancel their bet and get their funds back.  
-There is a manual bet solving in case chainlink takes too much but ideally owners should renounce contract and use chainlink VRF.  
-Bets amounts are in $ and price is calculated using a chainlink datafeed.  
-CASINO_DAPP directory is the next DAPP used as UI to interact with the roulette, show data and sign transactions against the smart contracts.  
-This project should work on any EVM based chain but contract addresses and chain settings has to be set on .env and .env.local files.  


## Quick start

The first thing you need to do is clone repo.

Before compile and deploy contracts you have to set some .env addresses following the .env.sample these address can vary depending on the chain you want to deploy, if you want deploy in arbitrum mainnet use the default values

### To compile and test contracts against the arbitrum mainnet

```bash
cd SOLIDITY
```

Install libraries

```bash
pnpm install
```

Initialize ganache

```bash
pnpm run ganacheFork
```

Run the tests

```bash
pnpm run test
```

### Deploy contracts against arbitrum mainnet

```bash
pnpm run deploy
```

### If you want to verify the contracts you can use

```bash
pnpm run verify
```

If you want deploy against another chain, you can edit arbitrumOneMainnet in truffle-config.js, setting provider url, chain id and gas settings should do the trick,
don't forget set your pk on .pk file and your block explorer key on .blockExplorerKey file if you want to verify the contracts.

Only casino treasury and roulette contracts will be verified, if you want to verify the internal roulette managers you have to do it manually using your blockchain explorer, providing the code and the constructor parameters encoded (you can use this to encode your parameters https://abi.hashex.org/).

Initialize the contracts bets following the test files and set the contract addresses RPC and chain on the .env.local, contract deployed by me are set by default

### Run the client

```bash
cd ..
cd CASINO_DAPP/casino-dapp
pnpm install
pnpm run dev
```

## Project Structure SOLIDITY

```
📦SOLIDITY                   // Solidity part of the project you will need for smart contract deployment and testing
 ┣ 📂build 
 ┃ ┗ 📂contracts             // automatically generated json output from compiler, is used by typechain to generate types
 ┣ 📂contracts 
 ┃ ┗ 📂current 
 ┃ ┃ ┣ 📂BasicLibraries      // basic smart contracts, most commonly used     
 ┃ ┃ ┣ 📂Chainlink           // chainlink interfaces in order to communicate with chainlink contract for random number generation and safe bet solving
 ┃ ┃ ┣ 📂Libraries           // casino treasury and roulette libraries
 ┃ ┃ ┣ 📂UniswapV3           // uniswap libraries, used to buy link against liquidity pair and fund chainlink susbcription manually
 ┃ ┃ ┣ 📜CasinoTreasury.sol  // casino treasury where users eth and eth for bets is stored, users only have to send eth to one unique contract
 ┃ ┃ ┗ 📜Roulette.sol        // main roulette contract
 ┣ 📂migrations              // contracts deployment
 ┃ ┗ 📜1_migration.js 
 ┣ 📂test                    // test files, you can check it using 'npm run test' after setting up ganache with 'npm run ganacheFork'
 ┃ ┗ 📜1_test_basic_ini.js 
 ┣ 📜.blockExplorerKey       // (remove .sample from blockExplorerKey.sample) the key used for smart contract verification
 ┣ 📜.blockExplorerKey.sample// empty .blockExplorerKey file
 ┣ 📜.env                    // (remove .sample from .env.sample) env file that contains the addresses variables required for smart contract deployment
 ┣ 📜.env.sample             // default .env file
 ┣ 📜.pk                     // (remove .sample from .pk.sample) the pk of the account you will use for deployment
 ┣ 📜.pk.sample              // empty .pk file
 ┣ 📜package.json            
 ┗ 📜truffle-config.js       // truffle config file where you can edit chain settings for test and deployment
```

## Project Structure CASINO_DAPP

```
📦CASINO_DAPP\casino-dapp    // DAPP part of the project
┣📦app
┣📦custom-types              // custom typescript types
┃ ┗ 📜index.d.ts
┣📦public
┃ ┣ 📂assets
┃ ┃ ┣ 📂css                  // mainly bootstrap and tailwind css files
┃ ┃ ┣ 📂img                                 
┃ ┃ ┣ 📂js                   // soft-ui and bootstrap js
┃ ┃ ┣ 📂media                // roulette sounds
┃ ┃ ┃ ┗ 📂sounds
┃ ┃ ┃ ┃ ┣ 📜lose.mp3
┃ ┃ ┃ ┃ ┣ 📜roulette.mp3
┃ ┃ ┃ ┃ ┗ 📜winner.mp3
┃ ┃ ┗ 📂scss                 // scss files
┃ ┃ ┃ ┣ 📂soft-design-system
┃ ┃ ┃ ┣ 📂soft-ui-dashboard
┃ ┃ ┃ ┣ 📜soft-design-system.scss
┃ ┃ ┃ ┗ 📜soft-ui-dashboard.scss
┣📦redux                     // redux files
┃ ┣ 📂actions
┃ ┣ 📂reducers
┃ ┣ 📂types
┣📦src
┃ ┣ 📂abis                   // typescript files automatically generated by typechain
┃ ┣ 📂betsConfig             // bets config
┃ ┃ ┣ 📂contractConfig       // depends on contract settings
┃ ┃ ┃ ┗ 📜index.ts
┃ ┃ ┣ 📂debug                // debug file that can be used to simulate pending or pending claim bets              
┃ ┃ ┃ ┗ 📜debug.json
┃ ┃ ┣ 📂rouletteConfig       // roulette style customization   
┃ ┃ ┃ ┗ 📜index.ts
┃ ┃ ┣ 📂types
┃ ┃ ┃ ┗ 📜index.ts
┃ ┃ ┗ 📜index.ts             // load
┃ ┣ 📂components
┃ ┃ ┣ 📂ConnectWallet        // Button to connect your wallet
┃ ┃ ┃ ┣ 📜ConnectWallet.jsx
┃ ┃ ┃ ┗ 📜styles.js
┃ ┃ ┣ 📂DashboardLayout      // Main dapp components and layouts
┃ ┃ ┃ ┣ 📜home.jsx
┃ ┃ ┃ ┣ 📜index.jsx
┃ ┃ ┃ ┣ 📜sidebar.jsx
┃ ┃ ┃ ┗ 📜topbar.jsx
┃ ┃ ┣ 📂wallet               // Required libraries for wallet connection, supported chains are set here
┃ ┃ ┃ ┗ 📜connectors.js
┃ ┃ ┗ 📂Wheel                // Wheel components
┃ ┃ ┃ ┣ 📜confeti.tsx
┃ ┃ ┃ ┣ 📜dialogBetResult.jsx
┃ ┃ ┃ ┣ 📜index.tsx
┃ ┃ ┃ ┣ 📜operationsBox.jsx
┃ ┃ ┃ ┣ 📜roulette.jsx
┃ ┃ ┃ ┗ 📜roulettePaid.jsx
┃ ┣ 📂config                 // We load and type .env.local file variables
┃ ┃ ┗ 📜index.ts
┃ ┣ 📂hooks                  // Provides the required methods to connect/disconned your wallet and other data
┃ ┃ ┣ 📜useWeb3.tsx
┃ ┃ ┗ 📜web3.js
┃ ┣ 📂pages                  // Main pages
┃ ┃ ┣ 📜about.js                
┃ ┃ ┣ 📜index.js             // Start page
┃ ┃ ┣ 📜wheel-fortune.js     // Roulette page
┃ ┃ ┣ 📜_app.js
┃ ┃ ┗ 📜_document.js
┃ ┣ 📂services               // This services are used to read data from smart contracts and sign transactions, using typechain types and lib
┃ ┃ ┣ 📜CasinoTreasuryService.ts
┃ ┃ ┣ 📜CommonService.ts
┃ ┃ ┗ 📜RouletteService.ts
┃ ┣ 📂styles                    
┃ ┃ ┗ 📜wheel.js
┃ ┣ 📂ts                     // Ts files
┃ ┃ ┣ 📜const.ts
┃ ┃ ┣ 📜interfaces.ts
┃ ┃ ┗ 📜types.ts
┃ ┗ 📂utils                   
┃ ┃ ┣ 📜device.tsx           // Browser/mobile detection
┃ ┃ ┣ 📜fonts.css
┃ ┃ ┣ 📜SnackbarElement.js   // Snackbar used when we receive and error from a smart contract when we try read data or sign transactions
┃ ┃ ┗ 📜theme.js
┣📜.env.local                // Public environment vars where smart contract addresses default rpc and chain id are set
┣📜.eslintrc.json            // Linter config file
┣📜.gitignore
┣📜next.config.js            // Next config file
┣📜package.json
┣📜postcss.config.js         
┣📜tailwind.config.js        // Tailwind config file, you can define a prefix and specify files where you want use tailwind, custom styles...
┣📜tsconfig.json             // Typescript config file, include/exclude modules and files
```
