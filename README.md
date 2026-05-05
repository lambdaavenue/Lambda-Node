# Lambda Node

## Overview

Lambda Node is a blockchain implementation designed to support a peer-to-peer digital currency system focused on scalability, decentralization, and efficient transactions.

The goal of the project is to provide a foundation for a global, permissionless payment network that enables fast and low-cost value transfer without central authorities.

---

## What is Lambda?

Lambda is a digital currency that enables instant payments to anyone, anywhere in the world.

It operates on a peer-to-peer network where:
- Transactions are validated by the network
- No central authority controls issuance or transfers
- The system is designed for decentralized financial exchange

Lambda Node is a full node implementation that maintains the network and validates transactions.


---

## Third-Party Software

This project includes software developed by:
- The OpenSSL Project (OpenSSL Toolkit)
- Eric Young (cryptographic software)
- Thomas Bernard (UPnP implementation)

---


## Build Instructions (Linux)

### 1. Install dependencies

```bash
sudo apt-get update

sudo apt-get install -y \
build-essential cmake git ninja-build pkg-config \
libboost-chrono-dev libboost-filesystem-dev libboost-test-dev libboost-thread-dev \
libevent-dev libssl-dev libzmq3-dev \
libminiupnpc-dev libdb++-dev \
qttools5-dev qttools5-dev-tools qtbase5-dev \
protobuf-compiler libprotobuf-dev libqrcodegen-dev \
libtool autoconf automake \
libcurl4-openssl-dev ca-certificates dos2unix
```

---

### 2. Clone repository

```bash
git clone https://github.com/lambdaavenue/Lambda-Node.git
cd Lambda-Node
```

---

### 3. Build

```bash
mkdir build
cd build

cmake -GNinja .. \
-DBUILD_LAMBDA_QT=ON \
-DENABLE_UPNP=OFF \
-DENABLE_MAN=OFF \
-DBUILD_LAMBDA_SEEDER=OFF \
-DBUILD_LAMBDA_ZMQ=ON

ninja
```

---

### 4. Fix permissions (if needed)

```bash
find ../ -name "*.sh" -exec dos2unix {} \; -exec chmod +x {} \;
find ../ -name "*.py" -exec dos2unix {} \; -exec chmod +x {} \;

chmod -R +x .
```
If it still gives some permission issue, then just give this command: chmod -R +x /path/to/your/project.
Rerun cmake and ninja. Don't clean before

---

## Configuration

Create the configuration file:

```
~/.lambda/lambda.conf
```

Example configuration:

```ini
server=1
txindex=1
acceptnonstdtxn=0
dns=1
listen=1
rpcuser=CHANGE_ME
rpcpassword=CHANGE_ME_STRONG_PASSWORD
rpcport=9332
addnode=145.239.0.137:11029
addnode=51.75.144.177:21029
addnode=91.55.255.202:9333
addnode=89.117.149.130:9333
addnode=66.94.115.80:9333
addnode=173.212.224.67:9333
```

⚠️ Do not use default credentials in production.

---

## Running the Node

```bash
./lambdad
```

CLI:

```bash
./lambda-cli
```

---

## Qt Wallet

The Qt wallet is included.

It supports legacy and Bech addresses depending on configuration and pool requirements.

To generate a legacy address by the console of the QT:

```bash
getnewaddress "" legacy
```

---

## Additional Information

See:

```
doc/README.md
```
