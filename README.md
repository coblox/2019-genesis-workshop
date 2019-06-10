# 2019-genesis-workshop

Welcome to the workshop!

In the instructions below, if nothing is specified for your system (Mac/Ubuntu) then you skip the step.

# Slack channel

1. Go to #coblox-workshop
2. The url of the repo in the Slack channel topic, clone it: `git clone https://github.com/coblox/2019-genesis-workshop`

## Tooling

Please install the following tools: 
1. Brew:
   - Mac: `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
2. Docker
   - Mac: https://download.docker.com/mac/beta/Docker.dmg or `brew cask install docker`
   - Ubuntu: https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-using-the-repository
3. Build tools:
   - Ubuntu: `apt-get install build-essential`
4. rustup (Mac & Ubuntu)
   - `curl https://sh.rustup.rs -sSf | sh`
   - Nix:
     - try `nix-shell -p rustup`
     - OR enter this into a terminal if nix is giving you trouble: `nix-env -e '.*'` you will need to reinstall the toolchain afterward and uninstall rustup
     - or need to set `LIBRARY_PATH` to include `zeromq` derivation and `OPENSSL_DIR` to include `staticSupport.openssl` from `tenx-dev`
5. libzmq:
   - Ubuntu/Debian: `apt install libzmq3-dev`
   - Mac ([Homebrew](https://brew.sh/)) `brew install zeromq`
6. OpenSSL:
   - Ubuntu/Debian: `apt install libssl-dev pkg-config`
7. Source profile to add `cargo` to `$PATH`: `source ~/.profile`

## COMIT Setup
1. Clone comit-rs repo: `git clone https://github.com/comit-network/comit-rs.git && cd comit-rs`
2. Install:
   - `cargo install --path application/comit_node`
   - `cargo install --path application/btsieve`

## Bitcoin setup
1. Navigate to the `2019-genesis-workshop` folder
2. In `docker-compose.yml`, replace `BITCOIN_NODE_IP_PORT` with the Bitcoin Node IP:PORT from the Slack channel topic 
3. Start the Bitcoin node from the workshop folder: `docker-compose up`

## Ethereum setup
1. Install metamask: https://metamask.io/
2. Setup Metamask by following the wizard (new wallet). Yes, you have to do the seed phrase thing.
3. Connect metamask to our Ethereum node:
  - Choose "Custom RPC"
    
    ![connect Ethereum](./img/eth_connect.png)
    
  - Network Name: "CoBloX Test"
  - New RPC URL: Ethereum URL from the Slack channel topic
  - Leave the rest empty
4. Paste your address in the Slack channel with "Fund me please"

  ![copy address](./img/eth_copy_address.png)
  
  
## Resume COMIT setup
1. In the `btsieve.toml` file, replace `REPLACE_THIS_ETHEREUM_NODE_URL` with the Ethereum URL from the Slack channel topic
2. Start btsieve: `btsieve --config ./btsieve.toml` 
3. Start comit_node: `comit_node`, this will generate a config file
4. Kill comit_node: `pkill comit_node` or `CTRL+C`
5. In `~/.config/comit/comit_node.toml`, update both `poll_interval_secs` to `2` (seconds).
6. Start comit_node again: `comit_node`
7. Go to http://localhost:8080
8. Accept to register comit links with COMIT-I (notification in your browser)

## Do a Swap!
Start by buying Bitcoin with Ether from our bobtimus (click the link in the chat).

To do Ethereum actions: use Metamask. Fund only ONCE.

To do Bitcoin actions you need to use the commandline:
- `alias btc-cli='docker exec 2019-genesis-workshop_bitcoind_1 bitcoin-cli -regtest'`
    - Redeeming:
        - Get an address from your wallet (to redeem): `btc-cli getnewaddress`
        - Use the returned address and `20` for fees to create the transaction in the browser
        - Broadcast the transaction: `btc-cli sendrawtransaction <transaction hex>`
    - Funding:
        - `btc-cli sendtoaddress "address" amount`

Start by buying Bitcoin with Ether from our bobtimus (click the link in the chat).
