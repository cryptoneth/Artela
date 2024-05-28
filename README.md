# Artela

Minimum Hardware Requirements
4x CPUs; the faster clock speed the better
8GB RAM
100GB of storage (SSD or NVME)


Recommended Hardware Requirements
8x CPUs; the faster clock speed the better
16GB RAM
1TB of storage (SSD or NVME)


ران کردن با اسکریپت


```
wget https://raw.githubusercontent.com/freshe4qa/artela/main/artela.sh && chmod +x artela.sh && ./artela.sh

```
عدد 1 رو بزنید بعد اینتر

صبر کنید نصب تموم شه

حالا عدد 2 رو بزنید بعد اینتر

اطلاعاتی مثل ادرس و کلید خصوصی رو یادداشت کنید .

حالا عدد 4 رو بزنید بعد اینتر تا خارج بشید

```
source $HOME/.bash_profile

artelad status 2>&1 | jq .SyncInfo

```

-------------------------------------------------------------

هر زمانی نودتون سینک شد . Catching Up = False بود و بلاک ها با بلاک شبکه سینک بود کامل 
https://betanet-scan.artela.network/
که از سایت بالا میتونید ببینید برید مرحله بعدی

** دقت کنید اگر بلاک ها اروم جلو میرفت وقتی
artelad status 2>&1 | jq .SyncInfo
کامند بالا رو هی برای چک کردن اجرا میکنید 

کافیه یکبار نود رو ری استارت کنید

sudo systemctl restart artela

تا بلاک ها شروع کنن با سرعت سینک شدن

-------------------------------------------------------------

با کامند زیر و جایگذاری ادرس ولت ارتلا . ادرس ولت Evm رو با فرمت EIP 55 بگیرید و کپی کنید

artelad debug addr <YOUR_ART_ADDRESS>  

 وارد دیسکورد بشید و فاست بگیرید

https://discord.com/invite/artela

تو بخش فاست کافیه 
$request <YOUR_EVM_ADDRESS>
وارد کنید . هر 6 ساعت یک بار میتونید فاست بگیرید و یادتون نره که ادرس Eip 55 که به صورت EVM گرفتید رو جایگذاری کنید

برای چک کردن بالانس کامند پایین رو بزنید و جای $ARTELA_WALLET_ADDRESS  ادرس ولتتون رو بدید ( ادرس Artella . ادرس EVM رو نمیخواد ) . ادرسی رو میخواد که تو مرحله اول با اسکریپت ساختیم


artelad query bank balances $ARTELA_WALLET_ADDRESS    

برای گرفتن کلید خصوصی ولت برای ایمپورت به متامسک کافیه کامند زیر رو بزنید                               

artelad keys unsafe-export-eth-key wallet


برای اضافه کردن شبکه ارتلا به متا مسک مشخصات زیر رو نیاز دارید

Network Name: Artela Testnet
New RPC URL: https://betanet-rpc1.artela.network
ChainID: 11822
Symbol: ART
Block Explorer URL: https://betanet-scan.artela.network/


-------------------------------------------------------------


با دستور 
artelad status 2>&1 | jq .SyncInfo

چک کنید اگر نودتون سینک بود کامل . اگر بلاک ها با شبکه یکی بود . برید مرحله ساخت ولیدیور

artelad tx staking create-validator \
--amount="100000000000000000uart" \
--pubkey=$(artelad tendermint show-validator) \
--moniker="iamshaho" \
--website="https://x.com/iamshaho" \
--details="a simple human" \
--commission-rate="0.10" \
--commission-max-rate="0.20" \
--commission-max-change-rate="0.01" \
--min-self-delegation="1" \
--gas="200000" \
--chain-id="artela_11822-1" \
--from=wallet \
--node tcp://47.254.66.177:26657
