# Beepminer - NIMIQ CPU Miner

A precompiled NIMIQ Miner optimized for maximum hashrate 

# Features

* Highest hashrate for CPUs
* Pre-compiled for all architectures
* Support all pools based on the official pool protocol
* Fallbacks to solo mining if pool is down
* 0% fee

# Setup

Download the version and unzip it to any folder. Usually you can do that using these commands

```
wget https://github.com/Beeppool/miner/releases/download/0.5.0/beepminer-0.5.0.zip
unzip beepminer-0.5.0.zip
cd beepminer-0.5.0
```

After that you are ready to mine. Start the miner using `./miner --wallet-address='NQXX XXXX ...'`

It will automaticly establish consensus and start solo mining. It is also possible to adjust a bunch of settings by appending additional command line flags.

Command line flag | Description
------------ | -------------
`--miner=<threads>` | Number of threads used for mining
`--pool=<url>:<port>` | Connect to a pool using the given URL and Port. You can usually find these values on the pool main page
`--pool=<name>` | Connect to a pool by name, supported pools: `nimiqpocket`, `nimiqwatch`, `nimpool`, `skypool`, `siriuspool`, `sushipool`
`--region=<region>` | Use the pool server for this region if available, supported regions: `EU`,  `AF`,  `NA`,  `SA`,  `AS`,  `OC`
`--deviceLabel=<name>` | Name for this miner, usually visible in the pool statistics
`--in-memory` | Store consensus database in memory
`--architecture=<name>` | Force the usage of a specific architecture
`--protocol=dumb\|ws\|wss` | Choose how your miner connects to the NIMIQ network. If you are using a public reachable server or can modify your router/firewall settings you may consider using ws or wss. That way other servers can connect to your miner and improve your conection to the NIMIQ network. If you own a domain you can even activate wss to secure the connection. Defaults to dumb.
`--host=<name>` | IP Address or domain name, only required if you use ws or wss as protocol
`--port=<port>` | Port used for connections, only required if you use ws or wss as protocol
`--cert=<path>` | Path to the certificate file, only required if you use wss as protocol
`--key=<path>` | Path to the private key file, only required if you use wss as protocol

# Download

The latest version can be found on the [release page](https://github.com/Beeppool/miner/releases/)
