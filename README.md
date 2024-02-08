<h1 align="center"> Mangata AVS
  
![image](https://pbs.twimg.com/profile_banners/1314872601949462530/1686804364/1500x500)

## Sistem gereksinimleri:
### Ubunutu 22.04
NODE TİPİ | CPU     | RAM      | SSD     |
| ------------- | ------------- | ------------- | -------- |
| Mangata  | 2          | 4         | 40  |
  

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




> Kapalı parantez dahil, `<key-ismi>` değiştirin, <> parantezleri kaldırın.

![Ekran görüntüsü 2024-02-08 124148](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/6b7700d0-d255-4e63-8162-54a8309af9cb)

```
eigenlayer operator keys create --key-type ecdsa <key-ismi>
```

> Bu komuttan sonra şifre oluşturmanızı isteyecek, şifre karmaşık olmalı. Aynı şifreyi iki kere gireceğiz.

![Ekran görüntüsü 2024-02-08 124257](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/ea8a2804-7875-4a29-b102-e1848e3e1085)

> `ecdsa` KEY bize bir `EVM` adresi, `private key` ve dosya `path` (yolu) verecek

> Buradaki bilgiler sizde de benzer şekilde çıkacak güvenli şekilde saklayın.

![Ekran görüntüsü 2024-02-08 124603](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/bed08b0c-2706-4a95-b2ae-37dbf7184a75)

> Kapalı parantez dahil, `<key-ismi>` değiştirin, <> parantezleri kaldırın.
![Ekran görüntüsü 2024-02-08 125720](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/fe3d4dc1-d278-4801-bf68-11fb32b12236)
```
eigenlayer operator keys create --key-type bls <key-ismi>
```
> Bu komuttan sonra şifre oluşturmanızı isteyecek, şifre karmaşık olmalı. Aynı şifreyi iki kere gireceğiz.

![Ekran görüntüsü 2024-02-08 125831](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/2ad73b8c-06f4-49a8-9ca4-019aee6e43fb)

> `bls` KEY ise bir `private key` verecek. Hepsini kayıt edelim.

![Ekran görüntüsü 2024-02-08 125927](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/5a2ca0fe-0e87-4141-a25f-193acf14735b)

> Keyleri listeyerek dosya yollarını kontrol ediyoruz.

![Ekran görüntüsü 2024-02-08 130326](https://github.com/CoinHuntersTR/Mangata-AVS/assets/111747226/58803415-318c-4750-bcc9-63470a3374ab)

```
eigenlayer operator keys list
```
## Operatör Kaydı
