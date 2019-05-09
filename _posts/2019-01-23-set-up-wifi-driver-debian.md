---
title: "Cài đặt driver Intel Wireless WiFi"
published: true
---


## Supported Devices

```yaml
PCI: 8086:0082 Intel Corporation Centrino Advanced-N 6205 [Taylor Peak]
PCI: 8086:0083 Intel Corporation Centrino Wireless-N 1000 [Condor Peak]
PCI: 8086:0084 Intel Corporation Centrino Wireless-N 1000 [Condor Peak]
PCI: 8086:0085 Intel Corporation Centrino Advanced-N 6205 [Taylor Peak]
PCI: 8086:0087 Intel Corporation Centrino Advanced-N + WiMAX 6250 [Kilmer Peak]
PCI: 8086:0089 Intel Corporation Centrino Advanced-N + WiMAX 6250 [Kilmer Peak]
PCI: 8086:008A Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak]
PCI: 8086:008B Intel Corporation Centrino Wireless-N 1030 [Rainbow Peak]
PCI: 8086:0090 Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak]
PCI: 8086:0091 Intel Corporation Centrino Advanced-N 6230 [Rainbow Peak]
PCI: 8086:0885 Intel Corporation Centrino Wireless-N + WiMAX 6150
PCI: 8086:0886 Intel Corporation Centrino Wireless-N + WiMAX 6150
PCI: 8086:0887 Intel Corporation Centrino Wireless-N 2230
PCI: 8086:0888 Intel Corporation Centrino Wireless-N 2230
PCI: 8086:088E Intel Corporation Centrino Advanced-N 6235
PCI: 8086:088F Intel Corporation Centrino Advanced-N 6235
PCI: 8086:0890 Intel Corporation Centrino Wireless-N 2200
PCI: 8086:0891 Intel Corporation Centrino Wireless-N 2200
PCI: 8086:0892 Intel Corporation Centrino Wireless-N 135
PCI: 8086:0893 Intel Corporation Centrino Wireless-N 135
PCI: 8086:0894 Intel Corporation Centrino Wireless-N 105
PCI: 8086:0895 Intel Corporation Centrino Wireless-N 105
PCI: 8086:0896 Intel Corporation Centrino Wireless-N 130
PCI: 8086:0897 Intel Corporation Centrino Wireless-N 130
PCI: 8086:08AE Intel Corporation Centrino Wireless-N 100
PCI: 8086:08AF Intel Corporation Centrino Wireless-N 100
PCI: 8086:08B1 Intel Corporation Wireless 7260
PCI: 8086:08B2 Intel Corporation Wireless 7260
PCI: 8086:08B3 Intel Corporation Wireless 3160
PCI: 8086:08B4 Intel Corporation Wireless 3160
PCI: 8086:095A Intel Corporation Wireless 7265
PCI: 8086:095B Intel Corporation Wireless 7265
PCI: 8086:24F3 Intel Corporation Wireless 8260
PCI: 8086:24F4 Intel Corporation Wireless 8260
PCI: 8086:422B Intel Corporation Centrino Ultimate-N 6300
PCI: 8086:422C Intel Corporation Centrino Advanced-N 6200
PCI: 8086:4232 Intel Corporation WiFi Link 5100
PCI: 8086:4235 Intel Corporation Ultimate N WiFi Link 5300
PCI: 8086:4236 Intel Corporation Ultimate N WiFi Link 5300
PCI: 8086:4237 Intel Corporation PRO/Wireless 5100 AGN [Shiloh] Network Connection
PCI: 8086:4238 Intel Corporation Centrino Ultimate-N 6300
PCI: 8086:4239 Intel Corporation Centrino Advanced-N 6200
PCI: 8086:423A Intel Corporation PRO/Wireless 5350 AGN [Echo Peak] Network Connection
PCI: 8086:423B Intel Corporation PRO/Wireless 5350 AGN [Echo Peak] Network Connection
PCI: 8086:423C Intel Corporation WiMAX/WiFi Link 5150
PCI: 8086:423D Intel Corporation WiMAX/WiFi Link 5150
```

## Installation

### Cài đặt thông qua terminal với tool apt-get.

```liquid
# apt-get update && apt-get install firmware-iwlwifi
```
### Cài đặt thông qua các gói (package) với tool dpkg.

Download package firmware iwlwifi tại link: https://packages.debian.org/stretch/all/firmware-iwlwifi/download.
Sau khi download: package có dạng firmware-iwlwifi_xxx.deb.
Di chuyển tới thư mục vừa download package firmware và mở terminal cài đặt thông qua package manager (tool) dpkg với câu lệnh:

```liquid
# dpkg -i firmware-iwlwifi_xxx.deb
```
  ![Firmware](https://raw.githubusercontent.com/qndev/qndev.github.io/master/assets/images/firmware.png)

Chú ý: đối với package manager dpkg cần cài đặt các package phụ thuộc của package firmware-iwlwifi trước.
