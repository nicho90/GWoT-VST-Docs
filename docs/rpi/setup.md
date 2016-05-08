## What is a Raspberry Pi?

>The Raspberry Pi is a low cost, credit-card sized computer that plugs into a computer monitor or TV, and uses a standard keyboard and mouse. It is a capable little device that enables people of all ages to explore computing, and to learn how to program in languages like Scratch and Python. It’s capable of doing everything you’d expect a desktop computer to do, from browsing the internet and playing high-definition video, to making spreadsheets, word-processing, and playing games.

>What’s more, the Raspberry Pi  has the ability to interact with the outside world, and has been used in a wide array of digital maker projects, from music machines and parent detectors to weather stations and tweeting birdhouses with infra-red cameras. We want to see the Raspberry Pi being used by kids all over the world to learn to program and understand how computers work.

>(Source: [https://www.raspberrypi.org/help/what-is-a-raspberry-pi/](https://www.raspberrypi.org/help/what-is-a-raspberry-pi/), 2016-04-28)

#### Different Models of the Pi

||   Pi Zero  |   Pi A  | Pi A+   |  Pi B  |   Pi B+ | Pi 2B   | Pi 3B |
|----|----|----|----|----|
| CPU | 1Ghz(1) | 700mHz(1) | 700mHz(1) | 700mHz(1) | 700mHz (1)  | 900mHz(4) | 1.2GHz(4) |
| RAM | 512MB | 256MB | 256MB | 512MB | 512MB | 1024MB | 1024MB |
| USB | 1(OTG) | 1 | 1 | 1 | 1 | 4 | 4 |
| Display port | mini HDMI | HDMI | HDMI | HDMI | HDMI | HDMI | HDMI |
| Memory | microSD | SD | microSD | SD | microSD | microSD | microSD |
| Network | - | - | - | Ethernet | Ethernet | Ethernet | Ethernet, Bluetooth, WLAN |
| GPIO-Pins | 40 | 26 | 40 | 26 | 40 | 40 | 40 |
| Watt | 0.5–0.7W | 2.5W | 0.5-1.2W | 3.5W | 2.5-3W | max. 4W | max. 4W |
| Milliamp | 100–140mA | 500mA | 100-130mA | 700mA | 500-600mA | 800mA | 800mA |
| Price US$ | 5 | 25 | 20 | 35 | 35 | 35 | 35 |

#### Setup of the PI

Raspbian is the Foundation’s official supported operating system. It can be installed with [NOOBS](https://www.raspberrypi.org/downloads/noobs/) or by downloading the [image](https://www.raspberrypi.org/downloads/raspbian/) and following the [installation guide](https://www.raspberrypi.org/documentation/installation/installing-images/README.md).

##### Installation instructions (Linux)

1) Run `df -h` to see all currently mounted devices.

2) Insert the SD card in your computer, mount it, and run `df -h` again. Identify the SD card, which will be listed as something like `/dev/mmcblk0p1` or `/dev/sdd1`. This are the partitions belonging to the whole SD card `/dev/mmcblk0` or `/dev/sdd`.

3) Unmount all partitions of the SD card by typing `umount /dev/mmcblk0p1`. If there is more than one partition starting with `/dev/mmcblk0` unmount this as well.

4) Use the `dd` command with `if=` for the input file and `of=` for the output file. The `bs=` command specifies the block size and is optional.

```bash
sudo dd bs=4M if=2016-03-18-raspbian-jessie.img of=/dev/mmcblk0
```
5) To see the progress run `sudo pkill -USR1 -n -x dd` in another terminal.

6) Run `sync` to savely unmount the SD card and remove it from the SD card reader.

7) Insert the SD card (or microSD card) into the PI and get started.
