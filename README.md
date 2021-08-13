[![](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/images/0)](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/links/0)[![](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/images/1)](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/links/1)[![](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/images/2)](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/links/2)[![](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/images/3)](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/links/3)[![](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/images/4)](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/links/4)[![](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/images/5)](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/links/5)[![](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/images/6)](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/links/6)[![](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/images/7)](https://sourcerer.io/fame/juanro49/juanro49/rtl88x2ce-dkms/links/7)

# RTL88x2CE dkms module driver

This driver is for MateBook13 Ubuntu 18, other MateBook using RTL8822CE PCIe may also be working, but I have not tested yet.


## Installation

### Dependencies

If you are installing the Wi-Fi driver from a fresh Ubuntu, **first connect to a mobile phone hotpot through Bluetooth** and update apt, then install dkms.

- Connect mobile phone to the laptop through Bluetooth
- Open laptop's quick link menu from the top right conner, *connect to internet* through mobile phone. Now the laptop is connecting to internet
- Open a terminal:
```
sudo apt update
sudo apt install dkms
```

### Build and install

- [Download this repository](https://github.com/ZuyuanZhu/rtl88x2ce-dkms) as a zip file from anyother PC, and unzip it to the laptop's Document folder.
- In the Document folder, open a terminal:
```
sudo cp rtl88x2ce-dkms/rtw88_blacklist.conf /etc/modprobe.d/rtw88_blacklist.conf
sudo mkdir /usr/src/rtl88x2ce-35403
sudo cp -Rv rtl88x2ce-dkms/* /usr/src/rtl88x2ce-35403/
sudo dkms add -m rtl88x2ce -v 35403
sudo dkms build -m rtl88x2ce -v 35403
sudo dkms install -m rtl88x2ce -v 35403
```
After finishing these steps, then reboot the laptop, the Wi-Fi should be working then.


## Other installation methods

IF your laptop already have access to the internet(eg., via ethernet cable), then you could try any one of the methods bellow:

### [PatoJAD Repo](https://patojad.com.ar/repositorio/) (outdated)
```
echo 'deb https://gitlab.com/patojad/repository/raw/patojad/debs/ patojad main' | sudo tee /etc/apt/sources.list.d/patojad.list
wget -qO - https://gitlab.com/LynxOS/repository/raw/lynxos/LynxPub.gpg | apt-key add -
sudo apt update
sudo apt install rtl88x2ce-dkms
```

### Deb package
```
wget https://github.com/juanro49/rtl88x2ce-dkms/releases/download/5.7.3_35403_20210523/rtl88x2ce-dkms_35403_amd64.deb
sudo dpkg -i rtl88x2ce-dkms_35403_amd64.deb
```

### Install from source
```
git clone https://github.com/juanro49/rtl88x2ce-dkms.git
sudo cp rtl88x2ce-dkms/rtw88_blacklist.conf /etc/modprobe.d/rtw88_blacklist.conf
sudo mkdir /usr/src/rtl88x2ce-35403
sudo cp -Rv rtl88x2ce-dkms/* /usr/src/rtl88x2ce-35403/
sudo dkms add -m rtl88x2ce -v 35403
sudo dkms build -m rtl88x2ce -v 35403
sudo dkms install -m rtl88x2ce -v 35403
```

### Enable module
Enable the driver:
`sudo modprobe rtl88x2ce`
If not working, just reboot to make your life easy. Or, just continue Google if you like :)


### Notes
- *Network controller: Realtek Semiconductor Co., Ltd. RTL8822CE 802.11ac PCIe Wireless Network Adapter*

- *Soure and more driver could be downloaded with guides [from this repo](https://github.com/XAIOThaifeng/realtek-linux/tree/master/RTL8822CE).*
