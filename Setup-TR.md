![GiDNGddbcAA8x3g](https://github.com/user-attachments/assets/7e18f4a5-002e-4c85-a2f5-066bce59b26f)

## Gereksinimler ; 


| Component        | Minimum              | Önerilen                         |
|------------------|----------------------------|---------------------------------------|
| **CPU**          | 4 | 16 |
| **RAM**          | 4 GB                     | 8 GB                                 |
| **Storage**      | 100 GB SDD                   | 100 GB SSD       |
| **Network**      | 100 Mbps (1 Gbps+ recommended) | 100 Mbps (1 Gbps+ recommended)        |

| Server Sağlayıcıları        | Link              | Özellikler |
|------------------|----------------------------|----------------------------|
| **NetCUP**          | [Link](https://www.netcup.com/en/?ref=261820) | Ucuz / Kredi Kartı / Paypal |
| **Contabo**          | [Link](https://www.dpbolvw.net/click-101330552-12454592)                     | Ucuz / Kredi Kartı / Paypal  |
| **PQ**      | [Link](https://pq.hosting/?from=627713)                  | Ucuz / Kredi Kartı / Kripto İle Ödeme |


## Node Kurulum ; 

#### Sistem paketlerini güncellemek ve yükseltmek için aşağıdaki komutu çalıştırın:

```bash
sudo apt update -y && sudo apt upgrade -y
```
## 2. Gerekli paketleri kurun:

```bash
sudo apt install htop ca-certificates zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev tmux iptables curl nvme-cli git wget make jq libleveldb-dev build-essential pkg-config ncdu tar clang bsdmainutils lsb-release libssl-dev libreadline-dev libffi-dev jq gcc screen unzip lz4 -y
```
## 3. Docker'ı Kur : 

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io -y
docker version
```

## 4. Docker Compose'u Kur : 

```bash
VER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep tag_name | cut -d '"' -f 4)
curl -L "https://github.com/docker/compose/releases/download/$VER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
docker-compose --version
```

## 4. Docker Kullanıcı İzinleri

```bash
sudo groupadd docker
sudo usermod -aG docker $USER
```

##  5. İmage'i İndirelim 

```bash
docker pull privasea/acceleration-node-beta:latest
```

## 6. Dizin Oluşturalım Ve Dizinin İçine Girelim 

```bash
mkdir -p ~/privasea/config && cd ~/privasea
```

## 7. Cüzdan ve Şifre Oluşturma 

- Bu komuttan sonra size kullanmalık şifre isteyecek ilerde lazım olacak kaydedin.
- Sizde cüzdan bilgileri vericek onlarıda tümüyle kaydediyoruz.

```bash
docker run --rm -it -v "$HOME/privasea/config:/app/config" privasea/acceleration-node-beta:latest ./node-calc new_keystore
```

#### Örnek : 
```bash
Enter password for a new key:      # Enter wallet password  
Enter password again to verify:   # Re-enter the password for confirmation  
After successful creation of the wallet, the program will display information similar to the following:
```
#### İşlem Sonucuda Böyle Görünecek :
```bash
node address: 0x1111111111111111111111111111111111111111
# This is the node address you generated, used for linking in the dashboard 
node filename: keystore:///app/config/UTC--2025-01-01T01-11-01.415191015Z--1111111111111111111111111111111111111111

Instructions: 0xf07c3eF23ae7BEb8CD8bA5fF546E35Fd4b332B34 is an example and may differ in your case.
```

## 8. KeyStore Dosyasını Yeni Dizine Taşıyalım 
```bash
mv $HOME/privasea/config/UTC--* $HOME/privasea/config/wallet_keystore
```

## 9. Dashbaord İşlemleri 

- Dashboard Link : https://deepsea-beta.privasea.ai/privanetixNode
- Cüzdanınızı bağlayın ardından "You don’t have a Privanetix node yet. Set one up now! > " Set one up now'a tıklayın. 
- 1-3 Arası bir komisyon yüzdesi ayarlayın ben 1 kullanacağım.
- Cüzdan bilgilerini kaydetmiştik orada bize adres verdi o adresi yazın. Onaylayın ardından Set up My Node'ye tıklayın.

![image](https://github.com/user-attachments/assets/995f0041-190b-4e31-ba0f-32f73f4f68ef)

## 10. Diğer İşlemler 

- Stake vb. işlemler  bulunuyor bunların detaylarına https://www.privasea.ai/privanetix-node sayfasından ulaşabilirsiniz.
- Manage my Privanetix node kısmından itibaren bakabilirsiniz - Üst Tarafı tamamladık.


<p align="center">
  <img src="https://komarev.com/ghpvc/?username=FurkanL0&style=flat-square&color=brightgreen&label=Profile+Views+/+Repo+Views+" alt="Repo / Profile Views" />
</p>
