---
description: Beacon Fuzzer guide for macOS users.
---

# Fuzzing on macOS

### General

#### [_**Fuzzing**_](https://en.wikipedia.org/wiki/Fuzzing) _or **fuzz testing** is an automated software testing technique that involves providing invalid, unexpected, or random data as inputs to a computer program._

* [https://github.com/sigp/beacon-fuzz](https://github.com/sigp/beacon-fuzz)
* [Lighthouse Discord Channel](https://discord.gg/Xdc9xZX)

#### Requirements

* [Install Docker](https://docs.docker.com/docker-for-mac/install/)
* 8-16 GB RAM&#x20;
* 2-4 Core CPU

#### Configure Docker file sharing settings

Make sure that the paths  `/Users` , `/Volumes` , `/private` ,  `/tmp` have been entered.

![](<../../.gitbook/assets/image (137).png>)

### Fuzzing

#### Step 0.&#x20;

Open up a **Terminal** and test if docker is up and running `docker -v`

![](<../../.gitbook/assets/image (142).png>)

**Step 1.**\
\
Clone the repository `git clone https://github.com/sigp/beacon-fuzz`

#### Step 2.

Change your directory `cd beacon-fuzz/eth2fuzz`

#### Step 3.&#x20;

Build **all** Ethereum 2.0 client docker containers `make fuzz-all`\
This process can take up to one hour.

![](<../../.gitbook/assets/image (143).png>)

Once the building process is done, the Fuzzer will start by fuzzing the Lighthouse client and fuzz the next client after one hour. The total process takes 5hours.

![Fuzzing Lighthouse](<../../.gitbook/assets/image (144).png>)

### Report & find bugs

#### Step 0.

Open **Finder** and head over to its **Preferences**\
Change the search settings to **Search the Current Folder**

![](<../../.gitbook/assets/image (148).png>)

#### Step 1.

If the fuzzer finds a bug it creates a _**crash**_ _**file**_ in the workspace folder\
`~/beacon-fuzz/eth2fuzz/workspace`

![](<../../.gitbook/assets/image (145).png>)

####

#### Step 2.

Search the workspace folder for files called "_**crash-..."**_, which is the bug file and compress it to a **zip.file**\
An example:\
_`crash-efc8b3f0753ddd9df52b066d2f4549d548a21a58`_

Post the zip file on the beacon-fuzz [github repository](https://github.com/sigp/beacon-fuzz/issues/new/choose).

![](../../.gitbook/assets/crash5.gif)
