# 重庆邮电大学定时健康打卡脚本

![School](https://img.shields.io/badge/School-CQUPT-green.svg)
![GitHub stars](https://img.shields.io/github/stars/ourongxing/CQUPT-Health-ClockIn)
![GitHub forks](https://img.shields.io/github/forks/ourongxing/CQUPT-Health-ClockIn)

### 事先声明

1. 本脚本仅供学习交流使用，请勿过分依赖。时刻注意每天是否打卡成功，如若失败，请手动打卡。
2. 本脚本仅限低风险地区学生使用，并且不要前往中高风险地区。如果身体出现新冠肺炎相关症状，请立即报告辅导员。
3. 本脚本需要自行抓包才能正常使用，为了避免脚本被滥用，在此我不会提供抓包相关教程。抓包工具 iOS 推荐 Stream，Android 推荐 HttpCanary，Windows 推荐 Fiddler，相比之下，Windows 下抓包最简单。
4. 开发者对使用或不使用本脚本造成的问题不负任何责任，不对脚本执行效果做出任何担保，原则上不提供任何形式的技术支持。

### 更新记录
- 2021.07.26 开源 `python` 版，仅支持腾讯云函数运行，原 `nodejs` 版不再维护。
- 2021.05.30 整理仓库时以为不再使用便删除了原仓库。
- 2021.02.26 仓库已归档，希望不再使用。正在使用的人也尽快删除仓库或者关闭自动打卡的 Workflow。

### 功能介绍
工作原理就是发送一个 POST 请求到 WE 重邮的服务器，这个 POST 请求的上传的信息包括
| 键名                        | 备注                                        | 默认值           |
| :-------------------------: | :--------------------------------------:    | :----------:     |
| openid                      | 个人唯一的身份标示，与微信绑定              | **自行抓包获得** |
| timestamp                   | 当前时间戳                                  | 自动获取         |
| mrdkkey                     | 通过日期 + 时间生成的字符串                 | 自动获取         |
| xh                          | 学号                                        | **手动输入**     |
| name                        | 姓名                                        | 自动获取     |
| xb                          | 性别                                        | 自动获取     |
| xxdz                        | 填写的详细地址                              | **手动输入**     |
| szdq                        | 填写的地址                                  | 自动获取         |
| localtionBig                | GPS 定位生成的位置信息                      | 自动获取         |
| localtionSmall              | GPS 定位生成的位置信息                      | 自动获取         |
| latitude                    | GPS 定位生成的纬度                          | 自动获取         |
| longitude                   | GPS 定位生成的经度                          | 自动获取         |
| ywjcqzbl                    | 新冠肺炎风险等级，非低风险地区请勿使用      | 低风险           |
| ywjchblj                    | 14 天内是否有中高风险地区旅居史             | 无               |
| xjzdywqzbl                  | 14 天内是否接触过有中高风险地区旅居史的人员 | 无               |
| twsfzc                      | 今日体温是否正常                            | 是               |
| ywytdzz                     | 今日是否有与新冠病毒感染有关的症状          | 无               |
| beizhu                      | 备注                                        | 无               |

### 使用方法
1. 修改相关信息并自行将 `index.py` 和 `ulits.py` 上传到腾讯云函数来实现定时执行，请不要使用 Github 来执行此类任务。
    ```python
    # 你的学号
    args.id = ""
 
    # 详细地址，建议精确到门牌号
    args.address = ""
 
    # 个人唯一的身份标示，与微信绑定，请自行抓包
    args.openid = ""
    
    # 推送，可以为空
    # 格式：qq:your key of qmsg 酱
    # 格式：tg:your key of tg 酱
    args.push = ""
    ```
2. 相关使用方法不再赘述，请自行抓包并了解 [腾讯云函数](https://console.cloud.tencent.com/scf) 以及 [Qmsg 酱](https://qmsg.zendee.cn/) 或 [Tg 酱](https://dianbao.vercel.app/) 的使用方法。

### Fork 后同步我的更新
可以参考[这个回答](https://www.zhihu.com/question/28676261/answer/1545698800)
