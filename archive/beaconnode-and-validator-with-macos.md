---
description: Altona Testnet
---

# Medalla Testnet: Lighthouse Client - macOS

[Official Lighthouse docs\
](https://lighthouse-book.sigmaprime.io/become-a-validator-source.html)[Lighthouse Discord server](https://discord.gg/8mFMS7G)

#### Requirements: A synced Goerli node ([Guide](https://kb.beaconcha.in/run-a-goerli-node-eth1-and-beaconnode-eth2#step-1) till step 3.)

####

#### 1. Step&#x20;

#### Installing Rust

Open a terminal window and paste the following in:

`curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`

_"Current installation options"_\
__Press **"1"** and confirm with Enter.

![](<../.gitbook/assets/image (130).png>)

_"Next time you log in this will be done automatically"_\
__**Close** this terminal window and **open a new one.**

#### 2. Downloading and building Lighthouse

`git clone https://github.com/sigp/lighthouse.git`\
`cd lighthouse`

and then run `make`

![](<../.gitbook/assets/image (133).png>)

_Wait a few minutes_\
__Once the process is done it will look like the following

![](<../.gitbook/assets/image (128).png>)

#### 3. Find the binary file

Open **Finder** and head over to `~/.cargo/bin/`

![](<../.gitbook/assets/image (132).png>)

**Copy** the Lighthouse file to a more convenient folder.

#### 4. Start the beaconnode

_Make sure the goerli node (ETH1) is running as mentioned in the_ [_requirements_](https://kb.beaconcha.in/archive/outdated-lighthouse-client-guides/beaconnode-and-validator-with-macos#requirements-a-synced-goerli-node-guide-till-step-3)_._

Drag and drop the **Lighthouse** file and add `--testnet medalla beacon --eth1 --http --graffiti "beaconcha.in<3"`&#x20;

![](<../.gitbook/assets/image (160).png>)

#### 5. Create ETH2 Wallet

_**Lighthouse** allows you to create an ETH2 wallet and attach your validator keys._

Open a new Terminal window, drag and drop the Lighthouse file and **add**\
`account wallet create --name my-validators --passphrase-file my-validators.pass`

**The 12 word mnemonic phrase can restore the ETH2 wallet - write the words down.**

![](<../.gitbook/assets/image (134).png>)

The wallet is located in `$HOME/lighthouse`

![](<../.gitbook/assets/image (123).png>)

#### 6. Create ETH2 Keys

Use the same Terminal window, drag and drop the Lighthouse file and **add** \
****`lighthouse account validator create --wallet-name my-validators --wallet-passphrase my-validators.pass --count 1`

![](<../.gitbook/assets/image (131).png>)

#### 7. Depositing to Ethereum 2.0

First, find the deposit data of the newly created ETH2 Key , which is located in `.lighthouse/validators/` \
\
There are two lighthouse folders, `.lighthouse` is a hidden folder.\
**Enable hidden folders with** **`CMD + Shift + .`**

Open the `eth1-deposit-data.rlp` file with a **text editor.** \
**Copy** the 842 long text sequence and **follow these** [**steps**](https://kb.beaconcha.in/ethereum-2.0-and-depositing-process/depositing-to-ethereum-2.0#depositing)**.**\
****\
**Medalla Deposit contract address:** `0x07b39F4fDE4A38bACe212b546dAc87C58DfE3fDC`

The deposit will be recognised by the beacon-chain in 8.5 hours.

![](<../.gitbook/assets/image (127).png>)



#### 8. Starting the validator

Open a new terminal window, drag and drop the **Lighthouse** file and add `validator --auto-register`

In total there are **three** terminal windows running simultaneously! \
[Track](https://altona.beaconcha.in/dashboard?validators=) your validator performance.

![](<../.gitbook/assets/image (122).png>)





