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
wget https://github.com/Beeppool/miner/releases/download/0.6.0/beepminer-0.6.0.zip
unzip beepminer-0.6.0.zip
cd beepminer-0.6.0
```

After that you are ready to mine. Start the miner using `./miner --wallet-address='NQXX XXXX ...'`

It will automaticly establish consensus and start solo mining. It is also possible to adjust a bunch of settings by appending additional command line flags.

Command line flag | Description
------------ | -------------
`--miner=<threads>` | Number of threads used for mining
`--type=dumb|nano|light|full` | Choose the consensus type. `nano` and `dumb` mode require a pool connection.
`--pool=<url>:<port>` | Connect to a pool using the given URL and Port. You can usually find these values on the pool main page
`--pool=<name>` | Connect to a pool by name, supported pools: `icemining`, `nimiqpocket`, `nimiqwatch`, `nimpool`, `skypool`, `siriuspool`, `sushipool`
`--region=<region>` | Use the pool server for this region if available, supported regions: `EU`,  `AF`,  `NA`,  `SA`,  `AS`,  `OC`
`--deviceLabel=<name>` | Name for this miner, usually visible in the pool statistics
`--in-memory` | Store consensus database in memory
`--architecture=<name>` | Force the usage of a specific architecture
`--protocol=dumb\|ws\|wss` | Choose how your miner connects to the NIMIQ network. If you are using a public reachable server or can modify your router/firewall settings you may consider using ws or wss. That way other servers can connect to your miner and improve your conection to the NIMIQ network. If you own a domain you can even activate wss to secure the connection. Defaults to dumb.
`--host=<name>` | IP Address or domain name, only required if you use ws or wss as protocol
`--port=<port>` | Port used for connections, only required if you use ws or wss as protocol
`--cert=<path>` | Path to the certificate file, only required if you use wss as protocol
`--key=<path>` | Path to the private key file, only required if you use wss as protocol

# Client/Server mining

Since version 0.6.0 it is possible to split up the consensus server and the actual mining process. This is especially usefull if you have a biger amount of servers in the same network. 

## Server config

Start the miner using `--workserver`. That way it doesn't start mining on this machine. To enable connections from other machines you have to authorize the ip/network using `--workerip=<ip>/<subnetmask>` e.g. `--workerip=192.168.1.0/24`.

## Client config

The subfolder `lib` contains the precompiled binarys for all supported cpu architectures. Choose the one that fits your cpu. 

```
OPTIONS:
    -b, --batch_size <batch_size>      Set the batch size [default: 1024]
    -r, --rpc <rpc>                    Set the JSON-RPC server [default: http://127.0.0.1:28648/]
    -s, --start_nonce <start_nonce>    Set the minimal nonce that should be tried [default: 0]
    -t, --threads <threads>            Set how many threads get used
```

If multiple clients connect to the same server, make sure that to set `--start_nonce` to seperate the region each client works on. For example in a setup with 100kh/s per client, `--start_nonce` should be incereased by ~60000000 (100000(kh/s) * 60(seconds per minute) * 10(max block time)) for each individual client.

# Download

The latest version can be found on the [release page](https://github.com/Beeppool/miner/releases/)
