[![996.icu](https://img.shields.io/badge/link-996.icu-red.svg)](https://996.icu)

## 后来……
我获得了一台M1 MacBook Pro 13 inch

## 2021.10.15更新
1. 如果在更新Monterey BETA 7及以上遇到诸如提示“固件错误”、反复重启但实际上更新没有完成之类的问题，请尝试使用这个https://github.com/acidanthera/RestrictEvents/releases/tag/1.0.5 ，同时保证OC设置中SecureBoot为disabled


## 2021.8.28更新
1. 更新键盘驱动以解决睡眠唤醒后失灵的问题
2. 添加有线网卡驱动但是没有启用，有需要可在OpenCore配置文件中自行启用
3. 增加为macOS 12 Monterey调试的EFI文件夹

### 重要说明：这里的EFI文件夹配置文件中均没有完整的三码信息，使用时请务必自行摇号并完整注入。正常注入以后可以开启iCloud、iMessage等服务。
=======

# OpenCore_EFI-For-DELL-G5-5587-适用于戴尔G5 5587的Hackintosh EFI
### 这里是专为Big Sur修改的EFI，Catalina没有用这个测试过，建议移步[Clover](https://github.com/Sosueyakiko/Clover_EFI-For-DELL-G5-5587)



### 感谢[Len](http://i.pcbeta.com/space-uid-4532202.html)、[黑果小兵](https://daliansky.net)和[彼岸花莫雨](https://www.cmbs-soft.com/user-info/1/)



## 机型配置
* CPU：Intel i5-8300H
* 显卡：Intel UHD630
* 显示屏：1920ｘ1080
* 声卡：ALC256（戴尔定制型号ALC3246）
* 无线网卡：重新使用Intel 9560(但仍然建议使用博通)

----



## 说明
#### EFI文件夹基于[[OC更新]机械革命8代9代标压OC 4.0.1稳定版更新](https://www.cmbs-soft.com/oc-8-9-th-4-0-0/comment-page-13/)修改而成。核显驱动属实给我整不会了，Catalina时用过来的玩意儿现在不好使了（话说本来那个就不太完美），只能找一个CPU和核显一致的其他机型EFI试一下，可以完美驱动核显以及加速，感谢大佬！



### 声卡（与Catalina相同）
1. 不使用VoodooHDA（内建扬声器正确但耳机插孔触点错误，发声频点混乱）。
2. AppleALC注入ID为97（不是ALC256通行的13/56等等常见值）。使用OpenCore中属性的方式注入。
3. 已知小问题：开机时接入耳机会导致系统识别不到内建扬声器（耳机孔正常）。开机之前记得拔下来就好了。
   
   
   
### 无线网卡
1. 博通依然是快乐的选择（功能更全），但是我的博通坏了，只能先换回Intel。这里没有放博通驱动，需要替换的可以参考[黑果小兵的教程](https://blog.daliansky.net/DW1820A_BCM94350ZAE-driver-inserts-the-correct-posture.html)
2. 使用[AirportItlwm和IntelBluetoothFirmware](https://github.com/OpenIntelWireless)驱动，但由于9560支持不完全，仅能应对一般Wi-Fi使用和蓝牙连接。可以开启aptX，AirDrop可以检测到设备但不能传输文件。随航需要接线。接力正常。需要完整功能仍然建议博通方案，若不愿意整驱动可以考虑换成其他[支持较好的Intel无线网卡](https://openintelwireless.github.io/itlwm/Compat.html)



### 一些其他的说明&关于这个EFI怎么来的
1. whatevergreen解决核芯显卡（没有独立显卡）的方案会导致没有DRM，AppleMusic可以开启无损选项但不能播放。
2. ~~EFI里PS2和I2C都有，后期会重做触摸板（~~
3. 不确定键盘上功能键的正确与否  因为前几天进水内置键盘坏了 日亚买了个JIS的交换用得过两周
4. 定制USB接口（包括读卡器但目前不包括显示输出）同时解决蓝牙驱动
5. ~~目前电源管理没解决~~

### TodoList：
1. - [ ] ~~外接显示器~~
2. - [x] 电源
3. - [x] 触摸板(其实我什么都没有做，尝试修复的时候它就变乖了！支持mac设置里的高级手势)
4. - [ ] OpenCore弄个GUI主题
5. - [x] 重做屏蔽独显补丁以优化续航


----

可能有纰漏，见谅。有什么其他bug或者需要在下做的留言就好。
