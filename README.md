# Athereum: Ethereum-on-AVA

![](Untitled-277509de-7383-4113-a34e-768feee3b381.png)

The AVA Network can lend its consensus network to any number of decentralized platforms. To demonstrate this, we have created an early-stage deployment of the Ethereum network. We have deployed a very small 25-node AVA network, where we have deployed Athereum as a subnetwork. 

There is an open RPC connection available with all ETH JSON-RPC calls available. This guide shows you how to access this demo RPC and interact with a demo contract we have deployed to confirm operation. The demo contract is a simple lottery, where you register ("buy" a ticket) with your pubkey, and at the end the winner is selected "randomly" (i.e., we just manually pick one at random). Yes, kinda janky, but it's just here to demonstrate a point. 

If you want to view the contract itself, go [here](https://gist.github.com/StephenButtolph/732f30185fd97b026b53837c8f8042b1#file-registry-sol). *This contract is meant to be simple, not secure, so funds are not #SAFU. Or real, for that matter. Again, this is just a test :)* 

# Requirements

We will be interacting with the contract using MyEtherWallet. You will need a private key to interact with the demo contract. We suggest using a randomly generated private key. You can obtain such a key from [https://vanity-eth.tk/](https://vanity-eth.tk/) by clicking the `Generate` button at the bottom of the page. After that, click `Private key: Click to reveal` and store your private key for later. **You should not use your own private key or Ethereum Keyfile for security reasons.**

![](MEW8-17769535-809d-4af2-8881-f70c36cf2e47.png)

# Creating Your MEW Wallet

To start, go to [https://www.myetherwallet.com/](https://www.myetherwallet.com/)

- [ ]  Visit [https://www.myetherwallet.com/](https://www.myetherwallet.com/)
- [ ]  Click the button that says "`Onwards!`"

![](MEW1-73f1c653-6a38-4858-abd0-5db9fd82a9ab.png)

- [ ]  Select the box that says, "`Access My Wallet`"

![](MEW4-5547c34d-0abf-41a4-bbf5-7c7d9c927c2e.png)

- [ ]  Four options will appear, select the "`Software`" option.

![](MEW5-5a91fa93-0fe4-4257-b6a4-9bb2740b3c28.png)

- [ ]  In the following window, you can choose either a Keystore File, Mnemonic Phrase, or Private Key. For this demonstration, use the Private Key generated in the **Requirements** section of these instructions. Select the "`Private Key`" option and hit the "`Continue`" button.

![](MEW6-1490a817-3f84-4218-8eb2-3c71dc9c18eb.png)

- [ ]  Paste your **newly generated** private key into the input box and press "`Access Wallet`".

![](MEW7-b1f5d26c-9289-4e7f-8c59-f610b46cb8f7.png)

- [ ]  You should now have a MEW Wallet! You will see your address, your balance, and your network. The next section describes how to connect to our Athereum demo network.

# Connecting to Athereum

Using the MEW Wallet you created in the **Creating Your MEW Wallet** section, do the following steps to connect to Athereum.

- [ ]  In the Light-Blue box on the far-right labeled "`Network`", click the "`Change`" button.

![](MEW9-ca51e026-12e0-4fcd-be2f-c905608e6897.png)

- [ ]  In the following screen, toggle the "`Add Custom Network/Node`" button.

![](MEW10-9b0206c0-fe90-400e-8d9b-224867079768.png)

- [ ]  An "`Advanced`" window will come up asking for the information about the custom network.  It should appear as follows.

![](MEW11-07c81eb2-dc10-429d-ab60-071cc737f797.png)

- [ ]  The default option is the Ethereum Mainnet. Switch that to the "`CUS - CUSTOM`" option at the very bottom of the drop down pictured below.

    ![](MEW13-75a2752f-b08a-4d70-bbfe-610399fabe28.png)

- [ ]  Fill in the fields as in the following picture, with `Port 443`, `ChainID 43110`, `URL https://ava.network/ext/evm/rpc`, `ExplorerTx http://ava.network:21005/tx/[[txHash]]`, and `ExplorerAddress http://ava.network:21005/address/[[address]]`. Then click "`Save`".

![](MEW13-2-1d3ece70-6d44-4c89-80b6-1214ae9402c7.png)

- [ ]  Scroll to the bottom of the Networks window and select "`AVA ETH 1 (CUS)`" under the "`Custom Networks`" heading by clicking on its name.

![](MEW14-1277dbf0-85f3-4630-a2f6-1d83d784d319.png)

- [ ]  You should see the following in your wallet's "`Network`" box when complete (your Last Block# will vary).

![](MEW15-5d34a9c1-77eb-4568-93c6-37f175ffa3bc.png)

# Interacting With The Contract

We're ready to begin interacting with the smart contract through our Wallet.

- [ ]  In the MEW sidebar on the left of your desktop wallet, expand the "Contract" menu option and click "`Interact with Contract`"

![](MEW16-5b4af96e-aad2-4224-ad77-3bca634a1561.png)

- [ ]  Fill out the "`Contract Address`" field to read "`0x045Fa33657bc06DB351915C9C1c0f37348F7Ae26`" and the "`ABI/JSON Interface`" to have the following value:

[https://gist.github.com/collincusce/d0fe8cea9223bf3ab67a1914173a1e34](https://gist.github.com/collincusce/d0fe8cea9223bf3ab67a1914173a1e34)

- [ ]  Press "`Continue`" to interact with the contract.

    ![](MEW17-11bb18f1-f8bb-44cd-b380-c4f0e977c404.png)

    - [ ]  Select the "`getSize`" function from the drop down on the right.

    ![](MEW20-37592c14-9b2b-430e-9951-75582c9941c5.png)

    - [ ]  This calls the "`getSize()`" function in the contract and displays its results. Make note of the "`Result`" value that appears after selecting the function. That number should be strictly increasing as people use the contract.

    ![](MEW21-6b8c7954-672b-4aa1-89f0-c6536afde9e2.png)

    - [ ]  Now select the "`register`" function from the dropdown on the right.

    ![](MEW18-69851366-a3ae-47ca-9310-66378b8fa1e7.png)

    - [ ]  Leave the fields as-is and press the "`Write`" button to register your address with the contract. *Note: You may only register once per address.*

    ![](MEW19-6c35b1a1-05a6-4b6f-8bc7-3c05047fb7fb.png)

    - [ ]  On the following screens, press the "`Confirm and Send`" button followed by the "Okay" button.

    ![](MEW22-8569debd-5fda-45a0-ab0c-9d0cfb17c859.png)

    ![](MEW23-3555fc2d-0224-4abd-9d4e-2dbccd15f2d2.png)

    - [ ]  Select "`getSize`" again, and you should see that the "`Result`" value has increased. If multiple people are using the contract, it should increase by the number of newly registered participants.

    ![](MEW24-a41f1e27-607d-4bc2-9cf0-576dda219047.png)

    # Congratulations!

    You are now able to interact with the Athereum demo network. You can deploy and interact with contracts just as you would using Ethereum mainnet. There are some additional caveats: AVA has sub-second finality, so blocks will be produced exceptionally fast. If your system depends on a certain blocktime, it will need to be adjusted for this new-found speed. In addition, AVA does not require confirmations as part of its protocol. If your system waits for confirmations, it no longer needs to, as this version of Ethereum does not use Longest-Chain Consensus. Lastly, this is a test network using the AVA Alpha Client, not yet publicly released. Connecting unmodified `geth` nodes will not produce the expected behavior. There is no warranty of availability. This system has yet to undergo full hardening. If you see something, say something by sending an email to contact@avalabs.org.

    Enjoy! 

    - AVA Team <3
