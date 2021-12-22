# STABILA Virtual Machine (SVM)

STABILA Virtual Machine (SVM) is a lightweight, Turing complete virtual machine developed for the STABILA's ecosystem. Its goal is to provide millions of global developers with a custom-built blockchain system that is efficient, convenient, stable, secure and scalable.

SVM can connect seamlessly with existing development ecosystem and supports DPoS. SVM is able to be compatible with EVM environment in the beginning, so that instead of learning a new programming language, developers can develop, debug and compile smart contracts in a (Ethereum) Remix environment with Solidity and other languages. Once you’ve built and uploaded your smart contract to STABILA’s mainnet, it will be executed on the SVM of the SR node to be isolated from external connections.

Furthermore, SVM employs the concept of Bandwidth. Different from the gas mechanism on Ethereum’s  EVM,  operations of transaction or smart contracts on SVM are free, with no tokens consumed. Technically, executable computation capacity on SVM is not restricted by total holding of tokens.

## Features of SVM
1.&nbsp;Lightweight

SVM adopts a lightweight architecture with the aim of reducing resource consumption to guarantee system performance.

2.&nbsp;Stability and security

With a meticulous design paradigm and fine-grained underlying operation code, SVM can guarantee the preciseness of every step of a computation, diminishing ambiguity to the largest extent. Out of security reasons, transfers and smart contract running cost only bandwidth points, not STB, which exempts STABILA from being attacked similarly to Ethereum for its mode of gas consumption. Stability of bandwidth consumption is achieved while the cost of each computational step is fixed.

3.&nbsp;Compatibility

Currently, SVM is compatible with EVM and will be with more mainstream VMs in the future. Thereby, all smart contracts on EVM are executable on SVM. By connecting seamlessly to existing development ecosystem, higher efficiency can be achieved by developers. Needless to learn a new programming language, they can use mainstream programming languages for smart contract such as Solidity to develop, debug and compile smart contracts in the Remix environment, which greatly reduces development costs.

4.&nbsp;Developer-friendly

Thanks to SVM’s bandwidth setup, developments costs are reduced and developers can focus on the logic of their contract code. SVM also offers all-in-one interfaces for contract deployment, triggering and viewing, for the convenience of developers.
The following interfaces are available in Stabila Wallet-CLI:

 + deploycontract(password, contractAddress, ABI, code, data, value)
 + triggercontract(password, contractAddress, selector, data, value)
 + getcontract(contractAddress)
Developers can call these interfaces to deploy, trigger or check smart contracts.

## How SVM Works

![Flowchart of Stabila Virtual Machine](https://raw.githubusercontent.com/stabilaprotocol/documentation-en/master/images/virtual_machine.png)

The above flowchart shows how SVM works:
Compilation of Stabila smart contract→execution and computing engines of VM→Interoperation service layer for external interfaces.

Put simply, the flow is as follows:
+ Currently, SVM is compatible mainly with Solidity. The compiler translates Solidity smart contract into bytecode readable and executable on SVM.
+ A virtual machine processes data through opcode, which is equivalent to operating a logic of a stack-based finite state machine.
+ SVM accesses blockchain data and invoke External Data Interface through the Interoperation layer.

## Future Development of SVM
1.&nbsp;More developer-friendly debugging tools

Stabila will be committed to the development of optimized debugging tools and the establishment of standardized symbol and data format, for improved developer efficiency.

2.&nbsp;Fulfillment of diversified processing demands

Different from gas consumption mechanism for every transaction on EVM, there is no charge on SVM. Each operation only occupies bandwidth, which will be released within a certain amount of time after completion of transaction. It takes developers very little to develop smart contracts with more complex logic. It is our belief that besides being used for digital asset transactions, smart contracts could also be suitably applied to areas such as game development, financial risk modeling and scientific computing. The design of SVM inherently supports multi-scenario tasks, and further optimizations of processing speed, response time, and floating point compatibility.

3.&nbsp;Improvement of Just-In-Time (JIT) compilation speed and integration of WebAssembly

Improving JIT compilation speed is conducive to faster interpretation and optimized compilation of local code. Meanwhile, Stabila is planning to further optimize its SVM based on WebAssembly (WASM). WebAssembly, spearheaded by Apple, Google, Microsoft and Mozilla, is designed to break bottlenecks of current Web browsers and can be generated through compiling C/C++ and other programming languages. Integrating WASM, SVM will be able to provide high performance and high throughput for blockchain to cope with complex scenarios.

The above is an introduction of Stabila Virtual Machine and a guide to deployment. We welcome everyone to check out SVM and give us your thoughts and suggestions. We will continue to perfect and update SVM for optimal performance on STABILA mainnet.
