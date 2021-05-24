# :beers: UDS_S32K144_APP <a title="Hits" target="_blank" href="https://github.com/SummerFalls/UDS_S32K144_APP"><img src="https://hits.b3log.org/SummerFalls/UDS_S32K144_APP.svg"></a>

```c
/*
 *          ___           ___         ___
 *         /  /\         /  /\       /  /\
 *        /  /::\       /  /::\     /  /::\
 *       /  /:/\:\     /  /:/\:\   /  /:/\:\
 *      /  /:/~/::\   /  /:/~/:/  /  /:/~/:/
 *     /__/:/ /:/\:\ /__/:/ /:/  /__/:/ /:/
 *     \  \:\/:/__\/ \  \:\/:/   \  \:\/:/
 *      \  \::/       \  \::/     \  \::/
 *       \  \:\        \  \:\      \  \:\
 *        \  \:\        \  \:\      \  \:\
 *         \__\/         \__\/       \__\/
 */
```

## :book: 简介

S32K1xx 的 CAN 接 `周立功 USBCANFD-100U-mini`，使用 `ZCANPRO` 软件的 `ECU刷新` 功能进行测试。在加载相应的安全访问算法 DLL 文件 :package: [UDS_SecurityAccess][UDS_SecurityAccess] 之后，通过相应的 UDS 服务将 :package: [UDS_S32K144_FlashDriver][UDS_S32K144_FlashDriver] 的 hex 文件下载至 :package: [UDS_S32K144_Bootloader][UDS_S32K144_Bootloader] 在链接文件中为其预先指定起始地址的 RAM 空间中，并通过 `Flash Driver` 内实际包含的相应的 Flash 驱动函数的相对偏移量以及驱动函数本身来计算相应驱动函数的入口点在 RAM 内的偏移地址后，再通过函数指针的方式调用相应的编程、擦写、校验等 `Flash API` 以实现将 :package: [UDS_S32K144_APP][UDS_S32K144_APP] 烧写至 Flash 的 APP 片区，最终实现 `ECU刷新` 的整个 APP 更新流程。

:warning: 注意：S32K144-EVB 开发板需要 12V 独立供电，CAN Transceiver 方可正常工作。

:game_die: 已做通用性适配，目前一套代码理论同时支持多个型号，已测试 `S32K144` 和 `S32K118` 可以同时支持。

![Pic_ZCANPRO_ECU_Refresh][Pic_ZCANPRO_ECU_Refresh]

## :link: 关联工程

- :package: [UDS_SecurityAccess][UDS_SecurityAccess]
- :package: [UDS_S32K144_Bootloader][UDS_S32K144_Bootloader]
- :package: [UDS_S32K144_FlashDriver][UDS_S32K144_FlashDriver]
- :package: [UDS_S32K144_APP][UDS_S32K144_APP]

## :gear: 硬件 & 软件 需求

### 硬件需求

- S32K144-EVB
- J-Link
- USBCANFD-100U-mini
- 12V External Power Supply

### 软件需求

- S32 Design Studio for ARM Version 2.2
- ZCANPRO
- J-Flash

<br/>

---

<br/>

### :warning: 注意

![Pic_ZCANPRO_ECU_Refresh_Note_ProgramSession][Pic_ZCANPRO_ECU_Refresh_Note_ProgramSession]
![Pic_ZCANPRO_ECU_Refresh_Note_ResetECU][Pic_ZCANPRO_ECU_Refresh_Note_ResetECU]

[Pic_ZCANPRO_ECU_Refresh]: ./Pic_ZCANPRO_ECU_Refresh.png
[Pic_ZCANPRO_ECU_Refresh_Note_ProgramSession]: ./Pic_ZCANPRO_ECU_Refresh_Note_ProgramSession.png
[Pic_ZCANPRO_ECU_Refresh_Note_ResetECU]: ./Pic_ZCANPRO_ECU_Refresh_Note_ResetECU.png

[UDS_SecurityAccess]: https://github.com/SummerFalls/UDS_SecurityAccess
[UDS_S32K144_Bootloader]: https://github.com/SummerFalls/UDS_S32K144_Bootloader
[UDS_S32K144_FlashDriver]: https://github.com/SummerFalls/UDS_S32K144_FlashDriver
[UDS_S32K144_APP]: https://github.com/SummerFalls/UDS_S32K144_APP
