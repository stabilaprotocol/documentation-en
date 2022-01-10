 # Stabila Network Instructure

Stabila network uses Peer-to-Peer(P2P) network instructure, all nodes status equal. There are two types of node: Governor and FullNode. Governor produces blocks, FullNode synchronizes blocks and broadcasts transactions. Any device that deploy the java-stabila code can join Stabila network as a node.

![image](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/network.png)

## Governor

Governor(abbr: GOV) is the block producer in STABILA network, there are 21 GOVs. They verify the transactions and write the transactions into the blocks in turn. The Governors' information is public to everyone in Stabila network. The best way to browse is using [Stabilascan](https://stabilascan.org/representatives).

Recommended Hardware Configuration:

```text
minimum requirement:
CPU: 16 cores, RAM: 32G, Bandwidth: 100M, Disk: 1T
Recommended requirement:
CPU: > 64 cores RAM: > 64G, Bandwidth: > 500M, Disk: > 2T
```

## FullNode

FullNode has the complete blockchain data, can update data in real time. It can broadcast the transactions and provide api service.

Recommended Hardware Configuration:

```text
minimum requirement:
CPU: 16 cores, RAM: 32G, Bandwidth: 100M, Disk: 1T
Recommended requirement:
CPU: > 32 cores RAM: > 48G, Bandwidth: > 500M, Disk: > 2T
```