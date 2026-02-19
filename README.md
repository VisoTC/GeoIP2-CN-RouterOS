# GeoIP-CN-RouterOS 简介

本项目会根据 [Loyalsoldier/geoip](https://github.com/Loyalsoldier/geoip) 生成用于导入到 RouterOS 的 GeoIP 数据文件，包含中国大陆的 IPv4 和 IPv6 地址数据。生成的文件格式为 RouterOS 的脚本格式（`.rsc`），可以直接在 RouterOS 上执行导入。

## 下载链接
| 项目 | 文件 | GitHub RAW | CDN 加速 |
|  :--:  |  :--:  |     :--:     |     :--:    |
| IPv4 列表 | CN.rsc | [点我下载](https://github.com/VisoTC/GeoIP2-CN-RouterOS/raw/refs/heads/release/CN.rsc) | [点我下载](https://fastly.jsdelivr.net/gh/VisoTC/GeoIP2-CN-RouterOS@release/CN.rsc) |
| IPv6 列表 | CN6.rsc | [点我下载](https://github.com/VisoTC/GeoIP2-CN-RouterOS/raw/refs/heads/release/CN6.rsc) | [点我下载](https://fastly.jsdelivr.net/gh/VisoTC/GeoIP2-CN-RouterOS@release/CN6.rsc) |

对于网络状况良好、无污染的环境下，建议选择 GitHub RAW 的方式下载，因为可以第一获取到最新的资源，因为服务器在境外，可能下载响应时间和速度稍长，但因为文件小，所以通常问题不大。

对于网络状况不好，存在污染的环境下，建议选择 CDN 加速的方式下载，速度非常快。但是可能存在缓存未更新的情况，很可能下载到旧的资源。

## 配置方式
可以直接下载rsc文件后，上传到 RouterOS，然后执行
``` RouterOS CLi
/import file-name=CN.rsc
```
也可以创建脚本，授予Policy: `read` `write` `test`，并且设置定时同步
``` RouterOS Script
# IPv4
/tool fetch url=https://raw.githubusercontent.com/VisoTC/GeoIP2-CN-RouterOS/refs/heads/release/CN.rsc dst-path=CN.rsc
/import file-name=CN.rsc
/file remove "CN.rsc"

# IPv6
/tool fetch url=https://raw.githubusercontent.com/VisoTC/GeoIP2-CN-RouterOS/refs/heads/release/CN6.rsc dst-path=CN6.rsc
/import file-name=CN6.rsc
/file remove "CN6.rsc"
```

## License

This project is licensed under the [GPL-3.0](https://github.com/VisoTC/GeoIP2-CN-RouterOS/blob/main/LICENSE). See the LICENSE file for details.

This project includes GeoIP data and logic derived from the following sources:

1. [Loyalsoldier/geoip](https://github.com/Loyalsoldier/geoip): Licensed under [CC-BY-SA-4.0](https://creativecommons.org/licenses/by-sa/4.0/) and [GPL-3.0](https://github.com/Loyalsoldier/geoip/blob/master/LICENSE-GPL).

2. MaxMind GeoLite2: This product includes GeoLite2 data created by MaxMind, available from https://www.maxmind.com.