# LightPayCoin
Shell script to install a [LightPayCoin Masternode](https://www.lightpaycoin.org/) on a Linux server running Ubuntu 14.04 or 16.04. Use it on your own risk.

It usually takes 24-32 hours from setting up a new masternode to receiving your first LPC.

***
## Installation:
```
git clone https://github.com/lpcproject/lpcinstall.git
cd lpcinstall
bash lpc-install.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps for Windows Wallet
1. Open the LightPayCoin Coin Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **1000** **LightPayCoin** to **MN1**.
4. Wait for 15 confirmations.
5. Go to **Tools -> "Debug console - Console"**
6. Type the following command: **masternode outputs**
7. Go to  ** Tools -> "Open Masternode Configuration File"
8. Add the following entry:
```
Alias Address Privkey TxHash Output_index
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* Output index:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
12. Open **Debug Console** and type:
```
startmasternode "alias" "0" "MN1"
```
***

## Usage:
```
lightpaycoin-cli getinfo
lightpaycoin-cli mnsync status
lightpaycoin-cli masternode status
```
Also, if you want to check/start/stop **LightPayCoin** , run one of the following commands as **root**:

**Ubuntu 16.04**:
```
systemctl status LightPayCoin #To check the service is running.
systemctl start LightPayCoin #To start LightPayCoin service.
systemctl stop LightPayCoin #To stop LightPayCoin service.
systemctl is-enabled LightPayCoin #To check whetether LightPayCoin service is enabled on boot or not.
```
**Ubuntu 14.04**:  
```
/etc/init.d/LightPayCoin start #To start LightPayCoin service
/etc/init.d/LightPayCoin stop #To stop LightPayCoin service
/etc/init.d/LightPayCoin restart #To restart LightPayCoin service
```
***
