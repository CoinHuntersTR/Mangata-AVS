### Eskiden kurup hata alanların yapması gereken değişiklikler.

# Güncelleme
```
cd avs-operator-setup
```
```
docker compose down -v
```
```
cd
```
```
srm -rf eigenlayer-cli
```
## EigenLayer CLI
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
## Operatör Kayıt

> nano operator.yaml içindekilerin hepsini bir yere not edelim. Sonradan lazım olabilir.

```
eigenlayer operator config create
```

> y Enter yapalım

> Kurarken verdiği ETH adresini giriyoruz. İki kere isteyecek

> Public RPC adresini istiyor infuradan aldığınız https adresini giriyoruz.

> ecdsa key path yani dosya yolunu giriyoruz.  

> goerli seçiyoruz.

> Daha önce girdiğiniz şifreyi isteyecek onu giriyoruz işlem tamam.

## Op. Dosyalarını düzenleyelim.

```
nano operator.yaml
```
> Github üzerinden yüklediğimiz raw linkini alıyoruz ve metadata_url bölümmüne giriyoruz.

> el_delegation_manager_address: 0x1b7b8F6b258f95Cf9596EabB9aa18B62940Eb0a8 bölümünde bu adres yazıyor olmalı.

> sonrasında Ctrl x y enter yapıp kayıt ediyoruz.

## Register işlemi

```
cd
```
```
eigenlayer operator register operator.yaml
```
```
cd avs-operator-setup
```
```
./run.sh opt-in
```
```
docker compose up -d
```
```
docker logs -f --tail 100 mangata-finalizer-node
```

