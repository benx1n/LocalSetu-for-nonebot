# LocalSetu

基于nonebot v2的本地setu插件，目前仍在开发中，[hoshinobot版](https://github.com/benx1n/LocalSetu)

## 特点

- [x] 全功能支持私聊
- [x] 支持所有用户上传图片，提交删除图片申请，共同维护色图库
- [x] 支持按上传者，ID，TAG等模糊查询色图
- [x] 支持并发上传时自定义每张TAG
- [x] 自动审核上传图片，未通过自动提交申请
- [x] 自动获取上传图片P站id，中日文tag，是否r18，原图文件
- [x] 自动检测重复色图（以P站id及md5作唯一性约束）
- [x] 优化指令，空参时自动进入上传、审核模式，方便手机端操作
- [x] 权限分离，普通用户无权进行敏感操作，全申请均可自动推送至审核人员
- [x] 支持反和谐
- [x] 多线程并发，大幅优化效率
- [x] 数据存储基于sqlite，更加轻量
- [x] 支持上传男同图，指令区分（不是

## 部署方法

开发中

## DLC

- **私聊支持：（可能会引起其他插件部分功能异常）<br>**
    >修改Hoshinobot文件夹中`.\hoshino\priv.py`内check_priv函数，返回值改为True<br>
    >```
    >def check_priv(ev: CQEvent, require: int) -> bool:
    >if ev['message_type'] == 'group':
    >    return bool(get_user_priv(ev) >= require)
    >else:
    >    return True
    >```
    >注释Hoshinobot文件夹中`.\hoshino\msghandler.py`内下方代码<br>
    >```
    >if event.detail_type != 'group':
    >    return
    >```
## 指令说明
|  指令   | 必要参数  |可选参数|说明|
|  :----  | :----  | :---- |:----|
| **kkqyxp<br>kkntxp**|无| ID,@上传者,TAG |随机发送色图/男同图|
| **上传色图<br>上传男图** | 无 |[TAG][**IMAGE**]|支持批量，[TAG][**IMAGE**][TAG][**IMAGE**]<br>空参时进入上传模式,用户发送的所有图片均视为上传，无操作20秒后自动退出|
|**查看原图**|**[ID]**|无|可用于保存原画画质的色图|
|**删除色图**|**[ID]**|无|删除指定ID色图，非审核人员仅可删除本人上传的色图，删除他人色图请使用'申请删除色图'|
|**申请删除色图**|**[ID]**|无|提交色图删除申请，自动推送至审核人员|
|**修改TAG**|**[ID]**|[TAG]|修改指定ID的自定义TAG|
|**反和谐**|**[ID]**|无|色图被TX屏蔽时使用该指令，进行一次反和谐，后续发送色图均使用反和谐后文件|

## 以下指令仅限审核人员使用

|  指令   | 必要参数  |可选参数|说明|
|  :----  | :----  | :---- |:----|
|**审核色图上传<br>审核色图删除**|无|无|进入审核模式，每次发送待审核的色图<br>使用指令[保留][删除]后自动发送下一张,发送[退出审核]或20秒无操作自动退出|
|**快速审核**|**[ID]**|无|快速通过指定ID的申请（默认保留）|

## TODO

- [x] 改用Sqlite
- [ ] WEB控制台
- [ ] 在线图库API
- [ ] 更自由的组合条件查询
- [ ] 自动审核方式改为炼丹
- [ ] 优化无代理模式

## 感谢

[HoshinoBot](https://github.com/Ice-Cirno/HoshinoBot)<br>
[go-cqhttp](https://github.com/Mrs4s/go-cqhttp)<br>
[PicImageSearch](https://github.com/kitUIN/PicImageSearch)<br>
[pixivpy](https://github.com/upbit/pixivpy)<br>

## 开源协议

GPL-3.0 License
