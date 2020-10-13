# Open Grant Proposal

* **Project:** `Ares`
* **Proposer:** [jiyilanzhou](https://github.com/jiyilanzhou)
* **Payment Address:**  bc1qzv5ljrt0sngjjnn25s4jzsu7qtts5d74cq8tz5

## Project Overview :page_facing_up:

Ares is a predictive machine project based on Substrate, with the objective of providing safe and credible under chain real data use a decentralized approach for smart contracts, parallel chains or other projects in the ecosystem of the Polkadot.

It is a decentralized oracle network that consists of Ares oracle Module, it makes full use of the off-chain worker, sources aggregator committee random mine block and reputation council.

### Overview

**Ares** consists of consumers, sources aggregator, and validators of the data. The consumer requests the data via extrinsic with rpc method or off-chain worker if we become a parallel chain, If we become an application on a parallel chain of contracts, it provides a pallet for The caller, The result of the request passed to the caller through a callback, Aggregators randomly selected through VRF, which aggregates data from multiple sources.

Aggregator needs to pledge certain assets, Every time the aggregator submits a correct data, its reputation value will grow. The reputation value and pledge will be weighted, from which we choose the members of council. council can only approve and reject data submitted by data aggregator. 
The default is to approve, and if the data found incorrect, the author will be slashed and its reputation will be degraded.

The functions of aggregator committees are similar with Babe, and reputation council are similar with Grandpa which finality the correctness of the data. Most nodes can become member of aggregators committees. It only takes few tokens to staking.

### Project Details

**Ares** is designed as decentralized oracle network. First of all, `Ares` will provide  basic `ares` pallet runtime which allows substrate built parachain/blockchain to interact with.

* define `ares Trait` which contain Event, Callback.
* define storage operator, request, result and error types
* request external data, contains parameters and methods for how to request them.
* describes how to integrate into parachain.
* aggregator scans the extrinsic in the block, requests the data, and submits it
* reputation council submit proof of fraud if it validates fails.

If basic functions have been completed, `Ares` will provide decentralized pallet, including:

* Multiple data source weight calculation
* Random aggregators using VRF 
* Proof of fraud based on BFT voting
* reputation council slash

### Ecosystem Fit

Although Off-chain worker can do part of the oracle job, However, it can't guarantee the authenticity and reliability of the data, We can provide randomness and correctness of data sources through multi-party data aggregation and provides anti-attack and auditing of data sources

## Team :busts_in_silhouette:

### Team members

* Keric: 7+ years development experience, proficient in public chain and cross chain development, proficient in using go and rust, p2p network expert.
* Daniel: 11 years of work experience in IoT software development and management, familiar with contract and DAPP development.
* Scott: More than 7 years of software development experience, proficient in /Java/Golang/node, etc. engaged in blockchain research and development, familiar with eos/eth.
* Andy Ray: 10 years of Internet entrepreneurship experience, 5 years of blockchain industry experience, proficient in the secondary market, economic model design.
* Fred: Over 13+ years of Embedded Network Technology Experience in multiple technological systems including Hardware networking, software networking, and server-side applications.

### Team's experience

We implemented the POW + DPOS consensus integrated with ethereum, used tendermint to provide finalize in blockchain system with golang. Recently, we implemented a rust pos blockchain, it  uses vrf select validators and libp2p network. We have enough experience to solve the centralization problem of Oracle.                                                                                                                                                                                                                                           

### Team Code Repos
* https://github.com/aresprotocols/ares

## Development Roadmap :nut_and_bolt:

We only provide **milestone1**  here for centralized oracle implementation. Full milestones are list in the [Project Details](#Project Details)

### Overview
* **Total Estimated Duration:** 2 month
* **Full-time equivalent (FTE):**  2
* **Total Costs:** 2 btc

### Milestone 1  — Implement ares low pallet
* **Estimated Duration:** 2 month
* **FTE:**  2
* **Costs:** 2 btc

In this milestone, all the basic substrate contract runtime api will be implemented in AssemblyScript. This stage will deliver a AssemblyScript package which provide encapsulation of current substrate contract api. With the AS api, contracts can be compiled to wasm and deployed on substrate contract node. We may benefit from the reference implemention of parity Ink and provide similar api.

The AS package will cover the following substrate contract api:

| Number | Deliverable | Specification |
| ------------- | ------------- | ------------- |
| 0a. | License | Apache 2.0 |
| 0b. | Testing | This milestone will have unit-test for all the following runtime api impemented. We will mock most of the contract runtime api to simulate host functions. Integration test will be delivered in next milestone. |
| 0c. | Documentation | We will provide both inline documentation of all the sdk api and  basic code example that show how developers use the api. |
| 1. | contract runtime environment | contract builder and execution to initailize the contract code |
| 2. | core types | add core component: AccountId, Balance, Hash, Block |
| 2. | storage access | contract low level storage read and write with key |
| 3. | object packing utilty | Provide user-defined data structure packing and unpacking method to storage access. |
| 4. | memory manipulation | Implement memory make and getter, setter |
| 5. | contract event generation | Generate event from contract call |
| 6. | contract call method | Provide method for make contract call. |
| 7. | hash utility | Make digest of encoded input to generate hash image |
| 8. | `SCALE` codec | Builtin codec functions to serialize and deserialize input. We may directly use LimeChain `as-scale-codec` implementation. |
| 9. | example for demonstration | Provide  ERC20 contract example to test on substrate node |

## Future Plans

After the `Subscript` presentation , we may make our effort to bring more  tool for contract development.

A simulated contract sandbox similar to ganache is needed to debug and test contract.

We may add more intergated tool and IDE packge for contract developer.

## Additional Information

We expect any developer who is interested in `ares protocol` join us and build efficient framework.