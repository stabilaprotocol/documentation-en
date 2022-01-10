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

### If one of the top 21 Governors goes wrong, will it be removed from the Governors' node list?

If people stop voting for it, it will drop out of the top 21 GOVs.

### Is there a threshold to become a GOV?

When the amount of votes you get ranks into top 21, you will become a GOV.

### 21 GOVs shares the block producing reward equally or by their computing power?

It has nothing to do with computing power. The reward is a fixed 0.23 STB for each block produced.

### Will there be an over 50% computing power issue in STABILA network?

No.

### Will voting burns STB?

No.

### How long does GOV's power last?

Every 6 hours, the votes will be counted to check the qualifications of all the GOVs.

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
Note: The addresses of Stabila, Unit, Moneta and Blackhole can not be deleted, but can be modified.

### How can I specify the data storage path when start a node?

You can add the data storage path when you start the node, like:

```text
java -jar FullNode.jar -c config.conf -d /data/output
```

## Compile and Build

### java-stabila build failed with unit test issue

Please use './gradlew build -x test' to skip the test cases.

## Deployment

### How to test if the deployment works normally, if there is a test api or command like redis: get ping return pong?

Java-stabila does not provide a default api to test. Once the service start, grpc commands can be sent. Based on that, there are several ways to test if the deployment is successful. You can also use the following command to test:

```text
> tail -f logs/stabila.log | grep "MyheadBlockNumber"
```

### How to know whether my test Governor is running or not?

Using the following command

```text
> tail -f logs/stabila.log | grep "Try Produce Block"
```

## Running a Node

### Which service port should be public to public network?

Default port 18888, 50051

### At the worst scenario, if the Governor can not be connected, the maximum time it allows the Governor to recover its service？

The internet connection recovery time only depends on the recovery of Governor itself, has nothing to do with internet situation.

### Does a node have wallet function?

No, but the node provides wallet rpc api.

### Why does the block process time take so long?

Java-stabila need more RAM to process transactions.

## Smart Contract


## RPC Client and API

### How to sync wallet-cli with wallet on Stabilascan?

By using wallet-cli api 'ImportWallet'.

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
