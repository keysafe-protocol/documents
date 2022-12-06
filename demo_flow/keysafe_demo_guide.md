This is the guidance for the users to walk through the [demo DApp of Keysafe](https://keysafe-front-keysafe.vercel.app/#/).

## Main features

### 1. Login
Go to [demo DApp of Keysafe](https://keysafe-front-keysafe.vercel.app/#/) and input an email you are using.

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/enter.png?raw=true)

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/login.png?raw=true)

### 2. Register

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/register1.png?raw=true)

__2.1 Import Keys__

You need to import your Web3 accounts of specified networks and input private keys or seeds.

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/register2.png?raw=true)

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/register3.png?raw=true)

__2.1 Set authentication methods__

Register your authentication methods such as passphrases, Email, and Github. The private segments will be generated from the given private key in triplicate by the BLS algorithm. Each authentication method will be bound with a segment, which makes you can control your Web3 account via these authentication methods.

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/register4.png?raw=true)

Click each "Set" button to set different authentication methods.

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/register5.png?raw=true)

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/register6.png?raw=true)

Click "Submit" when each method is set up successfully. We will go to the home page of the Dapp.

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/regsiter7.png?raw=true)

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/home.png?raw=true)

### 3. Key Recovery

If you want to recover any account from Keysafe, you could click the one listed on the home page, and click the "Recover" button, then click "Confirm". You will need to go through 2 of 3 authentication methods that you have set during the registration.

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/recovery1.png?raw=true)

Click each "Retrieve" button and go through them.

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/recovery2.png?raw=true)

Once 2 of 3 authentications are done, the "Submit" button will be clickable.

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/recovery3.png?raw=true)

Go ahead and "Submit" the authentication and export your private key from the security enclave of Keysafe Network.

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/recovery4.png?raw=true)

### 4. Make Transfer

Click the sender account listed on the home page and click the "Make Transfer" button. Input the receiver address and the transfer amount, then click "Confirm".

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/transfer1.png?raw=true)

The signature generation process is the same as the recovery process, you need to go through 2 of 3 authentication methods as well.

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/transfer2.png?raw=true)

Once you have done, you will receive two BLS signatures, when you click the "Submit" button, the valid signature will be calculated and sent out.

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/transfer3.png?raw=true)

You can check the transaction in blockchain explorer accordingly.

![](https://github.com/keysafe-protocol/documents/blob/main/demo_flow/transfer4.png?raw=true)
