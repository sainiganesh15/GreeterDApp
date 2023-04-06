# Greeter DApp

This project contains a decentralized application (DApp) that interacts with a smart contract deployed on the Ethereum blockchain. The DApp allows users to view and change the greeting message stored in the smart contract.

## Prerequisites

Before running the DApp, make sure you have the following installed on your system:

- Node.js
- npm or yarn
- Ganache or any other local Ethereum development blockchain
- Metamask browser extension

## Installation

1. Install `create-react-app` and `hardhat` by running the following command in your terminal:
``` 
npm install -g create-react-app
npm install hardhat
```
2. Create a new React app and initialize Hardhat with the basic sample project by running:
``` 
npx create-react-app my-app
cd my-app
npx hardhat
```
3. For running hardhat sample project install these dependencies:
```
npm install --save-dev @nomiclabs/hardhat-ethers@^2.0.5 @nomiclabs/hardhat-waffle@^2.0.3 
npm install --save-dev chai@^4.3.6 ethereum-waffle@^3.4.4 ethers@^5.6.2 hardhat@^2.9.2
```
This will create a new React app in a folder named my-app and initialize a new Hardhat project with the basic sample project.

## Deploying Smart Contract to Localhost

1. Write your smart contract in Solidity and save it in the `contracts/` folder.

2. In the `hardhat.config.js` file, configure your local development network by adding the following:

```
require("@nomiclabs/hardhat-waffle")


module.exports = {
    solidity: "0.8.9",
    networks: {
      hardhat: {
        chainId: 1337,
      },
    },
    paths: {
      artifacts: "./src/artifacts",
    },
  };
  ```

  3. In the `scripts/` folder, create a new script to deploy your contract to the local network:
  ```
  const { ethers } = require("hardhat");

async function main() {
  const Greeter = await ethers.getContractFactory("Greeter");
  const greeter = await Greeter.deploy("Hello, Hardhat!");

  console.log("Greeter deployed to:", greeter.address);
}

main()
  .then(() => process.exit(0))
  .catch(error => {
    console.error(error);
    process.exit(1);
  });
```
4. Compile and deploy the smart contract using Hardhat

```
npx hardhat compile
npx hardhat run scripts/deploy.js --network localhost

``` 

This will deploy your smart contract to the local development network.

5. Start the DApp server
`npm start
`

6. Open your web browser and navigate to http://localhost:3000.

## Usage

- On the home page of the DApp, you can view the current greeting message stored in the smart contract.
- To change the greeting, enter a new message in the input field and click the "Change" button.
- The greeting message will be updated in the smart contract and the page will be refreshed to display the new message.

## License

This project is licensed under the MIT License