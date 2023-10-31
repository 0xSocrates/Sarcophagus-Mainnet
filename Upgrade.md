# Archaeologist Node Network Güncelleme Rehberi

Arkadaşlar yeni gelen güncelleme ile birlikte aynı  sunucuda aynı arkeolog nodunu birden fazla ağda çalıştırabileceksiniz. Halihazırda ***Eth Mainnnette*** çalışıyorduk artık buna ek olarak ***Polygon Mainnet, Polygon Mumbai, Eth Sepolia*** ağlarında da çalıştırılabilecek. 

Eth Mainnete ek olarak hangi ağda veya ağlarda çalıştırmak istediğinize karar verdikten sonra yapmanız gerekenler;
- İlk olarak sunucunuzda `cd ~/quickstart-archaeologist` altındaki `.env` dosyasını yedekleyin. (bunu zaten yapmış olabilirsiniz)
- Çalıştırmak istediğiniz her ağ için yeni ve eşsiz mnemonic üretmeniz gerekecek. `COMPOSE_PROFILES=seed-gen docker compose run seed-gen` komutu ile sunucunuzda offline şekilde mnemonic oluşturabilirsiniz.
- Son ihtiyacınız olan şey çalıştıracağınız ağlarda gas ücretlerini ödemek için ağın yerel coini ve sarco token cüzdanlarınıza almanız gerekecek.

- **Halihazırda Eth Mainnette arkeolog çalıştırdığınız cüzdanı diğer ağlar için de kullacaksınız. Farklı cüzdan kullanmayın!!!**

**Polygon için;**
- Cüzdanınıza ağı ekleyin https://chainlist.org/?search=polygon
- Gas fee için MATIC alın
- Polygon $SARCO Contract Address: 0x80Ae3B3847E4e8Bd27A389f7686486CAC9C3f3e8
- Uniswap V3 $SARCO/MATIC havuzundan Sarco satın alabilirsiniz https://app.uniswap.org/tokens/polygon/0x80ae3b3847e4e8bd27a389f7686486cac9c3f3e8
- Ya da Ethereumdaki tokenlarınızı Polygon'a köprüleyebilirsiniz  https://wallet.polygon.technology/polygon/bridge/deposit

**Ethereum;**
- L1 Ethereum $SARCO Sözleşme Adresi: 0x7697b462a7c4ff5f8b55bdbc2f4076c2af9cf51a
- L1 Ethereum $SARCO/ETH havuzu: https://app.uniswap.org/tokens/ethereum/0x7697b462a7c4ff5f8b55bdbc2f4076c2af9cf51a
Bunlar zaten ekliydi

**Polygon Mumbai;**
- Ağı ekleyin https://mumbai.polygonscan.com/
- Test Matic alın  https://faucet.polygon.technology/ ya da https://mumbaifaucet.com/
- Polygon Mumbai $SARCO Contract Address: 0x2BC9019e6d9e6a26D7D8d8CDDa4e5dE9B787D7bb
- Polygon Mumbai $SARCO satın alın https://app.uniswap.org/swap?outputCurrency=0x2BC9019e6d9e6a26D7D8d8CDDa4e5dE9B787D7bb

**Sepolia;**
Sepolia $SARCO Contract Address: 0xfa1FA4d51FB2babf59e402c83327Ab5087441289
Sepolia ETH: https://sepoliafaucet.com/
Sepolia $SARCO: https://app.uniswap.org/swap?outputCurrency=0xfa1FA4d51FB2babf59e402c83327Ab5087441289

## Sunucuya geri dönün
```
cd ~/quickstart-archaeologist
```
```
COMPOSE_PROFILES=service docker compose down --remove-orphans
```
```
git pull origin main
```
```
COMPOSE_PROFILES=service docker compose pull
``` 
```
rm -rf .env
```
```
mv .env.example .env
```

Sırasıyla yaptıktan sonra `nano .env` ile ya da mobaxterm kullanıyorsanız sol taraftan env dosyasını açın

- `ETH_PRIVATE_KEY=` karşısına cüzdanının private keyi (yedeklediğiniz .env ile aynısı
- `DOMAIN=` karşısına a kaydı yaptığınız domain adresinizi
- `CHAIN_IDS=` karşısına " " içinde ve aralarında virgül olacak şekilde çalıştıracağınız ağların chain-id'lerini ekleyin. Yukarıda örneği verilmiş.

- Son kısımda her ağ için mnemonic ve provider url satırı var. (mainnet eth mainnet demek). Satırların başlarında # işareti var, bu yorum satırı olduğunu belirtir, dosya çalışırken bu satırları görmez. Sadece çalıştırmak istediğiniz ağların satırları başındaki **#** işaretini silin. Diğerleri aynı kalsın. 

- `..._ENCRYPTION_MNEMONIC=` satırı karşısına her ağ için ayrı oluşturduğunuz menmonicleri girin. Mainnet için, yedeklediğiniz .env dosyasındaki mnemonici girin.

- `...._PROVIDER_URL=` karşısına ekleyeceğiniz endpointler için bir İnfura hesabınıza girin, yoksa yeni hesap açın https://app.infura.io/dashboard
API Keys kısmına gelin My First Key üzerine tıklayın veya sağ üstten yeni bir tane oluşturun. açılan listenin sağ üstünde WebSockets üzerine tıklayın. https yerine buradaki wss ile başlayan endpointleri kullanıcaz. Çalıştırmak istediğiniz ağlar için .env dosyasına linkeri ekleyin.

Dosyayı kaydedip kapatın `ctrl+x` `y`

Yeni ağ/ağlardaki arkeologların kaydını yapın.
- eth mainnet için register yapmayacağız, zaten daha önce kaydetmiştik
- polygon mainnet için `COMPOSE_PROFILES=register NETWORK=polygonMainnet docker compose run register`
- polygon mumbai için  `COMPOSE_PROFILES=register NETWORK=polygonMumbai docker compose run register`
- eth sepolia için `COMPOSE_PROFILES=register NETWORK=sepolia docker compose run register`
- Komutunu girin, sorulan sorulara yanıtlarınızı girin. daha önceki arkeolog kaydı gibi. onayladıktan ve kaydettikten varsa diğer ağlar için de aynı şekilde register işlemini yapın ardından başlatın.
```
COMPOSE_PROFILES=service docker compose run up -d
```

- Eğer bir sorun olmazsa çalıştırdıktan bir kaç dakika sonra https://app.dev.sarcophagus.io/archaeologists arkeolog listesinde görüneceksiniz. (siteye çalıştırdığınız ağ ile bağlanmayı unutmayın)

















