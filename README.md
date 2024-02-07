<h1 align="center"> Mangata AVS
  
![image](https://pbs.twimg.com/profile_banners/1314872601949462530/1686804364/1500x500)

## Sistem gereksinimleri:
### Ubunutu 22.04
NODE TİPİ | CPU     | RAM      | SSD     |
| ------------- | ------------- | ------------- | -------- |
| Avail  | 2          | 4         | 40  |
  

## Kurulum

```
sudo apt-get update -y && sudo apt-get upgrade -y
```

### Docker Kurulumu
```
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do sudo apt-get remove $pkg; done
```
```
sudo apt-get update
```
```
sudo apt-get install ca-certificates curl gnupg
```
```
sudo install -m 0755 -d /etc/apt/keyrings
```
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```
```
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```
```
echo \
  "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
### Docker Güncelleme ve Çalıştırma
```
sudo apt update -y && sudo apt upgrade -y
```
```
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```
```
sudo docker run hello-world
```

### Go Kurulumu

```
cd $HOME
ver="1.20.2"
wget "https://golang.org/dl/go$ver.linux-amd64.tar.gz"
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf "go$ver.linux-amd64.tar.gz"
rm "go$ver.linux-amd64.tar.gz"
echo "export PATH=$PATH:/usr/local/go/bin:$HOME/go/bin" >> $HOME/.bash_profile
source $HOME/.bash_profile
go version
```

## EigenLayer CLI kurulumu

```
git clone https://github.com/Layr-Labs/eigenlayer-cli.git
```
```
cd eigenlayer-cli
```
```
mkdir -p build
```
```
go build -o build/eigenlayer cmd/eigenlayer/main.go
```
```
cd
```
```
sudo cp eigenlayer-cli/build/eigenlayer /usr/local/bin/
```
> Altta ki komutlar ile KEY'ler oluşturuyoruz.

> `ecdsa` KEY bize bir `EVM` adresi, `private key` ve dosya `path` (yolu) verecek

> `bls` KEY ise bir `private key` verecek. Hepsini kayıt edelim.

> Kapalı parantez dahil, `<key-ismi>` değiştirin, <> parantezleri kaldırın..

> Her komuttan sonra şifre oluşturmanızı isteyecek, şifre karmaşık olmalı.

> Örnek şifre Özel karakterler kullanarak güçlü bir şifre oluştur ve kaybetme.

```
eigenlayer operator keys create --key-type ecdsa <key-ismi>
```
```
eigenlayer operator keys create --key-type bls <key-ismi>
```
> Keyleri listeyerek dosya yollarını kontrol ediyoruz.
```
eigenlayer operator keys create --key-type bls <key-ismi>
```
