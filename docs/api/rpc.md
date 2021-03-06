# RPC List

**For the specific definition of API, please refer to the following link:**
[api/api.proto](https://github.com/stabilaprotocol/protocol/blob/master/api/api.proto)

**1.&nbsp;Get account information**

```protobuf
rpc GetAccount (Account) returns (Account) {}
```
Nodes: Fullnode

**2.&nbsp;STB transfer**

```protobuf
rpc CreateTransaction (TransferContract) returns (Transaction) {}
```
Nodes: Fullnode

**3.&nbsp;Broadcast transaction**

```protobuf
rpc BroadcastTransaction (Transaction) returns (Return) {}
```
Nodes: Fullnode

Description:
Transfer, vote, issuance of token, or participation in token offering. Sending signed transaction information to node, and broadcasting it to the entire network after executive verification.

**4.&nbsp;Create an account**

```protobuf
rpc CreateAccount (AccountCreateContract) returns (Transaction) {}
```
Nodes: FullNode

**5.&nbsp;Account name update**
```protobuf
rpc UpdateAccount (AccountUpdateContract) returns (Transaction) {}
```
Nodes: Fullnode

**6.&nbsp;Vote for Governor candidates**
```protobuf
rpc VoteExecutiveAccount (VoteExecutiveContract) returns (Transaction) {}
```
Nodes: FullNode

**7.&nbsp;Query the ratio of brokerage of the executive**
```protobuf
rpc GetBrokerageInfo (BytesMessage) returns (NumberMessage) {}
```
Nodes: FullNode

**8.&nbsp;Query unclaimed reward**
```protobuf
rpc GetRewardInfo (BytesMessage) returns (NumberMessage) {}
```
Nodes: FullNode

**9.&nbsp;Update the ratio of brokerage**
```protobuf
rpc UpdateBrokerage (UpdateBrokerageContract) returns (TransactionExtention) {}
```
Nodes: FullNode

**10.&nbsp;Issue a token**
```protobuf
rpc CreateAssetIssue (AssetIssueContract) returns (Transaction) {}
```
Nodes: FullNode

**11.&nbsp;Query of list of executives**
```protobuf
rpc ListExecutivees (EmptyMessage) returns (ExecutiveList) {}
```
Nodes: FullNode

**12.&nbsp;Application for Governor**
```protobuf
rpc CreateExecutive (ExecutiveCreateContract) returns (Transaction) {}
```
Nodes: FullNode

Description:
To apply to become STABILA’s Governor candidate.

**13.&nbsp;Information update of executives**
```protobuf
rpc UpdateExecutive (ExecutiveUpdateContract) returns (Transaction) {}
```
Nodes: FullNode

Description: Update the website url of the GOV.

**14.&nbsp;Token transfer**
```protobuf
rpc TransferAsset (TransferAssetContract) returns (Transaction){}
```
Node: FullNode

**15.&nbsp;Participate a token**
```protobuf
rpc ParticipateAssetIssue (ParticipateAssetIssueContract) returns (Transaction) {}
```
Nodes: FullNode

**16.&nbsp;Query the list of nodes connected to the ip of the api**
```protobuf
rpc ListNodes (EmptyMessage) returns (NodeList) {}
```
Nodes: FullNode

**17.&nbsp;Query the list of all issued tokens**
```protobuf
rpc GetAssetIssueList (EmptyMessage) returns (AssetIssueList) {}
```
Nodes: FullNode

**18.&nbsp;Query the token issued by a given account**
```protobuf
rpc GetAssetIssueByAccount (Account) returns (AssetIssueList) {}
```
Nodes: FullNode

**19.&nbsp;Query the token information by token name**
```protobuf
rpc GetAssetIssueByName (BytesMessage) returns (AssetIssueContract) {}
```
Nodes: FullNode

**20.&nbsp;Query the list of tokens by timestamp**
```protobuf
rpc GetAssetIssueListByTimestamp (NumberMessage) returns (AssetIssueList){}
```
Nodes: FullNode

**21.&nbsp;Get current block information**
```protobuf
rpc GetNowBlock (EmptyMessage) returns (Block) {}
```
Nodes: FullNode

**22.&nbsp;Get a block by block height**
```protobuf
rpc GetBlockByNum (NumberMessage) returns (Block) {}
```
Nodes: FullNode

**23.&nbsp;Get the total number of transactions**
```protobuf
rpc TotalTransaction (EmptyMessage) returns (NumberMessage) {}
```
Nodes: FullNode

**24.&nbsp;Query the transaction by transaction id**
```protobuf
rpc getTransactionById (BytesMessage) returns (Transaction) {}
```
Nodes: FullNode

**25.&nbsp;Stake STB**
```protobuf
rpc CdBalance (CdBalanceContract) returns (Transaction) {}
```
Nodes: FullNode

**26.&nbsp;Unstake STB**
```protobuf
rpc UncdBalance (UncdBalanceContract) returns (Transaction) {}
```
Nodes: FullNode

**27.&nbsp;Block producing reward redemption**
```protobuf
rpc WithdrawBalance (WithdrawBalanceContract) returns (Transaction) {}
```
Nodes: FullNode

**27.&nbsp;Unstake token balance**
```protobuf
rpc UncdAsset (UncdAssetContract) returns (Transaction) {}
```
Nodes: FullNode

**29.&nbsp;Query the next maintenance time**
```protobuf
rpc GetNextMaintenanceTime (EmptyMessage) returns (NumberMessage) {}
```
Nodes: FullNode

**30.&nbsp;Query the transaction fee & block information**
```protobuf
rpc GetTransactionInfoById (BytesMessage) returns (TransactionInfo) {}
```
Nodes: FullNode

**31.&nbsp;Query block information by block id**
```protobuf
rpc GetBlockById (BytesMessage) returns (Block) {}
```
Nodes: FullNode

**32.&nbsp;Update token information**
```protobuf
rpc UpdateAsset (UpdateAssetContract) returns (Transaction) {}
```
Nodes: FullNode

Description:
Token update can only be initiated by the token issuer to update token description, url, maximum bandwidth consumption by each account and total bandwidth consumption.

**33.&nbsp;Query the list of all the tokens by pagination**
```protobuf
rpc GetPaginatedAssetIssueList (PaginatedMessage) returns (AssetIssueList) {}
```
Nodes: FullNode

**34.&nbsp;To sign a transaction**
```protobuf
rpc GetTransactionSign (TransactionSign) returns (Transaction) {}
```
Nodes: FullNode

**35.&nbsp;Address and private key creation**
```protobuf
rpc CreateAdresss (BytesMessage) returns (BytesMessage) {}
```
Nodes: FullNode

**36.&nbsp;STB easy transfer**
```protobuf
rpc EasyTransfer (EasyTransferMessage) returns (EasyTransferResponse) {}
```
Nodes: FullNode

**37.&nbsp;Deploy a smart contract**
```protobuf
rpc DeployContract (CreateSmartContract) returns (TransactionExtention) {}
```
Nodes: FullNode

**38.&nbsp;Trigger a smart contract**
```protobuf
rpc TriggerContract (TriggerSmartContract) returns (TransactionExtention) {}
```
Nodes: FullNode

**39.&nbsp;Create a shielded transaction**
```protobuf
rpc CreateShieldedTransaction (PrivateParameters) returns (TransactionExtention) {}
```
Nodes: FullNode

**40.&nbsp;Get a Merkle tree information of a note**
```protobuf
rpc GetMerkleTreeVoucherInfo (OutputPointInfo) returns (IncrementalMerkleVoucherInfo) {}
```
Nodes: FullNode

**41.&nbsp;Scan note by ivk**
```protobuf
rpc ScanNoteByIvk (IvkDecryptParameters) returns (DecryptNotes) {}
```
Nodes: FullNode

**42.&nbsp;Scan note by ovk**
```protobuf
rpc ScanNoteByOvk (OvkDecryptParameters) returns (DecryptNotes) {}
```
Nodes: FullNode

**43.&nbsp;Get spending key**
```protobuf
rpc GetSpendingKey (EmptyMessage) returns (BytesMessage) {}
```
Nodes: FullNode

**44.&nbsp;Get expanded spending key**
```protobuf
rpc GetExpandedSpendingKey (BytesMessage) returns (ExpandedSpendingKeyMessage) {}
```
Nodes: FullNode

**45.&nbsp;Get ak from ask**
```protobuf
rpc GetAkFromAsk (BytesMessage) returns (BytesMessage) {}
```
Nodes: FullNode

**46.&nbsp;Get nk from nsk**
```protobuf
rpc GetNkFromNsk (BytesMessage) returns (BytesMessage) {}
```
Nodes: FullNode

**47.&nbsp;Get incoming viewing key**
```protobuf
rpc GetIncomingViewingKey (ViewingKeyMessage) returns (IncomingViewingKeyMessage) {}
```
Nodes: FullNode

**48.&nbsp;Get diversifier**
```protobuf
rpc GetDiversifier (EmptyMessage) returns (DiversifierMessage) {}
```
Nodes: FullNode

**49.&nbsp;Get zen payment address**
```protobuf
rpc GetZenPaymentAddress (IncomingViewingKeyDiversifierMessage) returns (PaymentAddressMessage) {}
```
Nodes: FullNode

**50.&nbsp;Get rcm**
```protobuf
rpc GetRcm (EmptyMessage) returns (BytesMessage) {}
```
Nodes: FullNode

**51.&nbsp;Get a note status of is spent or not**
```protobuf
rpc IsSpend (NoteParameters) returns (SpendResult) {}
```
Nodes: FullNode

**52.&nbsp;Create a shielded transaction without using ask**
```protobuf
rpc CreateShieldedTransactionWithoutSpendAuthSig (PrivateParametersWithoutAsk) returns (TransactionExtention) {}
```
Nodes: FullNode

**53.&nbsp;Create a shielded transaction hash**
```protobuf
rpc GetShieldTransactionHash (Transaction) returns (BytesMessage) {}
```
Nodes: FullNode

**54.&nbsp;Create a signature for a shielded transaction**
```protobuf
rpc CreateSpendAuthSig (SpendAuthSigParameters) returns (BytesMessage) {}
```
Nodes: FullNode

**55.&nbsp;Create a shield nullifier**
```protobuf
rpc CreateShieldNullifier (NfParameters) returns (BytesMessage) {}
```
Nodes: FullNode

**56.&nbsp;Get new shielded address**
```protobuf
rpc GetNewShieldedAddress (EmptyMessage) returns (ShieldedAddressInfo){}
```
Nodes: FullNode

**57.&nbsp;Create shielded contract parameters**
```protobuf
rpc CreateShieldedContractParameters (PrivateShieldedSRC20Parameters) returns (ShieldedSRC20Parameters) {}
```
Nodes: FullNode

**58.&nbsp;Create shielded contract parameters without ask**
```protobuf
rpc CreateShieldedContractParametersWithoutAsk (PrivateShieldedSRC20ParametersWithoutAsk) returns (ShieldedSRC20Parameters) {}
```
Nodes: FullNode

**59.&nbsp;Scan shielded SRC20 notes by ivk**
```protobuf
rpc ScanShieldedSRC20NotesbyIvk (IvkDecryptSRC20Parameters) returns (DecryptNotesSRC20) {}
```
Nodes: FullNode

**60.&nbsp;Scan shielded SRC20 notes by ovk**
```protobuf
rpc ScanShieldedSRC20NotesbyOvk (OvkDecryptSRC20Parameters) returns (DecryptNotesSRC20) {}
```
Nodes: FullNode

**61.&nbsp;Get the status of shielded SRC20 note of spent or not**
```protobuf
rpc IsShieldedSRC20ContractNoteSpent (NfSRC20Parameters) returns (NullifierResult) {}
```
Nodes: FullNode

**62.&nbsp;Get the trigger input for the shielded SRC20**
```protobuf
  rpc GetTriggerInputForShieldedSRC20Contract (ShieldedSRC20TriggerContractParameters) returns (BytesMessage) {}
```
Nodes: FullNode


**63.&nbsp;Create an market order**
Interface statement:
rpc MarketSellAsset (MarketSellAssetContract) returns (TransactionExtention) {};
Nodes: FullNode

**64.&nbsp;Cancel the order**
Interface statement:
rpc MarketCancelOrder (MarketCancelOrderContract) returns (TransactionExtention) {};
Nodes: FullNode

**65.&nbsp;Get all orders for the account**
Interface statement:
rpc GetMarketOrderByAccount (BytesMessage) returns (MarketOrderList) {};
Nodes: FullNode

**66.&nbsp;Get all trading pairs**
Interface statement:
rpc GetMarketPairList (EmptyMessage) returns (MarketOrderPairList) {};
Nodes: FullNode

**67.&nbsp;Get all orders for the trading pair**
Interface statement:
rpc GetMarketOrderListByPair (MarketOrderPair) returns (MarketOrderList) {};
Nodes: FullNode

**68.&nbsp;Get all prices for the trading pair**
Interface statement:
rpc GetMarketPriceByPair (MarketOrderPair) returns (MarketPriceList) {};
Nodes: FullNode

**69.&nbsp;Get order by id**
Interface statement:
rpc GetMarketOrderById (BytesMessage) returns (MarketOrder) {};
Nodes: FullNode

**70.&nbsp;perform a historical balance lookup**
Interface statement:
rpc GetAccountBalance (AccountBalanceRequest) returns (AccountBalanceResponse){};
Nodes: FullNode

**71.&nbsp;fetch all balance-changing transactions in a block**
Interface statement:
rpc GetBlockBalanceTrace (BlockBalanceTrace.BlockIdentifier) returns (BlockBalanceTrace) {};
Nodes: FullNode

**72.&nbsp;get the burn stb amount**
Interface statement:
rpc GetBurnStb (EmptyMessage) returns (NumberMessage) {};
Nodes: FullNode
