# S-DES小组作业
## 一 、作业任务

### 第一关：基本测试

**GUI用户交互界面首页**：用户选择加密或解密操作。

![1-1](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/1-1.png)

**加密界面**：用户输入需要加密的明文（需要在二进制8-bit模式和ASCII模式中进行选择）以及相关的密钥，得到加密后的密文

**二进制（8-bit）模式**：
如图，当输入明文为10011100，密钥为1111100000时，得到加密后的密文为11011011。

![1-2](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/1%20-2.png)

如果输入的内容不规范（非二进制8bit明文，非二进制10bit密钥），会进行相应的错误提示。


![1-3](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/1-3.png)


![1-4](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/1-4.png)


**解密界面**：用户输入需要解密的密文（同样需要在二进制8-bit模式和ASCII模式中进行选择）以及相关的密钥，得到解密后的明文。

**二进制（8-bit）模式：**

如图，当输入密文为11011011，密钥为1111100000时，得到解密后的明文与上述加密前的明文一致，为10011100

![1-5](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/1-5.png)

同样，如果输入的内容不规范（非二进制8bit密文，非二进制10bit密钥），也会进行相应的错误提示。


![1-6](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/1-6.png)



![1-7](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/1-7.png)


### 第二关：交叉测试

参考其他同学小组中的测试内容，可以验证我们的加密以及解密过程可以得到与其他小组同样的结果。
（参考小组的github链接：[https://github.com/KemingWu/SDES-CQU](https://github.com/KemingWu/SDES-CQU)；[https://github.com/cheney888-cyn/S-DES_2023](https://github.com/cheney888-cyn/S-DES_2023)）

**二进制（8-bit）模式下加密**：

明文：11001100

密钥：0101011010

密文：00010000

![2-1](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/2-1.png)


**二进制（8-bit）模式下解密**：

密文：00010000

密钥：0101011010

明文：11001100

![2-2](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/2-2.png)


**ASCII模式下加密**：

明文: Happy

密钥: 0110110100

密文: ªýOOÜ

![2-3](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/2-3.png)


**ASCII模式下解密:**

密文: ªýOOÜ

密钥: 0110110100

明文: Happy

![2-4](https://github.com/zzzxxxxzzz/S-DES/blob/main/image/2-4.png)



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

#  
##  三、开发者手册

### 1、系统结构 
S-DES（Simplified Data Encryption Standard）是一种简化版的数据加密标准算法，用于保护数据的机密性。

它使用8位密钥，对8位输入数据进行置换、替代和混淆操作，生成8位的加密结果。

根据S-DES算法的执行步骤，我们的S-DES系统结构如下：

#### 1.GUI用户界面（提供用户进行加解密交互操作的界面）

#### 2.基础加密（解密）操作：

（1）密钥生成：根据用户提供的10bits大小的密钥生成两个8bits的子密钥

（2）数据加密：依照S-DES算法的加密基本流程进行加密操作：初始置换（Initial Permutation）——轮函数（Round Function）（执行两次，第二次需要先交换左右部分并使用子密钥 K2）——逆初始分组（Inverse Initial Permutation）

（3）数据解密：依照S-DES算法的解密基本流程进行解密操作，解密流程与加密流程类似，相当于加密流程的逆操作（轮函数中需要第一次使用子密钥K2，第二次使用子密钥K1）。

### 2、关键代码组件
#### 1、SDES类（用于进行基础8bits明密文加解密功能的类）

（1） 需要用到的置换盒
``` java
// 定义S-DES算法所需要的置换表

private  static  final  int[] P10 = {3, 5, 2, 7, 4, 10, 1, 9, 8, 6};

private  static  final  int[] P8 = {6, 3, 7, 4, 8, 5, 10, 9};

private  static  final  int[] IP = {2, 6, 3, 1, 4, 8, 5, 7};
private  static  final  int[] IPInverse = {4, 1, 3, 5, 7, 2, 8, 6};
private  static  final  int[] EP = {4, 1, 2, 3, 2, 3, 4, 1};
private  static  final  int[] P4 = {2, 4, 3, 1};

