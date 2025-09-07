# Hackintosh


## 2025-09-07 更新 Tahoe beta5

2025 迎来最后一个黑苹果，应该也是最后一个更新:

- 支持 *睡眠* , 且 USB 欢迎正常(终于支持睡眠)
- 支持 ax210 蓝牙

不正常的硬件:

- Apple 移除了 AppleALC.kext 这个等正式版看怎么处理

## 2024-06-07 更新

- 更新了支持  Resizable Bar 的 BIOS
- BIOS 支持解锁 CFG Lock 但是重启失效

## 硬件配置

- 主板：Asrock EPC621D8A 
- BIOS版本：C621D8A2.15E 感谢[远景](bbs.pcbeta.com) @prmvb 提供
- CPU：Intel GOLD 6278 (LGA3647)
- 显卡：AMD 6950xt
- 内存：Samsung 32G x 4
- 硬盘：1. Intel P4500 for windows 2. C2000 pro for Mac OS 3.WD750 2T
- 网卡：Intel AX210 (隔空投送有问题)

## 软件说明

- 操作系统版本：macOS Sonoma 14.5
- OpenCore 版本：1.0.0
- RX6950 XT：仿冒 6900xt。
- SSD Trim：正常。
- 有个ssdt需要注意，Mac OS 需要屏蔽 P4500 参见 NOBR1A.aml, 但是你们可能不需要，或者跟我插的不是同一个 PCIE 接口，需要注意。
- CPU 名称已经被自定义, 请自行调整或者删除 NVRAM.4D1FDA02-38C7-4A6A-9CC6-4BCCA8B30102.revcpuname

## OpenCore 的更新

-  推荐[OCAuxiliaryTools](https://github.com/ic005k/OCAuxiliaryTools/), 手动更新太麻烦

## 存在的问题

- 睡眠不正常

## BIOS：关于 BIOS 的版本

如果你没有像我一样刷提供的 BIOS，请开启 AppleCpuPmCfgLock 和 AppleXcpmCfgLock， 并且移除 DSDT.aml, 不建议刷 BIOS，没有完全 PATCH.

OpenCore官方([这里](https://github.com/acidanthera/OpenCorePkg))提供了非常详尽的文档，建议阅读Configuration.pdf即知道每个配置项的存在的意义和作用了，待有时间再补充详细修改的地方。

## 致谢

- @[Cheney Veron](https://github.com/cheneyveron) 这个大佬在 BIOS 更新后给了我莫大的灵感和建议
- [Apple](https://www.apple.com)：研发的 macOS 系统
- [Clover EFI bootloader](https://sourceforge.net/projects/cloverefiboot/)：强大的通用操作系统引导器
- @[**vit9696**](https://github.com/vit9696)：制作 Lilu & AppleALC
- @[**cfmwan**](http://i.pcbeta.com/space-uid-8977.html)：分享的其EFI，其中有制作的修复睡眠、USB等功能的SSDT，见[这里](http://bbs.pcbeta.com/viewthread-1832693-1-1.html)
- [远景论坛](http://bbs.pcbeta.com) & [InsanelyMac](http://www.insanelymac.com)：提供交流的场所
