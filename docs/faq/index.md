# The STABILA FAQ

<!-- markdownlint-disable MD026 -->

[TOC]

## Network Design and Protocol

### How can I generate an account?

You can use [wallet-cli](https://github.com/stabilaprotocol/wallet-cli) or [Stabilascan](https://stabilascan.org/signup).

### What is the network flow?

Network flow depends on transaction volume. As a reference, the average size of a transaction currently is 200 bytes.

### After you create a token, how to change its status from 'not started yet' to 'participate'?

You need to wait till the time reaches the start time of participation you set when create a token. After a token is created, only the token url and description can be modified.

### Is there a place to see if all the Governors are producing blocks?

Please refer to [Stabilascan](https://stabilascan.org/representatives)

### Is the block producing time interval always remain the same?

The current block producing time interval is 3 seconds. In the future, it may be improved to 1 second.

### Will the block producing reward reduce half?

No.

### If one of the top 21 Governors goes wrong, will it be removed from the SRs list?

If people stop voting for it, it will drop out of the top 21 SRs.

### Is there a threshold to become a SR?

When the amount of votes you get ranks into top 21, you will become a SR.

### 21 SRs shares the block producing reward equally or by their computing power?

It has nothing to do with computing power. The reward is a fixed 32 STB for each block produced.

### Will there be an over 50% computing power issue in STABILA network?

No.

### Will voting burns STB?

No.

### How long does SR's power last?

Every 6 hours, the votes will be counted to check the qualifications of all the SRs.

### What is the proof of a transaction？

Transaction hash.

### Why I Can't stake STB longer than 3 days

Staked duration must be 3 days now. It means you can not unstake until the 3 days duration expires. If you don't unstake after 3 days, the staked STB will remain in staked status until you unstake it.

### How to calculate the transaction fee?

please refer to [https://stabilaprotocol.github.io/documentation-en/mechanism-algorithm/resource/](https://stabilaprotocol.github.io/documentation-en/mechanism-algorithm/resource/)

### How to calculate the number of bytes of transactions?

tx-size  = grpcClient.getTransactionById(txId).get().getSerializedSize() + 60

### How to reset my vote?

You need to vote again, set your votes number to 0.

## Node Configuration

### If I replace the field value of 'genesis.block.executives' with the address generated in [Stabilascan](https://stabilascan.org/) in config.conf, do I need to delete other addresses? Do I need to delete the field 'url' and 'voteCount'?

No need to delete other addresses, these addresses will be a part of your net, but if you do not own the private keys of these addresses, they will act like abandoned addresses.
Note: The addresses of Zion、Unit and Blackhole can not be deleted, but can be modified.

### How can I specify the data storage path when start a node?

You can add the data storage path when you start the node, like:

```text
java -jar FullNode.jar -c config.conf -d /data/output
```

### How can I get asset from private net?

In private network, you can set the initial account balance in config file. Please refer to below settings:

```text
genesis.block = {
  # Reserve balance
  assets = [
    {
      accountName = "TestA"
      accountType = "AssetIssue"
      address = "THRR7uvFbRLfNzpKPXEyQa8KCJqi59V59e"
      balance = "1000000000000000"
    },
    {
      accountName = "TestB"
      accountType = "AssetIssue"
      address = "TBLZaw93rsnLJ1SWTvoPkr7GVg5ixn2Jv1"
      balance = "1000000000000000"
    },
    {
      accountName = "TestC"
      accountType = "AssetIssue"
      address = "TJg8yZ4Co8RXsHmTWissmSL1VpL7dCybY1"
      balance = "1000000000000000"
    }
  ]
```

## Compile and Build

### java-stabila build failed with unit test issue

Please use './gradlew build -x test' to skip the test cases.

## Deployment

### How to test if the deployment works normally, if there is a test api or command like redis: get ping return pong?

Java-stabila does not provide a default api to test. Once the service start, grpc commands can be sent. Based on that, there are several ways to test if the deployment is successful. You can also use the following command to test:

```text
> tail -f logs/stabila.log |grep "MyheadBlockNumber"
```

### When to deploy private environment, what's the relationship of Governor and FullNode? Should I firstly deploy a Governor, and then deploy a FullNode？

Under private environment, there should be at least one Governor, there is no amount limit for FullNode.

### How to know whether my test Governor is running or not?

Using the following command

```text
> tail -f logs/stabila.log |grep "Try Produce Block"
```

### Can SolidityNode and FullNode be deployed in one machine? Will they share the data?

They can be deployed in one machine. You can specify the data storage path in configuration file `db.directory = "database"，index.directory = "index"`. You can run FullNode.jar and SolidityNode.jar in different paths to separate the data and log. Remember to change the port in `config.conf`, because two nodes can not work using the same port. SolidityNode is deprecated. Now a FullNode supports all RPCs of a SolidityNode. New developers should deploy FullNode only.

## Running a Node

### As under private environment, why the log keeps updating with all other public nodes? What's the difference of private and public environment？

If it is related to ip list: You need to update 'seed.ip' in config.conf, if it is the same as your public ip, and your computer is connected to the internet, it will try to connect other nodes, even if it fails to connect, the ip list will be stored into DB. If it is related to block and transaction: Under private environment, you need to modify the p2p version and parent hash.

### Under private environment, should I submit application information to STABILA to become a SR?

Under private environment, no need to submit application information to STABILA to become a SR.

Ask：Which service port should be public to public network?

Default port 18888, 50051

### At the worst scenario, if the Governor can not be connected, the maximum time it allows the Governor to recover its service？

The internet connection recovery time only depends on the recovery of Governor itself, has nothing to do with internet situation.

### Does SolidityNode sync data from FullNode?

Yes.

### Does a node have wallet function?

No, but the node provides wallet rpc api.

### Why does the block process time take so long?

Java-stabila need more RAM to process transactions.

## Smart Contract


## RPC Client and API

### How to sync wallet-cli with wallet on Stabilascan?

By using wallet-cli api 'ImportWallet'.

### Is gateway connected to SolidityNode？

Gateway can connect to SolidityNode and FullNode.

### What is the different between 'getTransactionById' and 'getTransactionInfoById'?

The data they return is from different data modules. 'getTransactionById' focuses on general transaction data, while 'getTransactionInfoById' focuses on transaction fee data.

### How to broadcast raw transaction？

You can use 'wallet/broadcasthex'.

### How to get token balance of an account?

You can use the following wallet-cli api:

```text
triggercontract contractaddress balanceOf(address) "youraddress" false 0 0 0 #
```

## Error Log

### What does the following error message mean?

```text
17:02:42.699 INFO [o.t.c.s.ExecutiveService] Try Produce Block
17:02:42.699 INFO [o.t.c.s.ExecutiveService] Not sync
```

This message means your node does not sync with the network. Before producing blocks, it needs to sync data. You can use the following command to check the block height.

```text
> tail -f logs/stabila.log |grep "MyheadBlockNumber"
```

## Other Questions

## My Question is Not Listed Here?

Feel free to join our community, just open an Issue on github:

- Github: [stabilaprotocol/java-stabila](https://github.com/stabilaprotocol/java-stabila)
