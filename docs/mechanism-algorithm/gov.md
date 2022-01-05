# Governor

## How to Become a Governor

In STABILA network, any account can apply to become a executive. Every account can vote for executives.

The top 21 executives are called Governor, the executives from 22nd to 100th are called Partner, the executives after 100th are called Candidates. Only Governor can produce blocks.

The votes will be counted every 6 hours, so governors may also change every 6 hours.

To prevent vicious attack, STABILA network burns 9999 STB from the account that applies to become a governor candidate.

## Governor Election

To vote, you need to have STABILA Power(TP). To get STABILA Power, you need to stake STB. Every 1 staked STB accounts for one STABILA Power(TP). Every account in STABILA network has the right to vote for a governor candidate. After you unstake your staked STB, you will lose the responding STABILA Power(TP), so your previous vote will be invalid.

Note: Only your latest vote will be counted in STABILA network which means your previous vote will be overwritten by your latest vote.

Example (Using wallet-cli):

```console
> cdbalance 10,000,000 3 // Stake 10 STB to get 10 STABILA Power(TP)
> voteexecutive executive1 4 executive2 6 // Vote 4 votes for executive1, 6 votes for executive2
> voteexecutive executive1 3 executive2 7 // Vote 3 votes for executive1, 7 votes for executive2
```

The final output above is: Vote 3 votes for executive1, 7 votes for executive2

### Executives Brokerage

The default ratio is 20%, which can be modified by the executives.

If a executive get 20% of the reward, and the other 80% will be awarded to the voters. If the brokerage ratio is set to 100%, the rewards are all obtained by the executive; if set to 0, the rewards are all sent to the voters.

## Reward for Executives

Often referred as Executive Reward, the topmost 79 Executives will split 78 STB as earned once per round (6 hours). The prize will be divided according on the vote percentage each Executive earns.

Total E reward per round = 10,972 Unit/block × 20 blocks/min × 60 mins/hr × 6 hrs/round.

A total of 28,834 STB will be given out every year to the 79 Gs.

## Committee

### 1. What is Committee

Committee can modify the STABILA network parameters, like transaction fees, block producing reward amount, etc. Committee is composed of the current 21 governors. Every governor has the right to start a proposal. The proposal will be passed after it gets 15 or more approves from the governors and will become valid in the next maintenance period.

### 2. Create a Proposal

Only Governors, Partners and Candidates can create a proposal.

The network parameters can be modified([min,max]).

{0,1}: 1 means 'allowed' or 'actived', 0 means 'disallow', 'disable' or 'no'.

| #  | Command                                                                                                                                       | Value                 |
|----|-----------------------------------------------------------------------------------------------------------------------------------------------|-----------------------|
| 0  | MaintenanceTimeInterval <br> (To modify the maintenance interval of Governor)                                                                 | 21600000 ms           |
| 1  | AccountUpgradeCost <br> (To modify the cost of applying for Governor account)                                                                 | 1000000000 STB        |
| 2  | CreateAccountFee <br> (To modify the account creation fee)                                                                                    | 1385 STB              |
| 3  | TransactionFee <br> (To modify the amount of STB used to gain extra bandwidth)                                                                | 40 STB                |
| 4  | AssetIssueFee <br> (To modify asset issuance fee)                                                                                             | 1000000000 STB        |
| 5  | ExecutivePayPerBlock <br> (To modify Governor block generation reward)                                                                        | 221714 STB            |
| 6  | ExecutiveStandbyAllowance <br> (To modify the rewards given to the top 21 Governors and <br> the following 100 executives)                    | 0 STB                 |
| 7  | CreateNewAccountFeeInSystemContract <br> (To modify the cost of account creation)                                                             | 0 STB                 |
| 8  | CreateNewAccountBandwidthRate <br> (To modify the consumption of bandwidth of account creation)                                               | 1&nbsp;Bandwidth/Byte |
| 9  | AllowCreationOfContracts <br> (To activate the Virtual Machine (VM))                                                                          | 0 <br> {0, 1}         |
| 10 | RemoveThePowerOfTheGr <br> (To remove the GR Genesis votes)                                                                                   | 0                     |
| 11 | UcrFee <br> (To modify the fee of 1 ucr)                                                                                                      | 40 UNIT               |                            |
| 12 | ExchangeCreateFee <br> (To modify the cost of trading pair creation)                                                                          | 14000000 STB          |
| 13 | MaxCpuTimeOfOneTx <br> (To modify the maximum execution time of one transaction)                                                              | 80 ms                 |
| 14 | AllowUpdateAccountName <br> (To allow to change the account name)                                                                             | 0                     |
| 15 | AllowSameTokenName <br> (To allow the same token name)                                                                                        | 0  <br> {0, 1}        |
| 16 | AllowDelegateResource <br> (To allow resource delegation)                                                                                     | 0 <br> {0, 1}         |
| 18 | AllowSvmTransferSrc10 <br> (To allow the SRC-10 token transfer in smart contracts)                                                            | 0 <br> {0, 1}         |
| 19 | TotalUcrCurrentLimit <br> (To modify current total ucr limit)                                                                                 | 30000000000           |
| 20 | AllowMultiSign <br> (To allow the initiation of multi-signature)                                                                              | 0 <br> {0, 1}         |
| 21 | AllowAdaptiveUcr <br> (To allow adaptive adjustment for total Ucr)                                                                            | 0 <br> {0, 1}         |
| 22 | UpdateAccountPermissionFee <br> (To modify the fee for updating account permission)                                                           | 1385000               |
| 23 | MultiSignFee <br> (To modify the fee for multi-signature)                                                                                     | 13857                 |
| 24 | AllowProtoFilterNum <br> (To enable protocol optimization)                                                                                    | 0 <br> {0, 1}         |
| 26 | AllowSvmConstantinople <br> (To support the new commands of Constantinople)                                                                   | 0 <br> {0, 1}         |
| 21 | AllowShieldedTransaction <br> (To enable shielded transaction)                                                                                | 0 <br> {0, 1}         |
| 29 | AdaptiveResourceLimitMultiplier <br> (To modify the adaptive ucr limit multiplier)                                                            | 1000                  |
| 30 | ChangeDelegation <br> (Propose to support the decentralized vote dividend)                                                                    | 0 <br> {0, 1}         |
| 31 | Executive127PayPerBlock <br> (Propose to modify the block voting rewards given to <br> the top 21 Governors and the following 100 executives) | 10972 STB             |
| 32 | AllowSvmSolidity059 <br> (To allow SVM to support solidity compiler 0.5.9)                                                                    | 0 <br> {0, 1}         |
| 33 | AdaptiveResourceLimitTargetRatio <br> (To modify the target ucr limit)                                                                        | 10                    |
| 35 | ForbidTransferToContract                                                                                                                      | 0                     | 
| 39 | AllowShieldedSrc20Transaction                                                                                                                 | 0                     | 
| 40 | AllowPbft	                                                                                                                                    | 0                     | 
| 41 | AllowSvmIstanbul                                                                                                                              | 0                     |                                                                                                                         
| 44 | AllowMarketTransaction                                                                                                                        | 0                     |
| 45 | MarketSellFee                                                                                                                                 | 0                     |
| 46 | MarketCancelFee                                                                                                                               | 0                     |
| 47 | MaxFeeLimit                                                                                                                                   | 15000000              |
| 48 | AllowTransactionFeePool                                                                                                                       | 0                     |
| 49 | AllowBlackholeOptimization                                                                                                                    | 0                     |
| 51 | AllowNewResourceModel                                                                                                                         | 0                     |
| 52 | AllowSvmCd                                                                                                                                    | 0                     | 
| 53 | AllowAccountAssetOptimization	                                                                                                                | 0 |
| 59 | AllowSvmVote                                                                                                                                  | 0 |
| 61 | FreeNetLimit                                                                                                                                  | 500 |
| 62 | TotalNetLimit                                                                                                              | 28800000 |

Example (Using wallet-cli):

```console
> createproposal id value
# id: the serial number (0 ~ 33)
# value: the parameter value
```

Note: In STABILA network, 1 STB = 1_000_000 UNIT

### 3. Vote for a Proposal

Proposal only support YES vote. Since the creation time of the proposal, the proposal is valid within 3 days. If the proposal does not receive enough YES votes within the period of validity, the proposal will be invalid beyond the period of validity. Yes vote can be cancelled.

Example (Using wallet-cli):

```console
> approveProposal id is_or_not_add_approval
# id: proposal id
# is_or_not_add_approval: YES vote or cancel YES vote
```

### 4. Cancel Proposal

Proposal creator can cancel the proposal before it is passed.

Example (Using wallet-cli):

```console
> deleteProposal id
# id: proposal id
```

### 5. Query Proposal

- Query all the proposals list (ListProposals)
- Query all the proposals list by pagination (GetPaginatedProposalList)
- Query a proposal by proposal id (GetProposalById)

For more API detail, please refer to [HTTP API](../api/http.md).
