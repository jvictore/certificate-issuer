# Certificate Issuer

## Project concept
Currently, the University's credit validation process is very bureaucratic. We have a huge dependence on papers and documents that we often lose throughout the course, as well as a dependence on the course secretariat to validate the credits of all students.

This project aims to use smart contracts from the Ethereum distributed network to validate University certificates. This way we can guarantee that the certificate was issued by a specific entity, and also guarantee that the documents will not be lost, as they will be distributed on the network forever.

Currently, the project is working for a single entity (Hackoonspace), but the objective is to improve it so it can be used by any entity.

## Prerequisites and resources used
The project and dependencies are divided into two parts, backend and frontend respectively. For the back-end we use Solidity to create the contract and Javascript and NodeJs (v16.19.1) for the test and deploy script. Regarding dependencies, it is only necessary to install the `hardhat` library, which is responsible for allowing the creation of a local blockchain.

For the front-end we use React and some common libraries to help create the interface that can be installed using the `npm install` command.

Finally, you will need to have Metamask installed in your browser to be able to test the application.

## Installation
First, make sure you have `Javascript` and `Node` installed on your machine. The node version used in the project is `v16.19.1`.

_NOTE: the steps to follow are to execute the contract on a local network, but the aim is to make it official on the official Ethereum network._

1 - **Install the dependencies**: ensure you are inside the root folder `/certificate-issuer`, then install the dependencies of the back-end and front-end modules;

``` bash
cd front-end
npm install

cd ../back-end
npm install
```


2- **Check if the project is working correctly**: to ensure that everything is working normally, within the `/back-end` path, run the following command to compile the contract and perform a connection test with the local Blockchain.

``` bash
npx hardhat run scripts/run.js
```

After running the command, a prompt similar to this one should appear, although there may be differences in the printed addresses.

```
Inicializando contrato.
Dono do contrato: 0xf39fd6e51aad88f6f4ce6ab8827279cfffb92266
Contract deployed to: 0x5FbDB2315678afecb367f032d93F642f64180aa3
Contract deployed by: 0xf39Fd6e51aad88F6F4ce6aB8827279cffFb92266
[
  [
    BigNumber { value: "760921" },
    BigNumber { value: "60" },
    'Projeto BlockChain 1.0',
    'https://drive.google.com/file/d/1FBYXtkKDeTElFe5sYTc7mJDKLEXq8jTP/view?usp=share_link',
    BigNumber { value: "1680270798" },
    RA: BigNumber { value: "760921" },
    hoursDone: BigNumber { value: "60" },
    name: 'Projeto BlockChain 1.0',
    link: 'https://drive.google.com/file/d/1FBYXtkKDeTElFe5sYTc7mJDKLEXq8jTP/view?usp=share_link',
    issueDate: BigNumber { value: "1680270798" }
  ],
  ...
]
```

## Execution

To run the application locally go to the `/back-end` folder and follow the steps below:

1- **Upload a local Ethereum network**: the command below will upload the network and print a list of wallets created by Hardhat, so that we can test our contract, and will keep a local network running until the terminal is finished.

``` bash
npx hardhat node
```

2- **Deploy the contract**: in another terminal, continuing with the path `/back-end`, execute the command below to deploy the contract on the local network.

``` bash
npx hardhat run scripts/deploy.js --network localhost
```

3- **Make the connection between Metamask and the local Blockchain and add wallet #0 from the test Blockchain to Metamask**: this can be done by following this tutorial [following this tutorial](https://medium.com/@kaishinaw/connecting-metamask-with-a-local-hardhat-network-7d8cea604dc6).

_NOTE: when recreating the local Blockchain after performing some operations you will need to reset the Metamask, to do this follow the steps below._

* _Within Metamask, click on your photo;_
* _Go to Settings;_
* _Go to Advanced;_
* _Click on Reset Account._

4- **Upload front-end server**: this command will upload the application that communicates with the local Ethereum network at `http://localhost:5173/`.

```bash
cd ../front-end
npm run dev
```

### How to use

The application interface is very simple, having only two main tabs, Search and Issuance. When opening the application you will see a screen very similar to this:

![Home Screen Locked](./docs/img/nao-conectado.png)

To connect the wallet and be able to issue or search for certificates, click the "Connect Wallet" button and confirm the operation in Metamask. After that, you can issue or search for certificates at will, simply filling in the fields on each tab.

<div style="text-align:center">
  <div><strong>Certificate Issuance</strong></div>
  <img src="docs/img/tela-de-emissao.png" />
</div>

<div style="text-align:center">
  <div><strong>Certificate Search</strong></div>
  <img src="docs/img/tela-de-busca.png" />
</div>




## Known bugs/issues
To date, the project has some limitations, such as issuing the certificate, which can only be done by the contract owner. In the future we will add functionality to register other entities with this permission.


## Authors

| Author Name | LinkedIn | GitHub |
| ------------- | -------- | ------ |
| Alex Sandro Momi Junior| [Alex Junior](https://www.linkedin.com/in/alexmomijunior/) | [AlexJunior01](https://github.com/AlexJunior01)
| João Victor Elias Costa  | [João Elias](https://www.linkedin.com/in/jvictore/) | [jvictore](https://github.com/jvictore)
