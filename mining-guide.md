# XeChain Mining Guide

This guide covers both **solo mining** and **pool mining** for XeChain. You can either compile the miner from source or download pre-built binaries from the [xeMiner repository](https://github.com/XeChain/xeMiner).

---

## 1. Prerequisites

1. **XeChain Node**  
   - You must have a running XeChain node for **solo mining**.  
   - Refer to the [XeChain Node Setup](https://github.com/XeChain/docs/blob/main/node-setup.md) guide to compile or download the latest node binary.
   
2. **xeMiner**  
   - Clone and compile, or download the pre-built miner from:  
     [XeChain/xeMiner](https://github.com/XeChain/xeMiner)
   - Ensure it is properly installed and executable.

---

## 2. Solo Mining Setup

Solo mining means your XeChain node will generate new blocks with your miner.  

1. **Start the XeChain node with WebSocket and mining APIs enabled**  
   ```bash
   ./xe --ws --ws.port 8546 --ws.api admin,personal,eth,net,web3,miner --mine --miner.etherbase 0xYourWalletAddress
   ```
   - `--ws` enables WebSocket connections.
   - `--ws.port 8546` sets the WebSocket port (you can pick another port if needed).
   - `--ws.api admin,personal,eth,net,web3,miner` enables the relevant APIs for mining.
   - `--mine` enables mining on node.
   - `--miner.etherbase 0xYourWalletAddress` sets the payout address (mining rewards go here).

2. **Run the miner against your local node**  
   ```bash
   ./xeMiner -user=username -pass=password -pool=ws://localhost:8546
   ```
   - `-user` and `-pass` can be any username/password you want.  
   - `-pool=ws://localhost:8546` tells `xeMiner` to use your local XeChain node via the WebSocket connection.
   - The mining rewards will be sent to the address specified by `--miner.etherbase`.

---

## 3. Pool Mining Setup

For pool mining, you connect your miner to a remote pool instead of running your own node:

```bash
./xeMiner -user=username -pass=password -pool=stratum://pool_address
```

- Replace `pool_address` with the actual pool’s endpoint.
- Your `-user` is typically your wallet address or account on the pool (depending on the pool’s instructions).
- `-pass` is often arbitrary (or the pool-specific password).

---

## 4. Troubleshooting

- **Miner cannot connect**  
  - Check that your node is running with the correct WebSocket port and APIs enabled.  
  - For pool mining, verify that the pool endpoint (`stratum://pool_address`) is valid and that your username/password matches pool requirements.

- **Insufficient balance or zero mining reward**  
  - Make sure your `--miner.etherbase` address is correct and belongs to you (for solo mining).
  - Verify that your local node is fully synced with the network.

---

## 5. Additional Resources

- [xeMiner GitHub Repository](https://github.com/XeChain/xeMiner)
- [XeChain GitHub Repository](https://github.com/XeChain/xe-core)
- [XeChain Official Website](https://xechain.org/)  

Happy Mining!
