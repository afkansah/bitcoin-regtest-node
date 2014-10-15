# Bitcoin Regtest Environment #

This repository contains instructions, with related helper code, that allows you
to run your own blockchain locally. Get started pretty fast and develop your
own Bitcoin application.

### Why this project?

This collection of instructions, with related scripts, should help Bitcoin
application developers. Instead of spending hours with setting up a testing
environment, the developer can focus on her application. The created environment
allows the complete testing of the Bitcoin part, without spending real money or
delays. The environment is reproducible and different scenarios, e.g. collection
of transactions in a predefined order, can be created, but also deleted again.

In comparison with the testnet3 Bitcoin network, this environment is not
dependent on external nodes. All happens locally and could be fully controlled
by the developer.

### Who should use this project?

* **Bitcoin Application Develpers:** The main target audience are developers
that need a deterministic and reproducible environment for Bitcoin application
development and testing.
* **People interested in how the Bitcoin blockchain works:** By running a
complete blockchain locally, it is easy to play around with different scenarios
and multiple nodes. It is not only a lot of fun, to play around with an own
blockchain, but improves the understanding of how a decentralized ledger works.

## Getting Started ##

### Quickstart ###

*TODO: Add helper scripts and explain here to execute them and in what order.*

### Manual Installation ###

Installation of the official bitcoin core implementation from
https://bitcoin.org/en/download

    ~$ BITCOIN_VERSION=0.9.3 # You may want to change this value to the current version.
    ~$ wget https://bitcoin.org/bin/${BITCOIN_VERSION}/bitcoin-${BITCOIN_VERSION}-linux.tar.gz
    ~$ tar xf bitcoin-${BITCOIN_VERSION}-linux.tar.gz
    # Change 64 to 32 for 32bit architecture
    ~$ mv bitcoin-${BITCOIN_VERSION}-linux/bin/64/* /usr/local/bin

### Get your first Bitcoin ###

    # For testing purpose we want verbose output
    ~$ bitcoind -regtest -printtoconsole
    ...

Switch to new console and let the bitcoind running. We generate 101 new blocks
(starting from the genesis block), in order to be able to access the first one
and get 50 BTC.

    ~$ bitcoind -regtest setgenerate 101
    ... # Wait until all blocks are generated, ~1 minute
    ~$ bitcoind -regtest getbalance
    50.00000000 # <= You should see that or at least a number bigger then zero.

**Congratulations!** You have now your first BTC that you can spent.

Where to go from here? Please read further how to spent this BTC and how to make
 the whole a little bit more effective, with less typing and more automated.

### Preparing your working environment ###

    # We don't want to type each time `bitcoind -regtest`.
    # The command `br` is easier to type and easy to remember (the beginning letters of the command).
    ~$ echo 'alias br="bitcoind -regtest"' >> ~/.bashrc; source ~/.bashrc


## TODO ##

* [AUTOMATION] Provide scripts that automate the whole node setup and spending
process, e.g.by simulated random transfers.
* [FEATURE] Explain how the blockchain could be stored in a SQL database and
accessed via your application.
* [PORTABILITY] Describe how the node can be virtualized with vagrant or docker.
Provide also the related scripts and configuration files.
* [SECURITY] Add the signature file, of bitcoin-core, to this repository and
explain how to check it.

## Screenshots ##

The script, that produces the following output, will be provided shortly. It
shutdowns a previous running bitcoind instance, deletes the old regtest
blockchain, creates a new one and mines 101 blocks, in order to get 50 BTC.

<img src="https://raw.githubusercontent.com/Sigimera/bitcoin-regtest-node/master/screenshots/script_fresh_regtest_start.png">

## Support this project ##

Please help us to extend and improve this project.

1. Fork it!
2. Make your changes.
3. Create a pull request.


Alternatively you can also donate, if you want to motivate us to improve this
project even further.

[1LKzkn4CfktnSXDMNt856KqHcjMdTCp57S](bitcoin:1LKzkn4CfktnSXDMNt856KqHcjMdTCp57S?label=bitcoin-regtest-node)<br/>
If clicking on the line above does not work, use this payment info:<br/>
**Pay to:**  `1LKzkn4CfktnSXDMNt856KqHcjMdTCp57S` <br/>
**Message:** Donation for bitcoin-regtest-node open source project.
