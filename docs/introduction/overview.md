# Overview

# 1. Project Repository

Github Url: [https://github.com/stabilaprotocol](https://github.com/stabilaprotocol)  1

[java-stabila](https://github.com/stabilaprotocol/java-stabila) is the source code of the MainNet.

[protocol](https://github.com/stabilaprotocol/protocol) is the definition of the api and data structure.

[wallet-cli](https://github.com/stabilaprotocol/wallet-cli) is the official command line wallet.


MainNet Configuration:
[https://github.com/stabilaprotocol/StabilaDeployment/blob/master/main_net_config.conf](https://github.com/stabilaprotocol/stabila-deployment/blob/master/main_net_config.conf)
# 2. GOVs and Committee

## 2.1 How to Become a Governor

 In STABILA network, any account can apply to become a governor candidate. Every account can vote for executives. The top 21 candidates with the most votes are Governors. Governors can produce blocks. The votes will be counted every 6 hours, so governors may also change every 6 hours.

 To prevent vicious attack, STABILA network burns 9999 STB from the account that applies to become a governor candidate.

## 2.2 Governors Election

 To vote, you need to have STABILA Power(SP). To get STABILA Power, you need to stake STB. Every 1 staked STB accounts for one STABILA Power(SP). Every account in STABILA network has the right to vote for a governor candidate. After you unstake your staked STB, you will lose the responding STABILA Power(SP), so your previous vote will be invalid.

 Note: Only your latest vote will be counted in STABILA network which means your previous vote will be over written by your latest vote.

Example (Using wallet-cli):

```text
cdbalance 10,000,000 3 // stake 10 STB to get 10 STABILA Power(SP)
voteexecutive executive1 4 executive2 6 // Vote 4 votes for executive1, 6 votes for executive2
voteexecutive executive1 3 executive2 7 // Vote 3 votes for executive1, 7 votes for executive2
```

The final output above is: Vote 3 votes for executive1, 7 votes for executive2

## 2.3 Reward for Governors

The top 21 Executives (Gs) that are elected every round (6 hours) will divide around 1,596 STB as mined, also known as Governor Reward. The prize will be distributed evenly among the 21 Gs.

Total reward per round = 221,714 Unit/block x 20 block/min x 60 mins/hr x 6 hrs/round .

A total of 2,330,657 STB will be awarded annually to the 21 Gs. It should be noted that every two years the reward for mining Stabila is halved.

## 2.4 Committee

### 2.4.1 What is Committee

Committee can modify the STABILA network parameters, like transaction fees, block producing reward amount, etc. Committee is composed of the current 21 governors. Every governor has the right to start a proposal. The proposal will be passed after it gets more than 15 approves from the governors and will become valid in the next maintenance period.

### 2.4.2 Create a Proposal

Only the account of a governor can create a proposal.
The network parameters can be modified([min,max]):

- 0: MAINTENANCE_TIME_INTERVAL, 21600000 ms //governor votes count time interval
- 1: ACCOUNT_UPGRADE_COST, 1000000000 UNIT //the fee to apply to become a governor candidate
- 2: CREATE_ACCOUNT_FEE, 1385 UNIT //the fee to create an account
- 3: TRANSACTION_FEE, 40 UNIT/byte //the fee for bandwidth
- 4: ASSET_ISSUE_FEE, 1000000000 UNIT //the fee to issue an asset
- 5: EXECUTIVE_PAY_PER_BLOCK, 221714 UNIT //the block producing reward
- 6: EXECUTIVE_STANDBY_ALLOWANCE, 0
- 7: CREATE_NEW_ACCOUNT_FEE_IN_SYSTEM_CONTRACT, 0
- 8: CREATE_NEW_ACCOUNT_BANDWIDTH_RATE, 1
- 9: ALLOW_CREATION_OF_CONTRACTS, 0 //to enable the VM
- 10: REMOVE_THE_POWER_OF_THE_GR, 0 //to clear the votes of GR
- 11: UCR_FEE, 40 //UNIT
- 12: EXCHANGE_CREATE_FEE, 14000000 //UNIT
- 13: MAX_CPU_TIME_OF_ONE_TX, 80 //ms
- 14: ALLOW_UPDATE_ACCOUNT_NAME, 0 //to allow users to change account name and allow account duplicate name, 0 means false
- 15: ALLOW_SAME_TOKEN_NAME, 0 //to allow create a token with duplicate name, 0 means false
- 16: ALLOW_DELEGATE_RESOURCE, 0 //to enable the resource delegation, 0 means false
- 17: TOTAL_UCR_LIMIT, 30000000000 //to modify the ucr limit
- 18: ALLOW_SVM_TRANSFER_SRC10, 0 //to allow smart contract to transfer SRC-10 token, 0 means false
- 19: TOTAL_CURRENT_UCR_LIMIT, 30000000000
- 20: ALLOW_MULTI_SIGN, 0, 0 means false
- 21: ALLOW_ADAPTIVE_UCR, 0, 0 means false
- 22: UPDATE_ACCOUNT_PERMISSION_FEE, 1385000
- 23: MULTI_SIGN_FEE, 13857
- 24: ALLOW_PROTO_FILTER_NUM, 0, 0 means false
- 25: ALLOW_ACCOUNT_STATE_ROOT, 0, 0 means false
- 26: ALLOW_SVM_CONSTANTINOPLE, 0, 0 means false
- 29: ADAPTIVE_RESOURCE_LIMIT_MULTIPLIER, 1000
- 30: ALLOW_CHANGE_DELEGATION, 0, 0 means false
- 31: EXECUTIVE_100_PAY_PER_BLOCK, 10972
- 32: ALLOW_SVM_SOLIDITY_059, 0, 0 means false
- 33: ADAPTIVE_RESOURCE_LIMIT_TARGET_RATIO, 10
- 35: FORBID_TRANSFER_TO_CONTRACT, 0, 0 means false
- 39: ALLOW_SHIELDED_SRC20_TRANSACTION, 0, 0 means false
- 40: ALLOW_PBFT,	0, 0 means false
- 41: ALLOW_SVM_ISTANBUL, 0, 0 means false
- 44: ALLOW_MARKET_TRANSACTION,	0, 0 means false
- 45: MARKET_SELL_FEE,	0
- 46: MARKET_CANCEL_FEE,	0
- 47: MAX_FEE_LIMIT,	15000000
- 48: ALLOW_TRANSACTION_FEE_POOL, 0, 0 means false
- 49: ALLOW_BLACKHOLE_OPTIMIZATION, 0, 0 means false
- 51: ALLOW_NEW_RESOURCE_MODEL, 0, 0 means false
- 52: ALLOW_SVM_CD, 0, 0 means false
- 53: ALLOW_ACCOUNT_ASSET_OPTIMIZATION, 0, 0 means false
- 59: ALLOW_SVM_VOTE, 0, 0 means false
- 61: FREE_NET_LIMIT, 500
- 62: TOTAL_NET_LIMIT, 28800000

Example (Using wallet-cli):
```text
createproposal id value
id: the serial number (0 ~ 18)
value: the parameter value
```

Note: In STABILA network, 1 STB = 1000_000 UNIT

### 2.4.3 Vote for a Proposal

Proposal only support YES vote. Since the creation time of the proposal, the proposal is valid within 3 days. If the proposal does not receive enough YES votes within the period of validity, the proposal will be invalid beyond the period of validity. Yes vote can be cancelled.

Example (Using wallet-cli):
```text
approveProposal id is_or_not_add_approval
id: proposal id
is_or_not_add_approval: YES vote or cancel YES vote
```

### 2.4.4 Cancel Proposal

Proposal creator can cancel the proposal before it is passed.

Example (Using wallet-cli):
```text
deleteProposal id
id: proposal id
```

### 2.4.5 Query Proposal

- Query all the proposals list (ListProposals)
- Query all the proposals list by pagination (GetPaginatedProposalList)
- Query a proposal by proposal id (GetProposalById)

For more api detail, please refer to [Stabila HTTP API](../api/http.md)

# 3. Account Model

## 3.1 Introduction

STABILA uses account model. An account's identity is address, it needs private key signature to operate an account. An account has many attributes, like STB balance, tokens balance, bandwidth, etc. STB and tokens can be transferred from account to account and it costs bandwidth. An account can also issue a smart contract, apply to become a governor candidate, vote, etc. All STABILA's activities are based on account.

## 3.2 How to Create an Account

1.&nbsp;Use a wallet to generate the address and private key. To activate the account, you need to transfer STB or transfer token to the new created account.

2.&nbsp;Use an account already existed in STABILA network to create an account

## 3.3 Key-pair Generation Algorithm
Stabila signature algorithm is ECDSA, curve used is SECP256K1. Private key is a random bumber, public key is a point in the elliptic curve. The process is: first generate a random number d to be the private key, then calculate P = d * G as the public key, G is the elliptic curve base point.

## 3.4 Address Format
Use the public key P as the input, by SHA3 get the result H. The length of the public key is 64 bytes, SHA3 uses Keccak256. Use the last 20 bytes of H, and add a byte of 0x3f in front of it, then the address comes out. Do basecheck to address, here is the final address. All addresses start with 'T'.

basecheck process: first do sha256 calculation to address to get h1, then do sha256 to h1 to get h2, use the first 4 bytes as check to add it to the end of the address to get address||check, do base58 encode to address||check to get the final result.

Character map:
ALPHABET = "123456789ABCDEFGHJKLMNPQRSTUVWXYZabcdefghijkmnopqrstuvwxyz"

## 3.5 Signature
### 3.5.1	Signing Steps for GRPC
1.	Convert the transaction’s raw data to byte[].
2.	Hash the raw data using sha256.  This gives you the Transaction ID.
3.	Sign the results of sha256 with the private key.
4.	Add the signed result to transaction.

### 3.5.2	Signing Steps
1.  Use the transaction ID included in the return data of an http request.
3.	Sign the transaction ID with the private key.
4.	Add the signed result to transaction.


### 3.5.3	Signature algorithm
1.	ECDSA algorithm, SECP256K.

2.	Example of signature data
``` 
    priKey:::8e812436a0e3323166e1f0e8ba79e19e217b2c4a53c970d4cca0cfb1078979df
    pubKey::04a5bb3b28466f578e6e93fbfd5f75cee1ae86033aa4bbea690e3312c087181eb366f9a1d1d6a437a9bf9fc65ec853b9fd60fa322be3997c47144eb20da658b3d1
    hash:::159817a085f113d099d3d93c051410e9bfe043cc5c20e43aa9a083bf73660145
    r:::38b7dac5ee932ac1bf2bc62c05b792cd93c3b4af61dc02dbb4b93dacb758123f
    s:::08bf123eabe77480787d664ca280dc1f20d9205725320658c39c6c143fd5642d
    v:::0

   Note: the signed result should be 65 byte in size—r 32 bytes, s 32 bytes and v 1 byte.
```

3.	Signature verification

When a full node receives the transaction, it will verify the signature, comparing an address calculated with hash, r, s and v with the address of the contract. Signature is successfully verified if the two addresses match.

### 3.5.4	Example of code
```java
    public static Transaction sign(Transaction transaction, ECKey myKey) {
    
        Transaction.Builder transactionBuilderSigned = transaction.toBuilder();  
        byte[] hash = sha256(transaction.getRawData().toByteArray());  
        List<Contract> listContract = transaction.getRawData().getContractList();  
        
            for (int i = 0; i < listContract.size(); i++) {
            
                ECDSASignature signature = myKey.sign(hash);    
                ByteString bsSign = ByteString.copyFrom(signature.toByteArray());    
                //Each contract may be signed with a different private key in the future.
                transactionBuilderSigned.addSignature( bsSign );
                 
                }
```

# 4. Network Node
## 4.1 Governor
### 4.1.1 Governor Introduction
Governor(abbr: GOV) is the block producer in STABILA network, there are 21 GOV. They verify the transactions and write the transactions into the blocks, they take turns to produce blocks. The governors' information is public to everyone in STABILA network. The best way to browse is using [stabilascan](https://stabilascan.org/representatives).
### 4.1.2 Governor Deployment
[Governor Deployment](https://github.com/stabilaprotocol/stabila-deployment)

### 4.1.3 Recommended Hardware Configuration

minimum requirement:
CPU: 16 cores, RAM: 32G, Bandwidth: 100M, Disk: 1T

Recommended requirement:
CPU: > 64 cores RAM: > 64G, Bandwidth: > 500M, Disk: > 20T

## 4.2 FullNode
### 4.2.1 FullNode Introduction
FullNode has the complete block chain data, can update data in real time. It can broadcast the transactions and provide api service.
### 4.2.2 FullNode Deployment
For Docker installation and deployment please refer to [STABILA-Deployment](https://github.com/stabilaprotocol/stabila-deployment)
### 4.2.3 Recommended Hardware Configuration
Minimum requirement:
CPU: 16 cores, RAM: 32G, Bandwidth: 100M, Disk: 1T
Recommended requirement:
CPU: > 64 cores RAM: > 64G, Bandwidth: > 500M, Disk: > 20T

## 4.3 SolidityNode
### 4.3.1 SolidityNode Introduction
SolidityNode only synchronize solidified blocks data from the fullNode it specifies, It also provie api service.
### 4.3.2 SolidityNode Deployment
For Docker installation and deployment please refer to [STABILA-Deployment](https://github.com/stabilaprotocol/stabila-deployment)
### 4.3.3 Recommended Hardware Configuration
Minimum requirement:
CPU: 16 cores, RAM: 32G, Bandwidth: 100M, Disk: 1T
Recommended requirement:
CPU: > 64 cores RAM: > 64G, Bandwidth: > 500M, Disk: > 20T

## 4.4 STABILA Network Instructure
STABILA network uses Peer-to-Peer(P2P) network instructure, all nodes status equal. There are three types of node: Governor, FullNode, SolidityNode. Governor produces blocks, FullNode synchronizes blocks and broadcasts transactions, SolidityNode synchronizes solidified blocks. Any device that deploy the java-stabila code can join STABILA network as a node.
![image](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/network.png)

## 4.5 FullNode and SolidityNode Fast Deployment
Download fast deployment script, run the script according to different types of node.
please refer to [Node Fast Deployment](https://github.com/stabilaprotocol/stabila-deployment#deployment-of-soliditynode-on-the-one-host)

## 4.6 MainNet

### 4.6.1 FullNode Deployment

 1.&nbsp;Download main_net_config.conf

```shell
wget https://github.com/stabilaprotocol/stabila-deployment/blob/master/main_net_config.conf
```

 2.&nbsp;set seed.node ip.list with GOV's ip and port

 3.&nbsp;set p2p.version the same as Governor's p2p.version

 4.&nbsp;set genesis.block the same as genesis.block

 5.&nbsp;set needSyncCheck true

 6.&nbsp;set node.discovery.enable true

 7.&nbsp;run the script


```shell
 nohup java -Xmx6g -XX:+HeapDumpOnOutOfMemoryError -jar FullNode.jar  -c main_net_config.conf

 command lines parameters
 --log-config: specify the log configuration file path, i.e.: --log-config logback.xml
 -c: specify the configuration file path, i.e.: -c config.conf
```

 The usage of the log file:
 You can change the level of the module to control the log output. The default level of each module is INFO, for example: only print the message with the level higher than warn:
 <logger name="net" level="WARN"/>
 The parameters in configuration file that need to modify:
 ip.list:

 ![image](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/ip_list.png)
 p2p.version:

 ![image](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/p2p_version.png)
 genesis.block:

 ![image](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/genesis_block.png)
 needSyncCheck:

 ![image](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/need_sync_check.png)
 node.discovery.enable:

 ![image](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/discovery_enable.png)

## 4.7 DB Engine
### 4.7.1 Rocksdb
**4.7.1.1 Configuration**

 Use rocksdb as the data storage engine, need to set db.engine to "ROCKSDB"
 ![image](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/db_engine.png)
 Note: rocksdb only support db.version=2, do not support db.version=1

 The optimization parameters rocksdb support:
 ![image](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/rocksdb_tuning_parameters.png)

**4.7.1.2 Use rocksdb's data backup function**

 Choose rocksdb to be the data storage engine, you can use it's data backup function while running
 ![image](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/db_backup.png)

 Note: FullNode can use data backup function. In order not to affect Governor's block producing performance, Governor does not support backup service, but Governor's backup service node can use this function.

**4.7.1.3 Convert leveldb data to rocksdb data**

 The data storage structure of leveldb and rocksdb is not compatible, please make sure the node use the same type of data engine all the time. We provide data conversion script which can convert leveldb data to rocksdb data.

 Usage:
```text
 cd to the source code root directory
 ./gradlew build   #build the source code
 java -jar build/libs/DBConvert.jar  #run data conversion command
```
 Note: If the node's data storage directory is self-defined, before run DBConvert.jar, you need to add the following parameters:

 **src_db_path**: specify LevelDB source directory, default output-directory/database
 **dst_db_path**: specify RocksDb source directory, default output-directory-dst/database

Example, if you run the script like this:
```text
 nohup java -jar FullNode.jar -d your_database_dir &
```
Then, you should run DBConvert.jar this way:
```text
 java -jar build/libs/DBConvert.jar  your_database_dir/database  output-directory-dst/database
```
 Note: You have to stop the running of the node, and then to run the data conversion script.

 If you do not want to stop the running of the node for too long, after node is shut down, you can copy leveldb's output-directory to the new directory, and then restart the node. Run DBConvert.jar in the previous directory of the new directory, and specify the parameters: `src_db_path` and `dst_db_path`.

Example:
```text
 cp -rf output-directory /tmp/output-directory
 cd /tmp
 java -jar DBConvert.jar output-directory/database  output-directory-dst/database
```
 All the whole data conversion process may take 10 hours.

**4.7.1.4 rocksdb vs leveldb**

# 5. Smart Contract
## 5.1 STABILA Smart Contract Introduction

Smart contract is a computerized transaction protocol that automatically implements its terms. Smart contract is the same as common contract, they all define the terms and rules related to the participants. Once the contract is started, it can run in the way it is designed.

STABILA smart contract support Solidity language in (Ethereum). Currently recommend Solidity language version is 0.4.24 ~ 0.4.25. Write a smart contract, then build the smart contract and deploy it to STABILA network. When the smart contract is triggered, the corresponding function will be executed automatically.

## 5.2 STABILA Smart Contract Features
STABILA virtual machine is based on Ethereum solidity language, it also has STABILA's own features.

### 5.2.1 Smart Contract
STABILA VM is compatible with Ethereum's smart contract, using protobuf to define the content of the contract:
```
message SmartContract {
  message ABI {
    message Entry {
      enum EntryType {
        UnknownEntryType = 0;
        Constructor = 1;
        Function = 2;
        Event = 3;
        Fallback = 4;
      }
      message Param {
        bool indexed = 1;
        string name = 2;
        string type = 3;
        // SolidityType type = 3;
      }
      enum StateMutabilityType {
        UnknownMutabilityType = 0;
        Pure = 1;
        View = 2;
        Nonpayable = 3;
        Payable = 4;
      }

      bool anonymous = 1;
      bool constant = 2;
      string name = 3;
      repeated Param inputs = 4;
      repeated Param outputs = 5;
      EntryType type = 6;
      bool payable = 7;
      StateMutabilityType stateMutability = 8;
    }
    repeated Entry entrys = 1;
  }
  bytes origin_address = 1;
  bytes contract_address = 2;
  ABI abi = 3;
  bytes bytecode = 4;
  int64 call_value = 5;
  int64 consume_user_resource_percent = 6;
  string name = 7；
  int64 origin_ucr_limit = 8;
}
```
origin_address: smart contract creator address

contract_address: smart contract address

abi: the api information of the all the function of the smart contract
bytecode: smart contract byte code

call_value: STB transferred into smart contract while call the contract
consume_user_resource_percent: resource consumption percentage set by the developer

name: smart contract name

origin_ucr_limit: ucr consumption of the developer limit in one call, must greater than 0. For the old contracts, if this parameter is not set, it will be set 0, developer can use
 updateUcrLimit api to update this parameter (must greater than 0)

Through other two grpc message types CreateSmartContract and TriggerSmartContract to create and use smart contracts.

### 5.2.2 The Usage of the Function of Smart Contract

1.&nbsp;constant function and inconstant function

There are two types of function according to whether any change will be made to the properties on the chain: constant function and inconstant function
Constant function uses view/pure/constant to decorate, will return the result on the node it is called and not be broadcasted in the form of a transaction
Inconstant function will be broadcasted in the form of a transaction while being called, the function will change the data on the chain, such as transfer, changing the value of the internal variables of contracts, etc.

Note: If you use create command inside a contract (CREATE instruction), even use view/pure/constant to decorate the dynamically created contract function, this function will still be treated as inconstant function, be dealt in the form of transaction.

2.&nbsp;message calls

Message calls can call the functions of other contracts, also can transfer STB to the accounts of contract and none-contract. Like the common STABILA triggercontract, Message calls have initiator, recipient, data, transfer amount, fees and return attributes. Every message call can generate a new one recursively. Contract can define the distribution of the remaining ucr in the internal message call. If it comes with OutOfUcrException in the internal message call, it will return false, but not error. In the meanwhile, only the gas sent with the internal message call will be consumed, if ucr is not specified in call.value(ucr), all the remaining ucr will be used.

3.&nbsp;delegate call/call code/libary

There is a special type of message call, delegate call. The difference with common message call is the code of the target address will be run in the context of the contract that initiates the call, msg.sender and msg.value remain unchanged. This means a contract can dynamically load code from another address while running. Storage, current address and balance all point to the contract that initiates the call, only the code is get from the address being called. This gives Solidity the ability to achieve the 'lib' function: the reusable code lib can be put in the storage of a contract to implement complex data structure library.

4.&nbsp;CREATE command

This command will create a new contract with a new address. The only difference with Ethereum is the newly generated STABILA address used the smart contract creation transaction id and the hash of nonce called combined. Different from Ethereum, the definition of nonce is the comtract sequence number of the creation of the root call. Even there are many CREATE commands calls, contract number in sequence from 1. Refer to the source code for more detail.
Note: Different from creating a contract by grpc's deploycontract, contract created by CREATE command does not store contract abi.

5.&nbsp;built-in function and built-in function attribute (Since Odyssey-v3.1.1, SVM built-in function is not supported temporarily)

1)SVM is compatible with solidity language's transfer format, including:
- accompany with constructor to call transfer
- accompany with internal function to call transfer
- use transfer/send/call/callcode/delegatecall to call transfer

Note: STABILA's smart contract is different from STABILA's system contract, if the transfer to address does not exist it can not create an account by smart contract transfer.

2)Different accounts vote for Governor (Since Odyssey-v3.1.1, SVM built-in function is not supported temporarily)
3)Governor gets all the reward (Since Odyssey-v3.1.1, SVM built-in function is not supported temporarily)
4)Governor approves or disapproves the proposal (Since Odyssey-v3.1.1, SVM built-in function is not supported temporarily)
5)Governor proposes a proposal (Since Odyssey-v3.1.1, SVM built-in function is not supported temporarily)
6)Governor deletes  a proposal (Since Odyssey-v3.1.1, SVM built-in function is not supported temporarily)
7)STABILA byte address converts to solidity address (Since Odyssey-v3.1.1, SVM built-in function is not supported temporarily)
8)STABILA string address converts to solidity address (Since Odyssey-v3.1.1, SVM built-in function is not supported temporarily)
9)Send token to target address (Since Odyssey-v3.1.1, SVM built-in function is not supported temporarily)
10)Query token amount of target address (Since Odyssey-v3.1.1, SVM built-in function is not supported temporarily)
11)Compatible with all the built-in functions of Ethereum

Note: Ethereum's RIPEMD160 function is not recommended, because the return of STABILA is a hash result based on STABILA's sha256, not an accurate Ethereum RIPEMD160.

### 5.2.3 Contract Address Using in Solidity Language

Ethereum VM address is 20 bytes, but STABILA's VM address is 21 bytes.

1.&nbsp;address conversion

Need to convert STABILA's address while using in solidity (recommended):
```text
/**
     *  @dev    convert uint256 (HexString add 0x at beginning) stabila address to solidity address type
     *  @param  stabilaAddress uint256 stabilaAddress, begin with 0x, followed by HexString
     *  @return Solidity address type
*/

function convertFromStabilaInt(uint256 stabilaAddress) public view returns(address){
        return address(stabilaAddress);
}
```
This is similar with the grammar of the conversion from other types converted to address type in Ethereum.

2.&nbsp;address judgement

Solidity has address constant judgement, if using 21 bytes address the compiler will throw out an error, so you should use 20 bytes address, like:
```text
function compareAddress(address stabilaAddress) public view returns (uint256){
        // if (stabilaAddress == 0x3fca35b7d915458ef540ade6068dfe2f44e8fa733c) { // compile error
        if (stabilaAddress == 0xca35b7d915458ef540ade6068dfe2f44e8fa733c) { // right
            return 1;
        } else {
            return 0;
        }
}
```
But if you are using wallet-cli, you can use 21 bytes address, like 0000000000000000000041ca35b7d915458ef540ade6068dfe2f44e8fa733c

3.&nbsp;variable assignment

Solidity has address constant assignment, if using 21 bytes address the compiler will throw out an error, so you should use 20 bytes address, like:
```text
function assignAddress() public view {
        // address newAddress = 0x3fca35b7d915458ef540ade6068dfe2f44e8fa733c; // compile error
        address newAddress = 0xca35b7d915458ef540ade6068dfe2f44e8fa733c;
        // do something
}
```
If you want to use STABILA address of string type (SLLM21wteSPs4hKjbxgmH1L6poyMjeTbHm) please refer to (2-4-7,2-4-8).

## 5.3 Ucr Introduction
Each command of smart contract consume system resource while running, we use 'Ucr' as the unit of the consumption of the resource.

### 5.3.1 How to Get Ucr

Stake STB to get ucr.

Example (Using wallet-cli):

```text
cdBalance cded_balance cded_duration [ResourceCode:0 BANDWIDTH,1 UCR]
```

Stake STB to get ucr, ucr obtained = user's STB staked amount / total amount of staked STB in STABILA * 50_000_000_000.

Example:

```text
If there are only two users, A stakes 2 STB, B stakes 2 STB
the ucr they can get is:
A: 25_000_000_000 and ucr_limit is 25_000_000_000
B: 25_000_000_000 and ucr_limit is 25_000_000_000

when C stakes 1 STB:
the ucr they can get is:
A: 20_000_000_000 and ucr_limit is 20_000_000_000
B: 20_000_000_000 and ucr_limit is 20_000_000_000
B: 10_000_000_000 and ucr_limit is 10_000_000_000
```

** Ucr Recovery **

The ucr consumed will reduce to 0 smoothly within 24 hours.

Example:

```text
at one moment, A has used 72_000_000 Ucr
if there is no continuous consumption or STB stake
one hour later, the ucr consumption amount will be 72_000_000 - (72_000_000 * (60*60/60*60*24)) Ucr = 69_000_000 Ucr
24 hours later, the ucr consumption amount will be 0 Ucr
```

### 5.3.2 How to Set Fee Limit (Caller Must Read)
***

*Within the scope of this section, the smart contract developer will be called "developer", the users or other contracts which call the smart contract will be called "caller"*

*The amount of ucr consumed while call the contract can be converted to STB or UNIT, so within the scope of this section, when refer to the consumption of the resource, there's no strict difference between Ucr, STB and UNIT, unless they are used as a number unit.*

***

Set a rational fee limit can guarantee the smart contract execution. And if the execution of the contract cost great ucr, it will not consume too much ucr from the caller. Before you set fee limit, you need to know several conception:

1.&nbsp;The legal fee limit is a integer between 0 - 10^9, unit is UNIT.

2.&nbsp;Different smart contracts consume different amount of ucr due to their complexity. The same trigger in the same contract almost consumes the same amount fo ucr[1]. When the contract is triggered, the commands will be executed one by one and consume ucr. If it reaches the fee limit, commands will fail to be executed, and ucr is not refundable.

3.&nbsp;Currently fee limit only refers to the ucr converted to UNIT that will be consumed from the caller[2]. The ucr consumed by triggering contract also includes developer's share.

4.&nbsp;For a vicious contract, if it encounters execution timeout or bug crash, all it's ucr will be consumed.

5.&nbsp;Developer may undertake a proportion of ucr consumption(like 90%). But if the developer's ucr is not enough for consumption, the rest of the ucr consumption will be undertaken by caller completely. Within the fee limit range, if the caller does not have enough ucr, then it will burn equivalent amount of STB [2].

To encourage caller to trigger the contract, usually developer has enough ucr.

** Example **

How to estimate the fee limit:

Assume contract C's last execution consumes 18000 Ucr, so estimate the ucr consumption limit to be 20000 Ucr[3]

According to the staked STB amount and ucr conversion, assume 1 STB = 400 ucr.

When to burn STB, 1 STB = 10000 ucr[4]

Assume developer undertake 90% ucr consumption, and developer has enough ucr.

Then the way to estimate the fee limit is:
```
1). A = 20000 ucr * (1 STB / 400 ucr) = 50 STB = 50_000_000 UNIT,

2). B = 20000 ucr * (1 STB / 10000 ucr) = 2 STB = 2_000_000 UNIT,

3). Take the greater number of A and B, which is 50_000_000 UNIT,

4). Developer undertakes 90% ucr consumption, caller undertakes 10% ucr consumption,
```

So, the caller is suggested to set fee limit to 50_000_000 UNIT * 10% = 5_000_000 UNIT

Note:
```
[1] The ucr consumption of each execution may fluctuate slightly due to the situation of all the nodes.
[2] STABILA may change this policy.
[3] The estimated ucr consumption limit for the next execution should be greater than the last one.
[4] 1 STB = 10^4 ucr is a fixed number for burning STB to get ucr, STABILA may change it in future.
```

### 5.3.3 Ucr Calculation (Developer Must Read)

1.&nbsp;In order to punish the vicious developer, for the abnormal contract, if the execution times out (more than 50ms) or quits due to bug (revert not included), the maximum available ucr will be deducted. If the contract runs normally or revert, only the ucr needed for the execution of the commands will be deducted.

2.&nbsp;Developer can set the proportion of the ucr consumption it undertakes during the execution, this proportion cna be changed later. If the developer's ucr is not enough, it will consume the caller's ucr.

3.&nbsp;Currently, the total ucr available when trigger a contract is composed of caller fee limit and developer's share

Note:
- If the developer is not sure about whether the contract is normal, do not set caller's ucr consumption proportion to 0%, in case all developer's ucr will be deducted due to vicious execution[1].
- We recommend to set caller's ucr consumption proportion to 10% ~ 100%[2].

**Example 1**

A has an account with a balance of 90 STB(90000000 UNIT) and 10 STB staked for 100000 ucr.

Smart contract C set the caller ucr consumption proportion to 100% which means the caller will pay for the ucr consumption completely.

A triggers C, the fee limit set is 30000000 (unit UNIT, 30 STB)

So during this trigger the ucr A can use is from two parts:
- A's ucr by staking STB;
- The ucr converted from the amount of STB burning according to a fixed rate;

If fee limit is greater than the ucr obtained from staking STB, then it will burn STB to get ucr. The fixed rate is: 1 Ucr = 100 UNIT, fee limit still has (30 - 10) STB = 20 STB available, so the ucr it can keep consuming is 20 STB / 100 UNIT = 200000 ucr.

Finally, in this call, the ucr A can use is (100000 + 200000) = 300000 ucr.

If contract executes successfully without any exception, the ucr needed for the execution will be deducted. Generally, it is far more less than the amount of ucr this trigger can use.

If Assert-style error come out, it will consume the whole number of ucr set for fee limit.

**Example 2**

A has an account with a balance of 90 STB(90000000 UNIT) and 10 STB staked for 100000 ucr.

Smart contract C set the caller ucr consumption proportion to 40% which means the developer will pay for the rest 60% ucr consumption.

Developer D stakes 50 STB to get 500000 ucr.

A triggers C, the fee limit set is 200000000 (unit UNIT, 200 STB).

So during this trigger the ucr A can use is from three parts:
- A's ucr by staking STB -- X;
- The ucr converted from the amount of STB bruning according to a fixed rate -- Y;
If fee limit is greater than the ucr obtained from staking STB, then it will burn STB to get ucr. The fixed rate is: 1 Ucr = 100 UNIT, fee limit still has (200 - 10) STB = 190 STB available, but A only has 90 STB left, so the ucr it can keep consuming is 90 STB / 100 UNIT = 900000 ucr;
- D's ucr by staking STB -- Z;

There are two situation:
if (X + Y) / 40% >= Z / 60%, the ucr A can use is X + Y + Z
if (X + Y) / 40% < Z / 60%, the ucr A can use is (X + Y) / 40%

If contract executes successfully without any exception, the ucr needed for the execution will be deducted. Generally, it is far more less than the amount of ucr this trigger can use.

Note: when developer create a contract, do not set consume_user_resource_percent to 0, which means developer will undertake all the ucr consumption. If Assert-style error comes out, it will consume all ucr from the developer itsef.

To avoid unnecessary lost, 10 - 100 is recommended for consume_user_resource_percent.

## 5.4 Smart Contract Development Tool

**Start a 21**

Make sure the fullnode code has been deployed locally, you can check if 'Produce block successfully' log appears in FullNode/logs/stabila.log

** Write your first smart contract **

pragma solidity <=0.8.0;
contract DataStore {

    mapping(uint256 => uint256) data;

    function set(uint256 key, uint256 value) public {
        data[key] = value;
    }

    function get(uint256 key) view public returns (uint256 value) {
        value = data[key];
    }
}

**Using Wallet-cli to Deploy**

Download Wallet-Cli and build

```shell
# download source code
git clone https://github.com/stabilaprotocol/wallet-cli
cd  wallet-cli
# build
./gradlew build
cd  build/libs
```

Note: You need to change the node ip and port in config.conf

start wallet-cli

```text
java -jar wallet-cli.jar
```

after started, you can use command lines to operate:

```text
importwallet
<input your password twice for your account>
<input your private key>
login
<input your password you set>
getbalance
```

deploy contract

```text
Shell
# contract deployment command
DeployContract contractName ABI byteCode constructor params isHex fee_limit consume_user_resource_percent <value> <library:address,library:address,...>

# parameters
contract_name: Contract name
ABI: ABI content from generated .abi file
bytecode: ByteCode content from generated .bin file
constructor: When deploy contract, this will be called. If is needed, write as constructor(uint256,string). If not, just write #
params: The parameters of the constructor, use ',' to split, like  1, "test", if no constructor, just write #
fee_limit: The STB consumption limit for the deployment, unit is UNIT(1 UNIT = 10^-6 STB)
consume_user_resource_percent: Consume user's resource percentage. It should be an integer between [0, 100]. if 0, means it does not consume user's resource until the developer's resource has been used up
value: The amount of STB transfer to the contract when deploy
library: If the contract contains library, you need to specify the library address

# example
deploycontract DataStore [{"constant":false,"inputs":[{"name":"key","type":"uint256"},{"name":"value","type":"uint256"}],"name":"set","outputs":[],"payable":false,"stateMutability":"nonpayable","type":"function"},{"constant":true,"inputs":[{"name":"key","type":"uint256"}],"name":"get","outputs":[{"name":"value","type":"uint256"}],"payable":false,"stateMutability":"view","type":"function"}] 608060405234801561001057600080fd5b5060de8061001f6000396000f30060806040526004361060485763ffffffff7c01000000000000000000000000000000000000000000000000000000006000350416631ab06ee58114604d5780639507d39a146067575b600080fd5b348015605857600080fd5b506065600435602435608e565b005b348015607257600080fd5b50607c60043560a0565b60408051918252519081900360200190f35b60009182526020829052604090912055565b600090815260208190526040902054905600a165627a7a72305820fdfe832221d60dd582b4526afa20518b98c2e1cb0054653053a844cf265b25040029 # # false 1000000 30 0
If it is deployed successfully, it will return 'Deploy the contract successfully'
```

get the contract address

```text
Your smart contract address will be: <contract address>

# in this example
Your smart contract address will be: TTWq4vMEYB2yibAbPV7gQ4mrqTyX92fha6
```

call the contract to store data, query data

```text
Shell
# call contract command
triggercontract <contract_address> <method> <args> <is_hex> <fee_limit> <value>

# parameters
contract_address: Contract address, like TTWq4vMEYB2yibAbPV7gQ4mrqTyX92fha6
method: The method called, like set(uint256,uint256) or fool(), use ',' to split the parameters. Do not leave space between parameters
args: The parameters passed to the method called, use ',' to split the parameters. Do not leave space between parameters
is_hex: whether the input parameters is Hex, false or true
fee_limit: The STB consumption limit for the trigger, unit is UNIT(1 UNIT = 10^-6 STB)
value: The amount of STB transfer to the contract when trigger

# trigger example
## set mapping 1->1
triggercontract TTWq4vMEYB2yibAbPV7gQ4mrqTyX92fha6 set(uint256,uint256) 1,1 false 1000000  0000000000000000000000000000000000000000000000000000000000000000

## get mapping key = 1
triggercontract TTWq4vMEYB2yibAbPV7gQ4mrqTyX92fha6 get(uint256) 1 false 1000000  0000000000000000000000000000000000000000000000000000000000000000
```

If the function called is constant or view, wallet-cli will return the result directly.
If it contains library, before deploy the contract you need to deploy the library first. After you deploy library, you can get the library address, then fill the address in library:address,library:address,...

```text
# for instance, using remix to get the bytecode of the contract, like:
608060405234801561001057600080fd5b5061013f806100206000396000f300608060405260043610610041576000357c0100000000000000000000000000000000000000000000000000000000900463ffffffff168063f75dac5a14610046575b600080fd5b34801561005257600080fd5b5061005b610071565b6040518082815260200191505060405180910390f35b600073<b>__browser/oneLibrary.sol.Math3__________<\b>634f2be91f6040518163ffffffff167c010000000000000000000000000000000000000000000000000000000002815260040160206040518083038186803b1580156100d357600080fd5b505af41580156100e7573d6000803e3d6000fd5b505050506040513d60208110156100fd57600080fd5b81019080805190602001909291905050509050905600a165627a7a7230582052333e136f236d95e9d0b59c4490a39e25dd3a3dcdc16285820ee0a7508eb8690029
```

The address of the library deployed before is: SSEJ29gnBkxQZR3oDdLdeQtQQykpVLSk54
When you deploy, you need to use browser/oneLibrary.sol.Math3:SSEJ29gnBkxQZR3oDdLdeQtQQykpVLSk54 as the parameter of deploycontract.

# 6. SRC-10 Token Introduction
STABILA network support two types of token, one is SRC-20 token issued by smart contract, the other one is SRC-10 token issued by system contract.

## 6.1 How to Issue a SRC-10 Token
HTTP API:

```text
wallet/createassetissue
Description: Issue a token
demo: curl -X POST  http://127.0.0.1:8090/wallet/createassetissue -d '{
"owner_address":"41e552f6487585c2b58bc2c9bb4492bc1f17132cd0",
"name":"0x6173736574497373756531353330383934333132313538",
"abbr": "0x6162627231353330383934333132313538",
"total_supply" :4321,
"stb_num":1,
"num":1,
"start_time" : 1530894315158,
"end_time":1533894312158,
"description":"007570646174654e616d6531353330363038383733343633",
"url":"007570646174654e616d6531353330363038383733343633",
"free_asset_net_limit":10000,
"public_free_asset_net_limit":10000,
"cded_supply":{"cded_amount":1, "cded_days":2}
}'
Parameter owner_address: Owner address, default hexString
Parameter name: Token name, default hexString
Parameter abbr: Token name abbreviation, default hexString
Parameter total_supply: Token total supply
Parameter stb_num: Define the price by the ratio of stb_num/num,
Parameter num: Define the price by the ratio of stb_num/num
Parameter start_time: ICO start time
Parameter end_time: ICO end time
Parameter description: Token description, default hexString
Parameter url: Token official website url, default hexString
Parameter free_asset_net_limit: Token free asset net limit
Parameter public_free_asset_net_limit: Token public free asset net limit
Parameter cded_supply: Token staked supply
Parameter permission_id: Optional, for multi-signature use
Return: Transaction object
Note: The unit of 'stb_num' is UNIT
```

## 6.2 Participate SRC-10 Token
HTTP API:

```text
wallet/participateassetissue
Description: Participate a token
demo: curl -X POST http://127.0.0.1:8090/wallet/participateassetissue -d '{
"to_address": "41e552f6487585c2b58bc2c9bb4492bc1f17132cd0",
"owner_address":"41e472f387585c2b58bc2c9bb4492bc1f17342cd1",
"amount":100,
"asset_name":"3230313271756265696a696e67"
}'
Parameter to_address: The issuer address of the token, default hexString
Parameter owner_address: The participant address, default hexString
Parameter amount: Participate token amount
Parameter asset_name: Token id, default hexString
Parameter permission_id: Optional, for multi-signature use
Return: Transaction object
Note: The unit of 'amount' is the smallest unit of the token
```

## 6.3 SRC-10 Token Transfer
HTTP API:

```text
wallet/transferasset
Description: Transfer token
demo: curl -X POST  http://127.0.0.1:8090/wallet/transferasset -d '{"owner_address":"41d1e7a6bc354106cb410e65ff8b181c600ff14292", "to_address": "41e552f6487585c2b58bc2c9bb4492bc1f17132cd0", "asset_name": "31303030303031", "amount": 100}'
Parameter owner_address: Owner address, default hexString
Parameter to_address: To address, default hexString
Parameter asset_name: Token id, default hexString
Parameter amount: Token transfer amount
Parameter permission_id: Optional, for multi-signature use
Return: Transaction object
Note: The unit of 'amount' is the smallest unit of the token
```

# 7. Resource Model
## 7.1 Resource Model Introduction

STABILA network has 4 types of resources: Bandwidth, CPU, Storage and RAM. Benefit by STABILA's exclusive RAM model, STABILA's RAM resource is almost infinite.

STABILA network imports two resource conceptions: Bandwidth points and Ucr. Bandwidth Point represents Bandwidth, Ucr represents CPU and Storage.

Note:
- Ordinary transaction only consumes Bandwidth points
- Smart contract related transaction not only consumes Bandwidth points, but also Ucr

## 7.2 Bandwidth Points

The transaction information is stored and transmitted in the form of byte array, Bandwidth Points consumed = the number of bytes of the transaction * Bandwidth Points rate. Currently Bandwidth Points rate = 1

Such as if the number of bytes of a transaction is 200, so this transaction consumes 200 Bandwidth Points.

Note: Due to the change of the total amount of the staked STB in the network and the self-staked STB amount, the Bandwidth Points an account possesses is not fixed.

## 7.2.1 How to Get Bandwidth Points

1.&nbsp;By staking STB to get Bandwidth Points, Bandwidth Points = the amount of STB self-staked / the total amount of STB staked for Bandwidth Points in the network * 43_200_000_000

2.&nbsp;Every account has a fixed amount of free Bandwidth Points every day, it is defined in #61 network parameter, user can check the value on stabilascan(https://stabilascan.org/representatives).

### 7.2.2 Bandwidth Points Consumption

Transactions other than queries consume Bandwidth points.

A special scenario: When transferring STB or SRC-10 tokens to an account that does not yet exist, this procedure creates the account prior to the transfer.

To create an account, a flat charge of 1 STB is required. If there are insufficient Bandwidth points obtained by STB staking, an additional 0.1 STB will be spent.

Bandwidth points consumption sequence for SRC-10 transfer:

1. Free Bandwidth points.

2. SRC-10 issuer's Bandwidth points(if possible.)

3. Bandwidth points STB staking.

4. Bandwidth points obtained by STB burning, the rate = the number of bytes of the transaction * 1_000 UNIT;

Bandwidth points consumption sequence for other transactions:

1. Free Bandwidth points.

2. Bandwidth points STB staking.

3. Bandwidth points obtained by STB burning, the rate = the number of bytes of the transaction * 1_000 UNIT;

### 7.2.3 Bandwidth Points Recovery
Every 24 hours, the amount of the usage of Bandwidth points of an account will be reset to 0.
## 7.3 Ucr
[5.3 Ucr Introduction](#5.3-ucr-introduction)

## 7.4 Resource Delegation
In STABILA network, an account can stake STB for Bandwidth or Ucr for other accounts. The primary account owns the staked STB and STABILA power, the recipient account owns the Bandwidth or Ucr. Like ordinary staking, resource delegation staking is also at least 3 days.

+ Example(Using wallet-cli)
```text
cdBalance cded_balance cded_duration [ResourceCode:0 BANDWIDTH,1 UCR] [receiverAddress]

cded_balance: the amount of STB to stake (unit UNIT)
cded_duration: the staking period (currently a fixed 3 days)
ResourceCode: 0 for Bandwidth, 1 for Ucr
receiverAddress: recipient account address
```

## 7.5 Other Fees

|Type|Fee|
| :------|:------:|
|Create a executive|9999 STB|
|Issue a SRC-10 token|1024 STB|
|Create an account|1 STB|
|Create an exchange|1024 STB|

# 8. Wallet Introduction
## 8.1 wallet-cli Introduction
Please refer to:
[https://github.com/stabilaprotocol/wallet-cli/blob/master/README.md](https://github.com/stabilaprotocol/wallet-cli/blob/master/README.md)

## 8.2 Get Transaction ID

```text
Hash.sha256(transaction.getRawData().toByteArray())
```
## 8.3 Get Block ID

```text
private byte[] generateBlockId(long blockNum, byte[] blockHash) {
  byte[] numBytes = Longs.toByteArray(blockNum);
  byte[] hash = blockHash;
  System.arraycopy(numBytes, 0, hash, 0, 8);
  return hash;
 }
```
## 8.4 How to Build a Transaction Locally
According to the definition of the transaction, you need to fill up all the fields of the transaction.

You need to set reference block and expiration time information, so you need to connect to the Mainnet. We recommend to use the latest block on fullnode as the value of reference block, use the latest block time plus N minutes as the value of expiration time.

The network judgment condition is if (expiration > latest block time and expiration < latest block time + 24 hours) means the transaction is in period of validity. Otherwise, it will be an overdue transaction, will not be accepted by the Mainnet.

Way to set reference block: set RefBlockHash the bytes from the 8 to 16(not included) of the hash of the latest block, set BlockBytes the bytes from 6 to 8(not included) of the height of the latest block.
```text
public static Transaction setReference(Transaction transaction, Block newestBlock) {
     long blockHeight = newestBlock.getBlockHeader().getRawData().getNumber();
     byte[] blockHash = getBlockHash(newestBlock).getBytes();
     byte[] refBlockNum = ByteArray.fromLong(blockHeight);
     Transaction.raw rawData = transaction.getRawData().toBuilder()
         .setRefBlockHash(ByteString.copyFrom(ByteArray.subArray(blockHash, 8, 16)))
         .setRefBlockBytes(ByteString.copyFrom(ByteArray.subArray(refBlockNum, 6, 8)))
         .build();
     return transaction.toBuilder().setRawData(rawData).build();
   }
```
Way to set expiration time and transaction timestamp:
```text
public static Transaction createTransaction(byte[] from, byte[] to, long amount) {
     Transaction.Builder transactionBuilder = Transaction.newBuilder();
     Block newestBlock = WalletClient.getBlock(-1);

     Transaction.Contract.Builder contractBuilder = Transaction.Contract.newBuilder();
     Contract.TransferContract.Builder transferContractBuilder = Contract.TransferContract
         .newBuilder();
     transferContractBuilder.setAmount(amount);
     ByteString bsTo = ByteString.copyFrom(to);
     ByteString bsOwner = ByteString.copyFrom(from);
     transferContractBuilder.setToAddress(bsTo);
     transferContractBuilder.setOwnerAddress(bsOwner);
     try {
       Any any = Any.pack(transferContractBuilder.build());
       contractBuilder.setParameter(any);
     } catch (Exception e) {
       return null;
     }
     contractBuilder.setType(Transaction.Contract.ContractType.TransferContract);
     transactionBuilder.getRawDataBuilder().addContract(contractBuilder)
         .setTimestamp(System.currentTimeMillis()) //in the form of millisecond
         .setExpiration(newestBlock.getBlockHeader().getRawData().getTimestamp() + 10 * 60 * 60 * 1000);
     Transaction transaction = transactionBuilder.build();
     Transaction refTransaction = setReference(transaction, newestBlock);
     return refTransaction;
   }
```
