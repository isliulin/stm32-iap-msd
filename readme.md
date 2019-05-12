###STM32 Flash-Udisk-IAP

:项目说明
> STM32内部Flash模拟成U盘进行固件升级。系统上电之后在3S内检测到PC连接到STM32成功则进入Boot模式，此时将固件拖入U盘则完成升级，之后跳转到App区域执行用户代码。

注意事项：
+ BOOT区域划分20K
+ App区域从0x8004000开始
+ App程序进入Main后首先需要设置中断向量表地址并且在工程配置里设置flash起始地址是0x8004000
+ 支持HEX文件拖拽升级
+ 支持BIN文件拖拽升级


项目开发过程：
1. 在Win10上bin文件烧录过程会失败，Win7待测 2019050
    + Win7同样会失败，初步原因分析是数据丢包 20190507
    + bin文件写入地址不正确，重新实现写入flash数据的算法，解决了bug 20190511

2. 在Win10上hex文件只能烧录一次，Win7待测 20190506
    + Win7上也是只能烧录一次，已经找到BUG，再第二次烧录前flash没有擦除，问题已经解决 ----20190507
    + hex文件与LAB值解耦合，重新实现写入算法，解决了bug 20190511

3. 文件16.xK 希望可以裁剪到10K左右 ----20190511
    + 已经将BOOT从16K压缩到10.7K,希望可以压缩到10K以内。----20190512
