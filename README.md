# Keysafe Protocol

## What is Keysafe

Account systems in web2 and web3 are natively **separate**, technically **unconnected**, and even inherently in **conflict** with their values.

Problems follow as a consequence:

1. Managing Web3 accounts is particularly unfriendly, inconvenient and burdensome to normal users.
2. Web3 accounts are vulnerable to hacking and private key loss, both of which are hardly recoverable.
3. Web3 Dapps cannot access users' Web2 profiles and social links because of huge gaps between the two account systems.

![](https://res.cloudinary.com/devpost/image/fetch/s--VaLB3J_z--/c_limit,f_auto,fl_lossy,q_auto:eco,w_900/https://github.com/shuttle-protocol/documents/blob/main/problems.png%3Fraw%3Dtrue)

The Solution:

**Keysafe** is a decentralized protocol that focuses on connecting a user's Web2 accounts, along with implicit social links, to his or her Web3 accounts. Keysafe ensures that such connections will be built and maintained in a trustless, verifiable yet privacy-preserving way.

![](https://github.com/shuttle-protocol/documents/blob/main/twosides.png?raw=true)

## Core Technologies

* **Smart Contract**: This decentralized, trustless network are managed by Smart Contracts. Not a single entity will be capable of committing malicious attacks. The smart contract prototypes on each chain are under [this repo](https://github.com/shuttle-protocol/contracts).

* **Trusted Execution Environment**: TEE guarantees secrets and code to be protected with respect to confidentiality and integrity from a hardware level. Even the node runner cannot acquire any sensitive data from the network. Check the TEE code [here](https://github.com/shuttle-protocol/ks-sgx).

* **Secret Sharing Schemes & MPC**: Private keys and authentication data are split, encrypted and distributed into the network to ensure extra safety and robustness for users. Potential attacker need support from more than 2/3 of the network nodes. Check the secret sharing code [here](https://github.com/shuttle-protocol/keysafe-front).

* **Decentralized OAuth**: Decentralizes the conventional OAuth process inside TEE and builds connections between Web2 and Web3 accounts in a trustless, secure and private manner.

![](https://github.com/shuttle-protocol/documents/blob/main/DAuth.png?raw=true)

## Production Plan

### Decentralized Verifier (dVerifier)

In the first product phase, Keysafe will provide a light-weight decentralized social link verification service, **dVerifier**. 

Recently, Web3 projects, especially those with regards to Social Networks, DIDs, On-chain Credentials and Community/Marketing Campaigns, have seen growing needs to bring in users' Web2 accounts, i.e. Twitter, Github and Email, to their Web3 accounts. In such scenarios, users are risking exposing their privacy, on-line profiles and social links to many untrusted parties as well as giving away sovereignty and ownership of their valuable personal data.

This is a truly game changer to account verification, especially in cross-web scenarios. With Keysafe's **dVerifier**, users can have their social links verified by third parties even without trusting these third parties.

### Keysafe SDK

After **dVerifier** gains its momentums and accumumates greater user base, we will be rolling out a new module **Keysafe SDK**, tailored for Web3 Apps/Dapps with easy integration. This SDK would help Web3 Apps/Dapps to adopt **Social Login** feature. 

With **Keysafe SDK**, Apps/Dapps users will be able to log in to the application simply by anthenticating their Web2 accounts, i.e. Google accounts and emails, after they have binded their social links to Web3 accounts (which should be previously registered and verified through **dVerifier**).

### Web3 Portal

**Web3 Portal** will be an ultimate navigation panel for Web3 Dapps. It differentiate itself from other wallet or asset management tool's navigation menu in the sense that **Web3 Portal** will simpify user's private key management, which contributes to an economy of scale inherently from its user experience. 

With **Web3 Portal**, users will be able to gain access with their Web2 accounts to any DApps included in the navigation panel, in a wonderfully trustless and private manner. This solution addresses the big problem of private key management for 50 million new Web3 users every year and will act as one of the very first stop for these new users to enter the Web3 space.
