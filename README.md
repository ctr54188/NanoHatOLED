# NanoHatOLED
[1]: https://img.shields.io/badge/license-MIT-brightgreen.svg
[2]: /LICENSE
[3]: https://img.shields.io/badge/PRs-welcome-brightgreen.svg
[4]: https://github.com/vinewx/NanoHatOLED/pulls
[5]: https://img.shields.io/badge/Issues-welcome-brightgreen.svg
[6]: https://github.com/vinewx/NanoHatOLED/issues/new
[7]: https://img.shields.io/badge/release-v1.0.4-blue.svg?
[8]: https://github.com/vinewx/NanoHatOLED/releases
[9]: https://img.shields.io/github/downloads/vinewx/NanoHatOLED/total
[![license][1]][2]
[![PRs Welcome][3]][4]
[![Issue Welcome][5]][6]
[![Release Version][7]][8]
[![Release Count][9]][8]

OpenWrt OLED display for NanoHatOLED.
## Depends / 依赖
- i2c-tools
- python-pillow / python3-pillow
- python-smbus / python3-smbus

## Compile / 编译
```bash
# Add NanoHatOLED feed to feeds.conf.default (Choose one of the following feeds)
# 请在feeds.conf.default中下方添加（二选一）
# For Python3.x: 
src-git NanoHatOLED https://github.com/vinewx/NanoHatOLED.git
# For Python2.7:
src-git NanoHatOLED https://github.com/vinewx/NanoHatOLED.git^e3285a3b37c7c34048c0ea108fa4ec18b49c0bfd

# Update & Install
# 更新并安装feeds软件包
./scripts/feeds update NanoHatOLED && ./scripts/feeds install nanohatoled

# Select this list item
# 选择要编译的包
# Extra packages -> nanohatoled
make menuconfig
```

## [Enable weather info / 显示天气](https://github.com/vinewx/NanoHatOLED/tree/weather) (Python3)
<img src="https://github.com/vinewx/NanoHatOLED/raw/weather/assets/k2_1.jpg" width="200" />

- 按压一次`F2`: 天气信息
- 再次按压`F2`: 系统信息

地区编码查询 -> [citycode.json](https://github.com/vinewx/NanoHatOLED/blob/weather/citycode.json)

```bash
# For depends / 安装依赖
opkg update && opkg install python3-requests
cd /usr/share/NanoHatOLED
wget -O Zpix.ttf https://github.com/vinewx/NanoHatOLED/raw/weather/nanohatoled/files/NanoHatOLED/Zpix.ttf
wget -O bakebit_nanohat_oled.py https://github.com/vinewx/NanoHatOLED/raw/weather/nanohatoled/files/NanoHatOLED/bakebit_nanohat_oled.py

# 先修改地区编码，再执行命令
# 例如：sed -i 's/101010100/101020100/g' bakebit_nanohat_oled.py
sed -i 's/101010100/修改为九位地区编码/g' bakebit_nanohat_oled.py

/etc/init.d/nanohatoled restart
```


## Thanks / 谢致 
- Based on: [friendlyarm/NanoHatOLED](https://github.com/friendlyarm/NanoHatOLED)
- [Weather API](https://www.sojson.com/api/weather.html)
- [zpix-pixel-font](https://github.com/SolidZORO/zpix-pixel-font)
- ![caiyun](http://caiyunapp.com/imgs/logo/logo-website.png)


<img src="https://github.com/vinewx/NanoHatOLED/raw/master/assets/k1.jpg" width="250" /> <img src="https://github.com/vinewx/NanoHatOLED/raw/master/assets/k2.jpg" width="250" /> <img src="https://github.com/vinewx/NanoHatOLED/raw/master/assets/k3.jpg" width="250" />
