<h1 align="center"> Sarcophagus-Mainnet </h1>

![1500x500](https://github.com/0xSocrates/Testnet-Rehberler/assets/108215275/166f6a97-37c4-4b04-b28c-da54d40eb0aa)

## Arkadaşlar herkese merhaba. Testnetini yaptığımız Sarcophagus mainneti başladı.
>  Aldığınız 1000 $SARCO ödülün tamamını burada kullanacaksınız.
> 
>  6 ay boyunca mainnet çalıştırıp ve %99 uptime şartını sağlayanlara 6000 $SARCO ödül verilecek.
> 
>  Etherium işlem katmanı ile etkileşime girebilmek için bir Eth Mainnet RPC adresine ihtiyacınız olacak. Muhtemelen ücretsiz olanlar yetecektir.
> 
>  Kurulum yapacağınız sunucuya A kaydı yapılmış bir domain olması gerekiyor.
> 
>  Sarco cüzdanınızın private keyi kurulum esnasında gerekecek
> 
>  Cüzdanınızda gaz ücretlerini karşılamak için $ETH bulunması gerekiyor.
>  En çok düşündüren konu bu biliyorum
>
> Eğer dapp testnetine de katıldıysanız 300 $Sarco da oradan ödül aldınız. Bunu ethye çevirince başlangıç için yeterli olacağını düşünüyorum.
> 
> Sunucu gereksinimleri 1 Cpu 1 Gb Ram ve 10 Gb Ssd fazlasıyla yeterli olacaktır. (Min 500mb ram 4gb ssd)

## Kurulum yapmak için bu komutu girin
```
curl -sSL -o sarcophagus.sh https://raw.githubusercontent.com/0xSocrates/Sarcophagus-Mainnet/main/sarcophagus.sh && chmod +x sarcophagus.sh && bash ./sarcophagus.sh
```
## Tamamlandıktan sonra arkeolog kaydını yapmak için
```
cd quickstart-archaeologist
COMPOSE_PROFILES=register docker compose run register
```
### Komutu girdikten sonra sırasıyla
> 1. soru kontrakla etkileşime girmek onayı `y` diyin
> 2. soru digging fee, tutacağınız lahitler karşılığında mumyacıdan aylık talep ettiğiniz $SARCO miktarı
> 3. soru free-bond 1000 yapın
> 4. 
