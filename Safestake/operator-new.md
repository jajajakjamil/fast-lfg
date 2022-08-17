<p style="font-size:14px" align="right">
<a href="https://t.me/BeritaCryptoo" target="_blank">Join our telegram <img src="https://user-images.githubusercontent.com/50621007/183283867-56b4d69f-bc6e-4939-b00a-72aa019d1aea.png" width="30"/></a>
<a href="https://twitter.com/BeritaCryptoo" target="_blank">Join our twitter <img src="https://user-images.githubusercontent.com/108946833/184274157-08210464-fa03-493d-b01c-2420c67a524f.jpg" width="30"/></a>
</p>
 
<p align="center">
  <img height="150" height="auto" src="https://user-images.githubusercontent.com/38981255/184852284-08b36261-236b-4027-bdc3-487858eb09c7.png">
</p>

# Safestake Incentivized Testnet By ParaState
## Mulai ulang layanan Anda (operator atau validator)
Mengapa?

Karena kami memperbaiki beberapa bug

Rentang Debug
- Hasilkan kesalahan id validator
- Operator tidak dapat menautkan ke simpul root

Bagaimana?

### Untuk operator

- Masuk ke server Anda
- Tetapkan aturan firewall

<img width="750" alt="firewall_rule" src="https://user-images.githubusercontent.com/108946833/185217868-3b70d0cb-ee2d-4740-813f-710ad09316a1.png">

## Stop your service
```
cd SafeStakeOperator
sudo docker compose -f docker-compose-operator.yml down
```
## Temukan ke direktori data operator Anda
```
cd /data/operator
```
## Hapus beberapa data kesalahan
```
sudo rm -rf ./ropsten/validators/
sudo rm -rf ./ropsten/secrets/
```
## Tarik kode sumber terbaru
```
cd SafeStakeOperator
git pull origin main
```
![Screenshot_50](https://user-images.githubusercontent.com/108946833/185222843-5ec5b558-fe75-42da-82b6-52a597ebaa7e.png)

Jika ada error seperti ini, hapus `.env`
```
rm .env
```
Buat lagi `.env`
```
vim .env
```
Masukan Output yang sudah di simpan 
Contoh Output:
![Screenshot_51](https://user-images.githubusercontent.com/108946833/185223543-5be20b72-67c0-4914-82bf-326604e5ae17.png)

Jika sudah keluar dari mode ini tekan `ESC`, lalu masukkan perintah `:wq` lalu `ENTER`
```
git commit
git pull origin main
```
![Screenshot_52](https://user-images.githubusercontent.com/108946833/185224125-fa248bd4-11b6-460f-bfe0-213efc2e4b7d.png)


## Bangun kembali citra operator Anda 
```
// mungkin membutuhkan waktu sekitar 1 jam
sudo docker compose -f  docker-compose-operator.yml build operator
```
## Mulai layanan Anda
```
sudo docker compose -f docker-compose-operator up -d
// Jika anda mau lihat logs(optional)
sudo docker compose -f docker-compose-operator logs -f
```
## Dapatkan kunci publik Anda
```
sudo docker compose -f docker-compose-operator logs -f operator | grep "node public key" 
```
***SIMPAN `NODE PUBLIK KEY`***
 