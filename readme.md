###STM32 Flash-Udisk-IAP

已知问题：
1. 在Win10上bin文件烧录过程会失败，Win7待测 20190506
    ----Win7同样会失败，初步原因是数据丢包 20190507
    ----bin文件写入地址不正确，重新实现写入flash数据的算法，解决了bug 20190511

2. 在Win10上hex文件只能烧录一次，Win7待测 20190506
    ----Win7上也是只能烧录一次，已经找到BUG，再第二次烧录前flash没有擦除，问题已经解决 ----20190507
    ----hex文件与LAB值解耦合，重新实现写入算法，解决了bug 20190511

3. 文件16.xK 希望可以裁剪到10K左右 ----20190511
    ----已经将BOOT从16K压缩到10.7K,希望可以压缩到10K以内。----20190512