# 2019-genesis-workshop

Welcome to the workshop!

If there are no instruction for your system (Mac/Ubuntu) then there is nothing to be done.

# Slack channel

- Go to #coblox-workshop
Url to repo in the topic, clone it: `git clone https://github.com/coblox/2019-genesis-workshop`

## Tooling

1. Install Brew:
   - Mac: `/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"`
2. Docker
   - Mac: https://download.docker.com/mac/beta/Docker.dmg or `brew cask install docker`
   - Ubuntu: https://docs.docker.com/install/linux/docker-ce/ubuntu/#install-using-the-repository
3. Build tools:
   - Ubuntu: `apt-get install build-essential`
4. Install `rustup`: `curl https://sh.rustup.rs -sSf | sh`
5. Install libzmq:
   - Ubuntu/Debian: `apt install libzmq3-dev`
   - Mac ([Homebrew](https://brew.sh/)) `brew install zeromq`
6. Install OpenSSL:
   - Ubuntu/Debian: `apt install libssl-dev pkg-config`
7. Source profile to add `cargo` to `$PATH`: `source ~/.profile`

## Comit
1. Clone comit-rs repo: `git clone https://github.com/comit-network/comit-rs.git && cd comit-rs`
2. Install:
   - `cargo install --path application/comit_node`
   - `cargo install --path application/btsieve`
3. Setup [Bitcoin](#Bitcoin) & [Ethereum](#Ethereum)
4. In `btsieve.toml` file, replace `REPLACE_THIS_ETHEREUM_NODE_URL` with Ethereum URL from Slack topic
5. Start btsieve: `btsieve --config ./btsieve.toml` 
6. Start comit_node: `comit_node`
7. Go to [http://localhost:8181]

## Bitcoin
1. Start Bitcoin node from the workshop folder: `docker-compose rm -sfv`

## Ethereum
1. Install metamask: https://metamask.io/
2. Setup Metamask by following the wizard (new wallet). Yes you have to do the seed phrase thing.
3. Connect metamask to our Ethereum node:
  - Choose "Custom RPC"
    ![connect Ethereum](./img/eth_connect.png)
  - Network Name: "CoBloX Test"
  - New RPC URL: Ethereum URL from Slack topic
  - Leave the rest empty
4. Send your address in the chat "Fund me please"
  ![copy address](./img/eth_copy_address.png)
  
