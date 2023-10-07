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

例如：
|密钥|  子密钥1|子密钥2|
|---------------|--|--|
|1111111111| 11111111 |11111111|
|1011111111| 11111111 |11111111|
|0001010101| 00011011 |01101001|
|0101010101| 00011011 |01101001|
|1001001001| 11010010 |01000011|
|1101001001| 11010010 |01000011|


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
```
（2）子密钥的生成函数
```java
//S-DES的密钥生成函数
private  static  int[] generateKey(int[] key, boolean  isFirst){
// 使用P10表对密钥进行置换
int[] temp = new  int[10];
for(int  i=0;i<10;i++){
temp[i]=key[P10[i]-1];
}
int  shiftAmount = isFirst  ?  1:2; //子密钥1左移一位，子密钥2左移两位
// 循环左移
int[] shiftedKey = new  int[10];
for(int  i=0;i<10;i++){
if(i<5){
shiftedKey[i] = temp[(i+shiftAmount)%5];
}
else{
shiftedKey[i] = temp[(i+shiftAmount)%5+5];
}
}
//使用P8表生成子密钥
int[] subKey = new  int[8];
for(int  i=0;i<8;i++){
subKey[i]=shiftedKey[P8[i]-1];
}
return  subKey;
}
```
（3）轮函数中需要用到的替换盒S-Box函数
```java
//替换盒S-Box函数
private  static  int[] sBoxSubstitution(int[] data){
int[][] sBox1 = {
{1, 0, 3, 2},
{3, 2, 1, 0},
{0, 2, 1, 3},
{3, 1, 0, 2}
};
int[][] sBox2 = {
{0, 1, 2, 3},
{2, 3, 1, 0},
{3, 0, 1, 2},
{2, 1, 0, 3}
};

int[] output = new  int[4];
int  row1 = data[0]*2+data[3];
int  col1 = data[1]*2+data[2];
int  output1 = sBox1[row1][col1];
int  row2 = data[4]*2+data[7];
int  col2 = data[5]*2+data[6];
int  output2 = sBox2[row2][col2];

output[0]=output1/2;
output[1]=output1%2;
output[2]=output2/2;
output[3]=output2%2;
return  output;

}
```
（4）用于执行S-DES加密算法的加密函数
```java
// S-DES加密函数
public  static  String  encrypt(String  plainText, int[] key){
int[] data = new  int[8];
for(int  i=0;i<8;i++){
data[i] = Character.getNumericValue(plainText.charAt(i)); //将数据从char转为int类型
}
// 生成子密钥
int[] subKey1 = generateKey(key, true);
int[] subKey2 = generateKey(key, false);
//初始置换IP

int [] permutedData = new  int[8];
for(int  i=0;i<8;i++){
permutedData[i]=data[IP[i]-1];
}

//将IP置换后的8bit分为左右两组
int[] permutedDataLeft = new  int[4];
int[] permutedDataRight = new  int[4];
for(int  i=0;i<4;i++){
permutedDataLeft[i]=permutedData[i];
}

for(int  i=4;i<8;i++){
permutedDataRight[i-4]=permutedData[i];
}

//第一次执行轮函数F
//(1)扩展置换
int[] expandedData=new  int[8];
for(int  i=0;i<8;i++){
expandedData[i]=permutedDataRight[EP[i]-1];
}

//(2)轮密钥异或
for(int  i=0;i<8;i++){
expandedData[i]=expandedData[i] ^ subKey1[i];
}

//(3)使用替换盒S-Box
int[] substitutedData = sBoxSubstitution(expandedData);
//(4)直接置换

int[] permutedData4 = new  int[4];
for(int  i=0;i<4;i++){
permutedData4[i] = substitutedData[P4[i]-1];

}

//左部分原始数据和轮函数结果进行异或
int[] temp1 = new  int[4];
for(int  i=0;i<4;i++){
temp1[i] = permutedDataLeft[i]^permutedData4[i];
}

//第二次执行轮函数F
//(1)扩展置换
expandedData = new  int[8];
for(int  i=0;i<8;i++){
expandedData[i]=temp1[EP[i]-1];
}

//(2)轮密钥异或
for(int  i=0;i<8;i++){
expandedData[i]=expandedData[i] ^ subKey2[i];
}

//(3)使用替换盒S-Box
substitutedData = sBoxSubstitution(expandedData);

//(4)直接置换
permutedData4 = new  int[4];
for(int  i=0;i<4;i++){
permutedData4[i] = substitutedData[P4[i]-1];
}

//右部分原始数据和轮函数结果进行异或
int[] temp2 = new  int[4];
for(int  i=0;i<4;i++){
temp2[i]=permutedDataRight[i]^permutedData4[i]; //此时的密文为temp2+temp1(未进行最终置换)
}

//进行最终置换

int[] tempData = new  int[8];
int[] cipherText = new  int[8];
for(int  i=0;i<8;i++){
if(i<4){
tempData[i]=temp2[i];
}
else{
tempData[i]=temp1[i-4];
}
}

for(int  i=0;i<8;i++){
cipherText[i]=tempData[IPInverse[i]-1];
}

// 转换为字符串
StringBuilder  result = new  StringBuilder();
for (int  i = 0; i < 8; i++) {
result.append(cipherText[i]);
}
return  result.toString();
}
```
（5）用于执行S-DES解密算法的解密函数
```java
//S-DES解密函数
public  static  String  decrypt(String  ciphperText, int[] key){
int[] data = new  int[8];
for(int  i=0;i<8;i++){
data[i] = Character.getNumericValue(ciphperText.charAt(i)); //将数据从char转为int类型

}

// 生成子密钥
int[] subKey1 = generateKey(key, true);
int[] subKey2 = generateKey(key, false);
//初始置换IP
int [] permutedData = new  int[8];
for(int  i=0;i<8;i++){
permutedData[i]=data[IP[i]-1];
}

//将IP置换后的8bit分为左右两组
int[] permutedDataLeft = new  int[4];
int[] permutedDataRight = new  int[4];
for(int  i=0;i<4;i++){
permutedDataLeft[i]=permutedData[i];
}

for(int  i=4;i<8;i++){
permutedDataRight[i-4]=permutedData[i];
}

//第一次执行轮函数F

//(1)扩展置换
int[] expandedData=new  int[8];
for(int  i=0;i<8;i++){
expandedData[i]=permutedDataRight[EP[i]-1];
}

//(2)轮密钥异或
for(int  i=0;i<8;i++){
expandedData[i]=expandedData[i] ^ subKey2[i];
}

//(3)使用替换盒S-Box
int[] substitutedData = sBoxSubstitution(expandedData);

//(4)直接置换
int[] permutedData4 = new  int[4];
for(int  i=0;i<4;i++){
permutedData4[i] = substitutedData[P4[i]-1];
}

//左部分原始数据和轮函数结果进行异或
int[] temp1 = new  int[4];
for(int  i=0;i<4;i++){
temp1[i] = permutedDataLeft[i]^permutedData4[i];
}

//第二次执行轮函数F

//(1)扩展置换
expandedData = new  int[8];
for(int  i=0;i<8;i++){
expandedData[i]=temp1[EP[i]-1];
}

//(2)轮密钥异或
for(int  i=0;i<8;i++){
expandedData[i]=expandedData[i] ^ subKey1[i];
}

//(3)使用替换盒S-Box
substitutedData = sBoxSubstitution(expandedData);

//(4)直接置换
permutedData4 = new  int[4];
for(int  i=0;i<4;i++){
permutedData4[i] = substitutedData[P4[i]-1];
}

//右部分原始数据和轮函数结果进行异或
int[] temp2 = new  int[4];
for(int  i=0;i<4;i++){
temp2[i]=permutedDataRight[i]^permutedData4[i]; //此时的密文为temp2+temp1(未进行最终置换)

}

//进行最终置换
int[] tempData = new  int[8];
int[] plainText = new  int[8];
for(int  i=0;i<8;i++){
if(i<4){
tempData[i]=temp2[i];
}
else{
tempData[i]=temp1[i-4];
}
}

for(int  i=0;i<8;i++){
plainText[i]=tempData[IPInverse[i]-1];
}

// 转换为字符串
StringBuilder  result = new  StringBuilder();
for (int  i = 0; i < 8; i++) {
result.append(plainText[i]);
}

return  result.toString();
}
```

####  2、用户界面设计

（1）主界面
```java
import javax.swing.*;  
import java.awt.event.ActionEvent;  
import java.awt.event.ActionListener;  
import java.awt.Font;  
public class UI extends JFrame{  
Encrypt_GUI encrypt_GUI;  
Decrypt_GUI decrypt_GUI;  
JLabel welcomeLabel;  
JButton decryptButton,encryptButton;  
  
UI(){  
JFrame frame = new JFrame();  
frame.setTitle("S-DES加密系统");  
frame.setSize(800, 600);  
frame.setDefaultCloseOperation(JFrame._EXIT_ON_CLOSE_);  
frame.setLocationRelativeTo(null);  
frame.setResizable(false);  
frame.setLayout(null);  
  
//设置基础进入界面  
welcomeLabel = new JLabel("欢迎使用S-DES加密系统！");  
welcomeLabel.setFont(new Font("宋体", Font._TYPE1_FONT_, 30));  
welcomeLabel.setBounds(230, 120, 400, 130);  
encryptButton = new JButton("加密明文");  
encryptButton.setFont(new Font("黑体", Font._PLAIN_, 18));  
encryptButton.setBounds(220, 315, 130, 50);  
encryptButton.addActionListener(new ActionListener() {  
public void actionPerformed(ActionEvent e){  
frame.setVisible(false);  
encrypt_GUI = new Encrypt_GUI();  
}  
});  
decryptButton = new JButton("解密密文");  
decryptButton.setBounds(450, 315, 130, 50);  
decryptButton.setFont(new Font("黑体", Font._PLAIN_, 18));  
decryptButton.addActionListener(new ActionListener() {  
public void actionPerformed(ActionEvent e){  
frame.setVisible(false);  
decrypt_GUI = new Decrypt_GUI();  
}  
});  
frame.add(welcomeLabel);  
frame.add(encryptButton);  
frame.add(decryptButton);  
frame.setVisible(true);  
  
}  
}
```

（2）加密界面
```java
<![endif]-->

import java.awt.Dimension;  
import java.awt.Font;  
import java.awt.event.ActionEvent;  
import java.awt.event.ActionListener;  
import java.awt.event.ItemEvent;  
import java.awt.event.ItemListener;  
import javax.swing.*;  
  
public class Encrypt_GUI {  
JTextField dataField;  
JTextArea resulTextArea;  
JPasswordField keyJPasswordField;  
JLabel dataJLabel, keyJLabel, resultJLabel, welcomeLabel;  
JCheckBox checkBox;  
JButton button1, button2;  
JOptionPane warning;  
String dataString, cipherText;  
char[] keyChar;  
int[] key;  
Box box_H_01, box_H_02, box_H_03, box_V;  
  
  
Encrypt_GUI(){  
init();  
}  
void init(){  
JFrame frame = new JFrame("Encrypt_GUI");  
  
//初始化UI布置组件  
box_H_01=Box._createHorizontalBox_();  
box_H_02=Box._createHorizontalBox_();  
box_H_03=Box._createHorizontalBox_();  
box_V=Box._createVerticalBox_();  
  
//设置窗体对象的属性值  
frame.setTitle("加密界面");  
frame.setSize(900, 650);  
frame.setDefaultCloseOperation(JFrame._DISPOSE_ON_CLOSE_);  
frame.setLocationRelativeTo(null);  
frame.setResizable(false);  
frame.setLayout(null);  
  
//设置欢迎标签  
welcomeLabel = new JLabel("欢迎使用S-DES加密系统！");  
welcomeLabel.setFont(new Font("宋体", Font._TYPE1_FONT_, 30));  
welcomeLabel.setBounds(265, 40 , 400, 80);  
  
// 明文输入模式选择按钮  
JRadioButton textModeRadioButton = new JRadioButton("二进制(8-bit)模式");  
JRadioButton asciiModeRadioButton = new JRadioButton("ASCII模式");  
ButtonGroup modeButtonGroup = new ButtonGroup();  
modeButtonGroup.add(textModeRadioButton);  
modeButtonGroup.add(asciiModeRadioButton);  
textModeRadioButton.setSelected(true);  
textModeRadioButton.setFont(new Font("黑体", Font._PLAIN_, 18));  
asciiModeRadioButton.setFont(new Font("黑体", Font._PLAIN_, 18));  
textModeRadioButton.setBounds(250, 115, 200, 30);  
asciiModeRadioButton.setBounds(500, 115, 120, 30);  
  
//明文输入  
dataJLabel=new JLabel("明文：");  
dataJLabel.setFont(new Font("黑体", Font._PLAIN_, 18));  
dataField=new JTextField();  
dataField.setPreferredSize(new Dimension(150, 25));  
dataField.setFont(new Font("宋体", Font._PLAIN_, 18));  
  
//密钥输入  
keyJLabel=new JLabel("密钥：");  
keyJLabel.setFont(new Font("黑体", Font._PLAIN_, 18));  
keyJPasswordField = new JPasswordField();  
keyJPasswordField.setEchoChar('*');  
keyJPasswordField.setPreferredSize(new Dimension(150,25));  
keyJPasswordField.setFont(new Font("宋体", Font._PLAIN_, 18));  
  
//密钥可视按钮  
checkBox= new JCheckBox("显示密钥");  
checkBox.setSize(new Dimension(70, 35));  
checkBox.setFont(new Font("黑体",Font._TYPE1_FONT_,21));  
checkBox.addItemListener(new ItemListener() {  
public void itemStateChanged(ItemEvent e){  
if(e.getStateChange()==ItemEvent._SELECTED_){  
keyJPasswordField.setEchoChar((char)0);  
}  
else{  
keyJPasswordField.setEchoChar('*');  
}  
}  
});  
checkBox.setBounds(650, 255, 130, 70);  
  
//密文显示  
resultJLabel=new JLabel("密文：");  
resultJLabel.setFont(new Font("黑体", Font._PLAIN_, 18));  
resulTextArea=new JTextArea();  
resulTextArea.setPreferredSize(new Dimension(180, 80));  
resulTextArea.setFont(new Font("宋体", Font._PLAIN_, 18));  
resulTextArea.setEditable(false);  
  
//加密按钮  
button1=new JButton();  
button1.setText("加密");  
button1.setFont(new Font("黑体", Font._PLAIN_, 19));  
button1.setSize(new Dimension(100,50));  
button1 = new JButton();  
button1.setText("加密");  
button1.setFont(new Font("黑体", Font._PLAIN_, 19));  
button1.setSize(new Dimension(100, 50));  
// 加密按钮  
button1.addActionListener(new ActionListener() {  
public void actionPerformed(ActionEvent e) {  
if (textModeRadioButton.isSelected()) {  
// 文本模式  
String dataInput = dataField.getText().trim();  
String keyInput = new String(keyJPasswordField.getPassword());  
if (!isValidBinary(dataInput)) {  
warning._showMessageDialog_(frame, "请输入8位的二进制明文！", "警告", JOptionPane._WARNING_MESSAGE_);  
} else if (!isValidBinaryKey(keyInput)) {  
warning._showMessageDialog_(frame, "请输入10位的二进制密钥！", "警告", JOptionPane._WARNING_MESSAGE_);  
} else {  
// 获取明文  
dataString = dataInput;  
// 获取密钥  
keyChar = keyJPasswordField.getPassword();  
key = new int[keyChar.length];  
for (int i = 0; i < keyChar.length; i++) {  
key[i] = Character._getNumericValue_(keyChar[i]);  
}  
cipherText = SDES._encrypt_(dataString, key);  
resulTextArea.setText(cipherText.toString());  
}  
} else if (asciiModeRadioButton.isSelected()) {  
// ASCII模式  
if (dataField.getText().trim().equals("")) {  
warning._showMessageDialog_(frame, "明文不能为空！", "警告", JOptionPane._WARNING_MESSAGE_);  
} else if (keyJPasswordField.getPassword().length != 10) {  
warning._showMessageDialog_(frame, "密钥长度必须为10bit！", "警告", JOptionPane._WARNING_MESSAGE_);  
} else {  
// 获取明文  
String asciiText = dataField.getText();  
// 获取密钥  
keyChar = keyJPasswordField.getPassword();  
key = new int[keyChar.length];  
for (int i = 0; i < keyChar.length; i++) {  
key[i] = Character._getNumericValue_(keyChar[i]);  
}  
// 将ASCII码转换为二进制字符串  
StringBuilder binaryText = new StringBuilder();  
for (char c : asciiText.toCharArray()) {  
String binaryChar = Integer._toBinaryString_(c);  
while (binaryChar.length() < 8) {  
binaryChar = "0" + binaryChar;  
}  
binaryText.append(binaryChar);  
}  
  
// 每8位进行切割，并放入字符串数组  
int blockCount = binaryText.length() / 8;  
String[] binaryBlocks = new String[blockCount];  
for (int i = 0; i < blockCount; i++) {  
binaryBlocks[i] = binaryText.substring(i * 8, (i + 1) * 8);  
}  
// 初始化一个StringBuilder来存储加密后的二进制块  
StringBuilder encryptedText = new StringBuilder();  
  
// 对每个8位的二进制块进行SDES加密  
for (String block : binaryBlocks) {  
cipherText = SDES._encrypt_(block, key); // 假设SDES.encrypt接受8位的二进制输入  
encryptedText.append(cipherText);  
}  
  
// 将加密后的二进制块转换为ASCII码形式  
StringBuilder asciiCipherText = new StringBuilder();  
for (int i = 0; i < encryptedText.length(); i += 8) {  
String binaryChar = encryptedText.substring(i, i + 8);  
int asciiValue = Integer._parseInt_(binaryChar, 2);  
char asciiChar = (char) asciiValue;  
asciiCipherText.append(asciiChar);  
}  
  
resulTextArea.setText(asciiCipherText.toString());  
}  
}  
}  
// 定义一个辅助方法来验证二进制输入是否有效  
private boolean isValidBinary(String input) {  
// 使用正则表达式验证是否是8位二进制输入  
return input.matches("[01]{8}");  
}  
// 定义一个辅助方法来验证二进制密钥是否有效  
private boolean isValidBinaryKey(String input) {  
// 使用正则表达式验证是否是10位二进制输入  
return input.matches("[01]{10}");  
}  
});  
  
  
button1.setBounds(265, 500, 160, 40);  
  
//返回按钮  
button2 = new JButton("返回");  
button2.setFont(new Font("黑体", Font._PLAIN_, 19));  
button2.setSize(new Dimension(100,50));  
button2.addActionListener(new ActionListener() {  
public void actionPerformed(ActionEvent e){  
UI uI = new UI();  
frame.dispose();  
}  
});  
button2.setBounds(465, 500, 160, 40);  
  
//布置各个组件  
box_H_01.add(dataJLabel);  
box_H_01.add(Box._createHorizontalStrut_(5));  
box_H_01.add(dataField);  
  
box_H_02.add(keyJLabel);  
box_H_02.add(Box._createHorizontalStrut_(5));  
box_H_02.add(keyJPasswordField);  
  
box_H_03.add(resultJLabel);  
box_H_03.add(Box._createHorizontalStrut_(5));  
box_H_03.add(resulTextArea);  
  
box_V.add(box_H_01);  
box_V.add(Box._createVerticalStrut_(40));  
box_V.add(box_H_02);  
box_V.add(Box._createVerticalStrut_(30));  
box_V.add(box_H_03);  
box_V.setBounds(200, 170, 450, 300);  
  
frame.add(welcomeLabel);  
frame.add(box_V);  
frame.add(checkBox);  
frame.add(button1);  
frame.add(button2);  
frame.add(textModeRadioButton);  
frame.add(asciiModeRadioButton);  
frame.setVisible(true);  
}  
}
```


（3）解密界面
```java
<![endif]-->

mport javax.swing.*;  
import java.awt.event.ActionEvent;  
import java.awt.event.ActionListener;  
import java.awt.event.ItemEvent;  
import java.awt.event.ItemListener;  
import java.awt.Dimension;  
import java.awt.Font;  
  
public class Decrypt_GUI {  
JTextField dataField;  
JTextArea resulTextArea;  
JPasswordField keyJPasswordField;  
JLabel dataJLabel, keyJLabel, resultJLabel, welcomeLabel;  
JCheckBox checkBox;  
JButton button1, button2;  
JOptionPane warning;  
String dataString, plainText;  
char[] keyChar;  
int[] key;  
Box box_H_01, box_H_02, box_H_03, box_V;  
SDES sDes;  
  
  
Decrypt_GUI(){  
init();  
}  
void init(){  
JFrame frame = new JFrame("Encrypt_GUI");  
  
//初始化UI布置组件  
box_H_01=Box._createHorizontalBox_();  
box_H_02=Box._createHorizontalBox_();  
box_H_03=Box._createHorizontalBox_();  
box_V=Box._createVerticalBox_();  
  
//设置窗体对象的属性值  
frame.setTitle("解密界面");  
frame.setSize(900, 650);  
frame.setDefaultCloseOperation(JFrame._DISPOSE_ON_CLOSE_);  
frame.setLocationRelativeTo(null);  
frame.setResizable(false);  
frame.setLayout(null);  
  
//设置欢迎标签  
welcomeLabel = new JLabel("欢迎使用S-DES解密系统！");  
welcomeLabel.setFont(new Font("黑体", Font._PLAIN_, 30));  
welcomeLabel.setBounds(265, 40 , 400, 80);  
  
// 明文输入模式选择按钮  
JRadioButton textModeRadioButton = new JRadioButton("二进制(8-bit)模式");  
JRadioButton asciiModeRadioButton = new JRadioButton("ASCII模式");  
ButtonGroup modeButtonGroup = new ButtonGroup();  
modeButtonGroup.add(textModeRadioButton);  
modeButtonGroup.add(asciiModeRadioButton);  
textModeRadioButton.setSelected(true);  
textModeRadioButton.setFont(new Font("黑体", Font._PLAIN_, 18));  
asciiModeRadioButton.setFont(new Font("黑体", Font._PLAIN_, 18));  
textModeRadioButton.setBounds(250, 115, 200, 30);  
asciiModeRadioButton.setBounds(500, 115, 120, 30);  
  
//密文输入  
dataJLabel=new JLabel("密文：");  
dataJLabel.setFont(new Font("黑体", Font._PLAIN_, 18));  
dataField=new JTextField();  
dataField.setPreferredSize(new Dimension(150, 25));  
dataField.setFont(new Font("宋体", Font._PLAIN_, 18));  
  
//密钥输入  
keyJLabel=new JLabel("密钥：");  
keyJLabel.setFont(new Font("黑体", Font._PLAIN_, 18));  
keyJPasswordField = new JPasswordField();  
keyJPasswordField.setEchoChar('*');  
keyJPasswordField.setPreferredSize(new Dimension(150,25));  
keyJPasswordField.setFont(new Font("宋体", Font._PLAIN_, 18));  
  
//密钥可视按钮  
checkBox= new JCheckBox("显示密钥");  
checkBox.setSize(new Dimension(70, 35));  
checkBox.setFont(new Font("黑体",Font._TYPE1_FONT_,21));  
checkBox.addItemListener(new ItemListener() {  
public void itemStateChanged(ItemEvent e){  
if(e.getStateChange()==ItemEvent._SELECTED_){  
keyJPasswordField.setEchoChar((char)0);  
}  
else{  
keyJPasswordField.setEchoChar('*');  
}  
}  
});  
checkBox.setBounds(650, 255, 130, 70);  
  
//明文显示  
resultJLabel=new JLabel("明文：");  
resultJLabel.setFont(new Font("黑体", Font._PLAIN_, 18));  
resulTextArea=new JTextArea();  
resulTextArea.setPreferredSize(new Dimension(180, 80));  
resulTextArea.setFont(new Font("宋体", Font._PLAIN_, 18));  
resulTextArea.setEditable(false);  
  
//解密按钮  
button1=new JButton();  
button1.setText("解密");  
button1.setFont(new Font("黑体", Font._PLAIN_, 19));  
button1.setSize(new Dimension(100,50));  
button1.addActionListener(new ActionListener() {  
public void actionPerformed(ActionEvent e) {  
if (textModeRadioButton.isSelected()){  
// 文本模式  
String dataInput = dataField.getText().trim();  
String keyInput = new String(keyJPasswordField.getPassword());  
if (!isValidBinary(dataInput)) {  
warning._showMessageDialog_(frame, "请输入8位的二进制密文！", "警告", JOptionPane._WARNING_MESSAGE_);  
} else if (!isValidBinaryKey(keyInput)) {  
warning._showMessageDialog_(frame, "密钥长度必须为10bit！", "警告", JOptionPane._WARNING_MESSAGE_);  
} else {  
//获取密文  
dataString = dataField.getText();  
//获取密钥  
keyChar = keyJPasswordField.getPassword();  
key = new int[keyChar.length];  
for (int i = 0; i < keyChar.length; i++) {  
key[i] = Character._getNumericValue_(keyChar[i]);  
}  
plainText = SDES._decrypt_(dataString, key);  
resulTextArea.setText(plainText);  
}  
}  
else if (asciiModeRadioButton.isSelected())  
if (dataField.getText().trim().equals("")) {  
warning._showMessageDialog_(frame, "密文不能为空！", "警告", JOptionPane._WARNING_MESSAGE_);  
} else if (keyJPasswordField.getPassword().length != 10) {  
warning._showMessageDialog_(frame, "密钥长度必须为10bit！", "警告", JOptionPane._WARNING_MESSAGE_);  
} else {  
// 获取密文  
String cipherText = dataField.getText();  
// 获取密钥  
keyChar = keyJPasswordField.getPassword();  
key = new int[keyChar.length];  
for (int i = 0; i < keyChar.length; i++) {  
key[i] = Character._getNumericValue_(keyChar[i]);  
}  
  
// 将密文转换为二进制字符串  
StringBuilder binaryText = new StringBuilder();  
for (char c : cipherText.toCharArray()) {  
String binaryChar = Integer._toBinaryString_(c);  
while (binaryChar.length() < 8) {  
binaryChar = "0" + binaryChar;  
}  
binaryText.append(binaryChar);  
}  
  
// 每8位进行切割，并放入字符串数组  
int blockCount = binaryText.length() / 8;  
String[] binaryBlocks = new String[blockCount];  
for (int i = 0; i < blockCount; i++) {  
binaryBlocks[i] = binaryText.substring(i * 8, (i + 1) * 8);  
}  
  
// 初始化一个StringBuilder来存储解密后的二进制块  
StringBuilder decryptedText = new StringBuilder();  
  
// 对每个8位的二进制块进行SDES解密  
for (String block : binaryBlocks) {  
String plaintextBlock = SDES._decrypt_(block, key); // 使用SDES解密  
decryptedText.append(plaintextBlock);  
}  
  
// 将解密后的二进制块转换为ASCII码形式  
StringBuilder asciiPlaintext = new StringBuilder();  
for (int i = 0; i < decryptedText.length(); i += 8) {  
String binaryChar = decryptedText.substring(i, i + 8);  
int asciiValue = Integer._parseInt_(binaryChar, 2);  
char asciiChar = (char) asciiValue;  
asciiPlaintext.append(asciiChar);  
}  
  
resulTextArea.setText(asciiPlaintext.toString());  
  
}  
}  
// 定义一个辅助方法来验证二进制输入是否有效  
private boolean isValidBinary(String input) {  
// 使用正则表达式验证是否是8位二进制输入  
return input.matches("[01]{8}");  
};  
// 定义一个辅助方法来验证二进制密钥是否有效  
private boolean isValidBinaryKey(String input) {  
// 使用正则表达式验证是否是10位二进制输入  
return input.matches("[01]{10}");  
}  
});  
button1.setBounds(265, 500, 160, 40);  
  
//返回按钮  
button2 = new JButton("返回");  
button2.setFont(new Font("黑体", Font._PLAIN_, 19));  
button2.setSize(new Dimension(100,50));  
button2.addActionListener(new ActionListener() {  
public void actionPerformed(ActionEvent e){  
UI uI = new UI();  
frame.dispose();  
}  
});  
button2.setBounds(465, 500, 160, 40);  
  
//布置各个组件  
box_H_01.add(dataJLabel);  
box_H_01.add(Box._createHorizontalStrut_(5));  
box_H_01.add(dataField);  
  
box_H_02.add(keyJLabel);  
box_H_02.add(Box._createHorizontalStrut_(5));  
box_H_02.add(keyJPasswordField);  
  
box_H_03.add(resultJLabel);  
box_H_03.add(Box._createHorizontalStrut_(5));  
box_H_03.add(resulTextArea);  
  
box_V.add(box_H_01);  
box_V.add(Box._createVerticalStrut_(40));  
box_V.add(box_H_02);  
box_V.add(Box._createVerticalStrut_(30));  
box_V.add(box_H_03);  
box_V.setBounds(200, 170, 450, 300);  
  
frame.add(welcomeLabel);  
frame.add(box_V);  
frame.add(checkBox);  
frame.add(button1);  
frame.add(button2);  
frame.add(textModeRadioButton);  
frame.add(asciiModeRadioButton);  
frame.setVisible(true);  
}  
}
```

#### 3、 暴力破解算法
```java
import java.util.Scanner;  
import java.text.DecimalFormat;  
  
public class test {  
public static void main(String[] args) {  
System.out.println("已知明密文对的数量");  
Scanner scan = new Scanner(System.in);  
int number = scan.nextInt();//记录明密文对数量  
String[] PlaintextArr = new String[number];//记录明文  
String[] CiphertextArr = new String[number];//记录密文  
int[][] keyarray = new int[10][10];//记录可能的密钥  
int keynum = 0;//记录密钥数量  
  
//输入明密文对  
int inputcount = 0;  
while (inputcount<number){  
System.out.print("请输入第"+(inputcount+1)+"条明文");  
PlaintextArr[inputcount] = scan.next();  
System.out.print("请输入第"+(inputcount+1)+"条密文");  
CiphertextArr[inputcount] = scan.next();  
inputcount++;  
}  
// 获取当前时间的毫秒数，作为起始时间  
long startTime = System.currentTimeMillis();  
  
int [] key = new int [10];//存储正确的密钥  
for(int n =0;n<number;n++){  
if(keynum==0){//如果还未找到正确的密钥  
for(int i=0;i<1024;i++){//遍历1024个二进制数  
String binary = Integer.toBinaryString(i);  
int length = binary.length();  
  
while(length<10){  
binary = "0" + binary;  
length++;  
}  
for(int j=0;j<10;j++){  
key[j] = binary.charAt(j) - '0';  
}  
String test = SDES.encrypt(PlaintextArr[n],key);  
if(test.equals(CiphertextArr[n])){//如果生成的密文和存储的密文相同  
for(int m = 0;m<10;m++){  
keyarray[keynum][m] = key[m];//存储密钥  
}  
keynum++;  
}  
}  
}  
  
else{//如果此时已找到正确的密钥，就直接将已产生密钥带入后续名密文对中，则无需再次遍历  
int update = 0;  
int [][]temp = new int[keynum][10];//用于更新正确的密钥库  
for(int i=0;i<keynum;i++){  
for(int j=0;j<10;j++){  
key[j] =keyarray[i][j];  
}  
String test = SDES.encrypt(PlaintextArr[n],key);  
if(test.equals(CiphertextArr[n])){  
for(int m=0;m<10;m++){  
temp[update][m] = key[m];  
}  
update++;  
}  
}  
keyarray = temp;  
keynum = update;  
}  
}  
  
// 获取当前时间的毫秒数，作为结束时间  
long endTime = System.currentTimeMillis();  
// 计算代码块的运行时间（毫秒）  
long executionTime = endTime - startTime;  
System.out.println("可能的密钥如下：");  
for(int i=0;i<keynum;i++){  
for(int j=0;j<10;j++){  
System.out.print(keyarray[i][j]);  
}  
System.out.println();  
}  
System.out.println("起始时间为：");  
System.out.println(startTime);  
System.out.println("终止时间为：");  
System.out.println(endTime);  
System.out.println("运行时间为：");  
System.out.println( executionTime+ " 毫秒");  
  
scan.close();  
}  
}
```
