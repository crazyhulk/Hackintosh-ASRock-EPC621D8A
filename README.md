# Hackintosh

## 硬件配置

- 主板：Asrock EPC621D8A 
- BIOS版本：C621D8A2.15E 感谢[远景](bbs.pcbeta.com) @prmvb 提供
- CPU：Intel GOLD 6278 (LGA3647)
- 显卡：Sapphire Radeon Nitro+ RX 590 Special Edition
- 内存：Samsung 32G x 2
- 硬盘：1. Intel P4500 for windows 2. C2000 pro for Mac OS
- 网卡：BCM943602CS

## 软件说明

- 操作系统版本：macOS big Sur 11.0.1
- OpenCore 版本：0.6.3
- RX590：正常。原生驱动。
- SSD Trim：正常。
- 有个ssdt需要注意，Mac OS 需要屏蔽 P4500 参见 NOBR1A.aml, 但是你们可能不需要，或者跟我插的不是同一个 PCIE 接口，需要注意。

### 2020-11-22 Update
- 支持 big sur
- 新添加 SSDT-RTC0-RANGE.aml, 解决 RTC 问题
- 默认使用 FakeSMC ，按需选择 VirtualSMC
- NVMeFix 按需选用，我有一颗不支持的 SSD 加了启动参数
- 机型信息等自己选用，自用的是 MacPro7,1 会有内存报错弹窗(memory modules misconfigured)

### 2020-07-25 Update
- 把原来的 `Devcie (CPXX) => Device (PRXX)` `_STA => XSTA` 让 SSDT 的 `Processor (CPXX)` 做替换

### 2020-07-24 Update
- 更新 BIOS 后会卡 ACPI，因为新的 DSDT 中的`Processor (CPXX)` => `Device (CPXX)` 而hackintosh 是要识别 Processor 关键字的
    之前的做法是修改原来的 DSDT，但是不太优雅，现在由 Processor 的 ssdt 代劳

## BIOS：关于 BIOS 的版本

如果你没有像我一样刷提供的 BIOS，请开启 AppleCpuPmCfgLock 和 AppleXcpmCfgLock， 并且移除 DSDT.aml

## 为何使用 OpenCore

OpenCore的思路是，通过完善ACPI表与UEFI固件来运行macOS：

- 一方面，通过修改ACPI表，可以让硬件的描述与操作方式符合苹果的ACPI规范，从而macOS可以正确的识别和操作硬件。
- 另一方面，通过修改UEFI固件，可以提供一些固件原本没有而macOS需要使用的方法，或者将现有方法改造为macOS可以调用的接口。

OpenCore官方([这里](https://github.com/acidanthera/OpenCorePkg))提供了非常详尽的文档，建议阅读Configuration.pdf即知道每个配置项的存在的意义和作用了，待有时间再补充详细修改的地方。

## 致谢

- @[Cheney Veron](https://github.com/cheneyveron) 这个大佬在 BIOS 更新后给了我莫大的灵感和建议
- [Apple](https://www.apple.com)：研发的 macOS 系统
- [Clover EFI bootloader](https://sourceforge.net/projects/cloverefiboot/)：强大的通用操作系统引导器
- @[**vit9696**](https://github.com/vit9696)：制作 Lilu & AppleALC
- @[**glasgood**](https://www.insanelymac.com/forum/profile/1077361-glasgood/)：写了一篇详细的Aorus Pro WiFi主板安装教程，见[这里](https://www.insanelymac.com/forum/topic/337837-glasgoods-macos-mojave-successguide-for-aorus-z390-pro/)
- @[**cfmwan**](http://i.pcbeta.com/space-uid-8977.html)：分享的其EFI，其中有制作的修复睡眠、USB等功能的SSDT，见[这里](http://bbs.pcbeta.com/viewthread-1832693-1-1.html)
- [远景论坛](http://bbs.pcbeta.com) & [InsanelyMac](http://www.insanelymac.com)：提供交流的场所
