# Keysafe Introduction

## The background

Managing Web3 accounts could be cumbersome, unfriendly to users, and vulnerable to hacking. Based on research by ChainAnalysis, the number of lost bitcoins due to account loss reached 3.79 million($150 billion).

To use Web2 social login is user-friendly, but it is trust needed and is vulnerable to Web2 identity exposure.

![Root problem](https://github.com/keysafe-protocol/documents/blob/main/pictures/behind-problem.png?raw=true)

## What is Keysafe

Keysafe Protocol is a missing layer that connects users' Web2 and Web3 accounts in a decentralized, verifiable, and private way. With the connection, users can access their Web3 assets and Dapps through Web2 verification such as Google OAuth and Email verification.

![What is Keyafe](https://github.com/keysafe-protocol/documents/blob/main/pictures/solution.png?raw=true)

## Technical modules

### Unilogin

Unilogin is a SaaS solution based on Keysafe Network. It helps users to access their Web3 assets and Dapps through Web2 verification such as Google OAuth and Email verification.

Try it at https://unilogin-demo.vercel.app/#/login-home

### Keysafe Node

A Keysafe Node is the basic unit of the Keysafe network.  Keysafe network consisted of nodes from several institutions in its early stage.  In the future, the number of nodes will gradually expand with the increase in the security and stability of Keysafe Network.

### On-chian

Keysafe deployed smart contracts on several Blockchain ecosystems, such as Aptos, Near Polygon, Solana, and Near Networks. The contract provides the registration function of the Keysafe node that allows users to verify the environment of the service node and the service result.

### TEE

Keysafe protocol uses Trusted Execution Environment (TEE) technology to manage user private key segments. TEE is a hardware technology that is leveraged on each Keysafe node. The TEE protects the code Keysafe protocol from being tampered with by the node and ensures that the data in the TEE enclave is not stolen by the node.

__The Weaknesses of TEE technology__

TEE can ensure that its internal code works correctly, but there are still a few functions that TEE does not support. They are:

* Unable to initiate a network request
* Unable to access external storage
* Cannot verify the execution of code deployed outside of TEE

These restrictions make it impossible for TEE to verify a user's Web2.0 account identity directly. Imagine that a user's private key is stored in the TEE of a server named "Key Unsafe", and we want the user to be identified by verifying his Google account and then allowing him to invoke the private key to sign transactions. However, TEE cannot access the network, so even if the user passed the Google authentication through the OAuth, he only proves his identity to the "Key Unsafe" server, and The TEE determines whether to sign transactions only through the authentication result returned by the "Key Unsafe" server. In this mode, the TEE cannot determine whether the program outside the TEE, namely the "Key Unsafe" server, is honestly implementing the Google account verification and returning the correct result. In that case, the "Key Unsafe" server can launch a "man-in-the-middle attack" to steal the user's private key from TEE.

On the other hand, there are many physical attacks aimed at TEE directly, such as [voltpillager attack](https://zt-chen.github.io/voltpillager/)which makes it possible to break the security zone and steal private data that is protected by TEE.

### DAuth

To solve the problem that TEE can not directly initiate network calls, Keysafe created DAuth technology. DAuth rewrites the HTTPS protocol to split it into an HTTP part that is responsible for network traffic (running on top of the Node server, outside the TEE security zone) and an SSL part that is responsible for establishing the private channels (running inside the TEE security zone). This split and reconstruction allow the TEE to make HTTPS calls to external apps such as Google and Twitter through Node while ensuring that the Node cannot see the transmission of information between the TEE and the target App. 

![dauth](https://github.com/keysafe-protocol/documents/blob/main/pictures/dauth.png?raw=true)

### MPC and BLS

Keysafe introduced BLS and MPC technologies to defend against physical-based attacks on TEE. The users' private segments will be generated in triplicate by the BLS algorithm. At the time of registration, each BLS segment will be registered by the user through DAuth to specify an associated social account, such as GitHub or email, and stored in the TEE of different nodes. 

MPC technology provides the function that the three BLS segments are directly generated in different node TEE. This design makes it impossible for any node to get any useful information by attack
ing TEE in physical methods. In the meantime, the node will face penalties from the Keysafe contract and lose reputation and staking assets. Therefore, the cost of attack against TEE is huge and the benefit is 0, so the node has no motivation to attack the TEE.

## The attacks and security models

Keysafe proposes a Keyless user experience. Users do not have direct contact with Keys when using Keysafe to log in DApps and send transactions. In Keysafe, the attacks mainly come from: 

1. The hacker is the node itself and tries to attack its TEE; 
2. Hacker attacks users' Web2.0 accounts; 
3. Several Web2.0 companies misbehave together at the same time.

For attack 1: When a node attacks a TEE, the TEE would be provisioned or destroyed, which will feed back to the on-chain contract. The assets and reputation of the node are hit (Keysafe will be a super-node mode in the early stage), and since each account has only 1/3 of the Segment in the node, the benefit of the node launching an attack is zero and the cost is huge.

For attack 2: Web2.0 users and applications know how to protect these Web2.0 accounts, much more than they do in Web3.0. On the other hand, if a user's multiple major Web2.0 accounts are stolen, then his non-crypto assets and even his life and property have been seriously threatened, which is a threat beyond the Crypto things (such kind of threats also include kidnapping, restriction of personal freedom, etc.).

For attack3: Each account of a user is divided into three BLS segments, and each segment is associated with a Web2.0 authentication method and stored in a different node's TEE. A threat can be formed only when two Segments are simultaneously manipulated by attackers. However, any misbehaved Web2.0 server can only control one segment at most and have no impact on user accounts. 
ETH has a large number of nodes hosted in AWS, Azure, and other cloud services. Therefore, we consider a protocol that uses the services of multiple Web2.0 vendors is decentralized.

## The service modes of Unilogin

Unilogin will provide services in different forms for different customers. The main modes are as follows:

__Decentralized custody__

 In this mode, customers use the Unilogin SDK, and the user account is divided into three parts and saved in three different Keysafe nodes. The development costs are lower and it's easier for customers to integrate.

![Decentralized Custody](https://github.com/keysafe-protocol/documents/blob/main/pictures/decentralizedcustody.png?raw=true)

__Non-custody__

In this mode, the Customer will build a Keysafe Node by itself, and the three segments are respectively saved in Keyafe Network, Customer Node, and user Device.

![Non-Custody](https://github.com/keysafe-protocol/documents/blob/main/pictures/noncustody.png?raw=true)

__Customer custody__

Unilogin's customers also include asset hosting platforms that maintain their own clusters. DAuth technology can help these customers expand the way their users can control their assets and improve the usability and security of their systems. Such customers tend to prefer to use their clusters on which to deploy the Unilogin DAuth module.

![Customer Custody](https://github.com/keysafe-protocol/documents/blob/main/pictures/customercustody.png?raw=true)
