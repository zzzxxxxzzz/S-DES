# S-DES小组作业
## 一 、作业任务

### 第一关：基本测试
### 第二关：交叉测试
### 第三关：扩展功能

我们对该项目进行了拓展，实现了以ASCII码为明文输入和密文输出的功能。下面是加密演示：

明文：wasd

密钥：1010101011

 密文：IÄèÆ

![3-1](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/3-1.png)

下面是相应的解密演示：

![3-2](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/3-2.png)

解密成功，得到相应的明文，第三关通过。

### 第四关：暴力破解

第四关要求对使用了相同密钥的明密文对进行暴力破解，从而得到正确的密钥Key。

首先是对单组明密文对采取暴力破解：

明文：10101100

密文：10111000

得到四组密钥：1010110101、1011111111、1110110101、1111111111

用时：4毫秒

![4-1](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/4-1.png)

然后是对多组明密文对采取暴力破解：
|明文 | 10111001 |11111100|01101010|
|--|--|--|--|
| **密文** |**01011000**  |**10101010**|**01010101**|

得到两组密钥：1000101010、1100101010

用时：5毫秒

![4-2](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/4-2.png)


第四关测试通过。

### 第五关：封闭测试

在第四问中，我们对 明文：10101100 密文：10111000 

进行暴力破解得到以下四组正确的密钥：1**0**10110101、1**1**10110101、1**1**11111111、1**0**11111111、。

* **容易看出一组明密文对可以存在多组密钥Key**。

然后假设有
|明文分组 |  10101100 |10101111| 01010011|
|--|--|--|--|
| **密文分组** |**11001101**  |**11111011**|**11000001**|

![5-1](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/5-1.png)

得到密钥为：1**0**00011110、1**1**00011110
 
* **因此任意给定的明文空间会出现选择不同的密钥Ki≠Kj加密得到相同的密文，这是由于两串仅有第二位不相同的密钥会产生相同的子密钥。**


#
## 二、用户手册
### 1、S-DES算法介绍


* S-DES（Simplified Data Encryption Standard）是一种简化版的数据加密标准算法，用于保护数据的机密性。
* 它使用8位密钥，对8位输入数据进行置换、替代和混淆操作，生成8位的加密结果。

### 2、使用步骤
#### （1） 启动S-DES密码系统以进入主界面

![enter image description here](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/u-1.png)

#### （2） 选择加密或解密操作

加密界面：

![u-2](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/u-2.png)


解密界面：

![u-3](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/u-3.png)

#### （3）选择使用二进制（8-bit）模式或ASCII模式以进行加密或解密操作

![u-4](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/u-4.png)

#### （4）输入需要加密（解密）的明文（密文）及其密钥（密钥输入时默认隐藏，如需要显示可点击右侧的“显示密钥”），如果格式错误会有相应的提示

![u-5](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/u-5.png)
#### （5）得到加密（解密）之后的密文（明文）结果

![u-6](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/u-6.png)
