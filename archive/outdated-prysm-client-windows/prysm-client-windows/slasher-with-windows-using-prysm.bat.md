# Slasher with Windows using prysm.bat

## General

The slasher's purpose is to find malicious validators **in the Ethereum 2.0 network** and report slashable offenses to the beacon-node.\


![](<../../../.gitbook/assets/image (69).png>)

####

## How does the slasher work?

The **slasher is its own entity** but requires a beacon-node to receive attestations.\
To find malicious activity by validators, the slashers iterates through all received attestations until a **slashable offense** is found. Found slashings are broadcasted to the network and the next block proposer adds the proof to the block. The block proposer get the reward for slashing - not the whistleblower(=Slasher).

## Run a slasher&#x20;

Make sure your **beacon-node** is **in sync**. \
If you need to run a beacon-node and validator, [here is a guide for Windows](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client/windows-prysm/script-beaconnode-and-validator) and [here for macOS](https://kb.beaconcha.in/tutorial-eth2-multiclient/prysm-client/macos-prysm/run-with-macos-using-prysm.sh).

#### &#x20;**Step 1.**

Drag and drop the **prysm.bat** file into the **Terminal** window and add:

`slasher  --datadir=$HOME/prysm`

![](../../../.gitbook/assets/slashergif.gif)



**That's it!**\
The slasher now iterates through all attestations and sends proof to the detection service. \
\
Debug mode enabled with `--verbosity=debug`

For **selfish** slashing, add `--disable-broadcast-slashings` to the beaconnode.\


![](<../../../.gitbook/assets/image (71).png>)
