# Smart contract watcher chainstack

 This simple project uses the Ethers.js library to examine blocks using the `eth_getBlockReceipts` method and extract data about newly deployed smart contracts.

> Read the full article on the [Chainstack](https://chainstack.com) blog:
 * [Uncovering the Power of eth_getBlockReceipts]()

 ## Project details

This program uses the `ethers.js` library to retrieve all of the transaction receipts in a block at once using the `eth_getBlockReceipts` method; it then looks for transactions that deployed a new smart contract by inspecting the `contractAddress` field of each transaction receipt.

This project is compatible with EVM-based chains and queryng a node running the Erigon client.

Project's structure:

```sh
    ├── Root directory
		├── index.js
                │   
		│── src
		│   ├── analyzer.js
		│ 	├── latestBlock.js
		│ 	├── parser.js
		│ 	├── ToHex.js
		│  
		├──.env
```

## Quickstart

### Prerequisites

The system requires at least:

* Node.js v16.17.0— [install node](https://nodejs.org/en/download/)

### Deploy an Erigon node with Chainstack

> To use this app, you need access to a node running the Erigon client.

Chainstack supports the Erigon client on **Ethereum,** **Polygon, and BNB smart chain** [archive nodes](https://chainstack.com/evm-nodes-a-dive-into-the-full-vs-archive-mode/). This option is available on the [Business subscription plan](https://chainstack.com/pricing/) and higher on elastic nodes or starting from the [Growth subscription plan](https://chainstack.com/pricing/) for dedicated nodes.

Follow the steps to deploy an archive node running Erigon on elastic nodes:

1. [Sign up with Chainstack](https://console.chainstack.com/user/account/create)
2. [Create a project](https://docs.chainstack.com/platform/create-a-project)

After you created a project:

1. Select the project with the network.
2. Select the network.
3. Click **Add node**.
4. Provide a node name.
5. Under **Type**, select **Elastic**.
6. Under **Mode**, select **Archive**. With an archive node, you can query historical states for the entire chain.
7. Under **Debug and trace APIs**, select **On**.
8. Under **Hosting**, select **Chainstack**.
9. For Chainstack hosting, select a cloud provider and a region.
10. Review your changes and click **Add node**.

### Clone this project

```sh
git clone https://github.com/soos3d/smart-contract-watcher-chainstack.git
```

### Install Dependencies

List of dependencies:

* `dotenv`: `^16.0.3`
* `ethers`: `^5.7.2`

From the root directory of the project run:

```sh
npm ci
```

> Use `npm ci` to launch a `clean install` of the dependencies, this will install the same version as in the `package.json` file.

### Edit .env.sample

Edit the `.env.sample` file, paste the node endpoint that you wish to test, and rename it to `.env`.

```sh
ERIGON_RPC="YOUR_ERIGON_NODE_URL"
```

### Start

To start the program run the following:

```sh
npm run start
```

This will run the app giving you the following results in the console if new smart contracts are detected.

```sh
> smart-contract-watcher-chainstack@1.0.0 watch
> node index.js

New smart contract detected! 

New smart contract address: 0x00e9a503b88732ee3e28a0fec3343c405f5e963d
Deployed by address: 0x984380fc12cc3bdb894e1f35111dd992fb52a231
Deployed by transaction: 0xad8d3a6647a4ad7e2f8eedef258b4c3233d54e5999a855ca59500f5df70d35de
```