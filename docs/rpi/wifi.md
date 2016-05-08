## Wifi connection of the PI 3

The Raspberry Pi 3 Model B comes with an integrated 802.11n Wireless LAN module. In order to get the Pi connected to the Wifi network the `/etc/wpa_supplicant/wpa_supplicant` file has to be configured.

##### At home

1) Open the file.

```bash
sudo nano /etc/wpa_supplicant/wpa_supplicant
```

2) Add a new entry.

```bash
network{
  ssid="SSID"
  psk="PASSWORD"
}
```

##### At the university (WWU Münster)

1) Download the CA certificate of the university [here](https://www.uni-muenster.de/WWUCA/info/wwuca-keys.html). Select the *Deutsche Telecom Root CA*, which is the **Import (.der)** in the **X.509 Wurzel-CA** column.

```bash
wget https://www.uni-muenster.de/WWUCA/rootca.der
```

2) Move the CA certificate to the `/etc/wpa_supplicant/` folder.

```bash
sudo mv rootca.der /etc/wpa_supplicant/rootca.der
```

3) Open the network configuration file.

```bash
sudo nano /etc/wpa_supplicant/wpa_supplicant
```

4) Add a new entry.

```bash
network{
  ssid="eduroam"
  proto=RSN
  key_mgmt=WPA-EAP
  pairwise=CCMP
  auth_alg=OPEN
  eap=PEAP
  identity="USERNAME@uni-muenster.de"
  password="PASSWORD"
  ca_cert="/etc/wpa_supplicant/rootca.der"
  phase2="auth=MSCHAPV2"
  disabled=0
}
```

5) Restart the network.

```bash
sudo service networking restart
```
