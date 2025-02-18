![GiDNGddbcAA8x3g](https://github.com/user-attachments/assets/7e18f4a5-002e-4c85-a2f5-066bce59b26f)

## Server ; 


| Component        | Minimum              | Recommended                         |
|------------------|----------------------------|---------------------------------------|
| **CPU**          | 4 | 16 |
| **RAM**          | 4 GB                     | 8 GB                                 |
| **Storage**      | 100 GB SDD                   | 100 GB SSD       |
| **Network**      | 100 Mbps (1 Gbps+ recommended) | 100 Mbps (1 Gbps+ recommended)        |

| Server Provider        | Link              | Features |
|------------------|----------------------------|----------------------------|
| **NetCup**          | [Link](https://www.netcup.com/en/?ref=261820) | Cheap / Paypal |
| **Contabo**          | [Link](https://www.dpbolvw.net/click-101330552-12454592)                     | Cheap / Paypal  |
| **PQ**      | [Link](https://pq.hosting/?from=627713)                  | Cheap / Crypto Payment |


## Privanetix Node Setup ; 

#### Run the following command to update and upgrade system packages:

```bash
sudo apt update -y && sudo apt upgrade -y
```
## 2. Install the required packages:

```bash
sudo apt install htop ca-certificates zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev tmux iptables curl nvme-cli git wget make jq libleveldb-dev build-essential pkg-config ncdu tar clang bsdmainutils lsb-release libssl-dev libreadline-dev libffi-dev jq gcc screen unzip lz4 -y
```
## 3. Install Docker : 

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io -y
docker version
```

## 4. Install Docker Compose : 

```bash
VER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep tag_name | cut -d '"' -f 4)
curl -L "https://github.com/docker/compose/releases/download/$VER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

## 4. Docker User Permissions

```bash
sudo groupadd docker
sudo usermod -aG docker $USER
```

##  5. Install Image 

```bash
docker pull privasea/acceleration-node-beta:latest
```

## 6. Create the program running directory and navigate to it

```bash
mkdir -p ~/privasea/config && cd ~/privasea
```

## 7. Wallet and Password Creation 

- After this command, it will ask you for a password to use, save it for future reference.
- You'll give us your wallet details and we'll save them all.

```bash
docker run --rm -it -v "$HOME/privasea/config:/app/config" privasea/acceleration-node-beta:latest ./node-calc new_keystore
```

#### Example : 
```bash
Enter password for a new key:      # Enter wallet password  
Enter password again to verify:   # Re-enter the password for confirmation  
After successful creation of the wallet, the program will display information similar to the following:
```
#### This is what it will look like at the end of the process :
```bash
node address: 0x1111111111111111111111111111111111111111
# This is the node address you generated, used for linking in the dashboard 
node filename: keystore:///app/config/UTC--2025-01-01T01-11-01.415191015Z--1111111111111111111111111111111111111111

Instructions: 0xf07c3eF23ae7BEb8CD8bA5fF546E35Fd4b332B34 is an example and may differ in your case.
```

## 8. Move KeyStore File to New Directory 
```bash
mv $HOME/privasea/config/UTC--* $HOME/privasea/config/wallet_keystore
```

## 9. Dashbaord Operations

- Dashboard Link : https://deepsea-beta.privasea.ai/privanetixNode
- Connect your wallet, then click "You don't have a Privanetix node yet. Set one up now! > " Click on Set one up now. 
- Set a commission percentage between 1-3 and I will use 1.
- We saved the wallet information, node gave us an address, write it down. Confirm and then click Set up My Node.

![image](https://github.com/user-attachments/assets/995f0041-190b-4e31-ba0f-32f73f4f68ef)

## 10 . Start  : 

- ENTER_YOUR_KEYSTORE_PASSWORD enter the password you set when you created the wallet.
- 

```bash
KEYSTORE_PASSWORD=ENTER_YOUR_KEYSTORE_PASSWORD && docker run -d --name privanetix-node -v "$HOME/privasea/config:/app/config" -e KEYSTORE_PASSWORD=$KEYSTORE_PASSWORD privasea/acceleration-node-beta:latest
```
## 11. Other Transactions

- Stake etc. There are transactions, you can find the details of these on https://www.privasea.ai/privanetix-node.
- You can look from Manage my Privanetix node - we have completed the Top Side.

- If the transaction in Stake is giving problems, make the Fee 350000. It can be a problem.

<p align="center">
  <img src="https://komarev.com/ghpvc/?username=FurkanL0&style=flat-square&color=brightgreen&label=Profile+Views+/+Repo+Views+" alt="Repo / Profile Views" />
</p>
