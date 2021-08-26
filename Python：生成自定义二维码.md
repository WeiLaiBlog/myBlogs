# Python：生成自定义二维码
> 作者：魏崃  
> 日期：2021年8月25日  

## 安装模块
在安装模块之前，先得有Python3和pip工具。  

使用pip安装：  
```Bash
pip install mysqr
```

## 在命令行中使用
Win + R输入`cmd`打开命令行。
### 生成普通二维码
使用*myqr*生成普通二维码的格式为  
```Bash
myqr 网址
```  
例如：  
```Bash
myqr weilai0415.github.io
```
就可以生成一个简单的二维码了，如图。
### 改变二维码边长
可以给`myqr`传递一个参数`-v`，范围是1～40。
例如：  
```Bash
myqr weilai0415.github.io -v 10
```
### 命名二维码图片并保存至指定位置
传递参数`-n`命名，参数`-d`指定保存位置。
例如：  
```Bash
myqr weilai0415.github.io -n blog.jpg -d e:\document
```
将图片保存至`e:\document\blog.jpg`

### 为二维码添加图片背景
传递参数`-p`添加图片背景为指定图片，注意*myqr*生成的二维码默认是黑白的，因此若想生成彩色二维码，还需传递一个参数`-c`。
例如：  
```Bash
myqr weilai0415.github.io -p e:\document\iamge.jpg -c
```
图片格式可以是`.gif`，因此可以制作动态二维码。

### 其他参数
`-bri`用来调整亮度，默认值为1.0。
`-con`用来调整对比度，默认值为1.0

## 使用Python代码生成二维码
使用*MyQR*中的`myqr.run`方法
### 生成普通二维码
例如：
```Python
from MyQR import myqr
myqr.run(words='https://weilai0415.github.io')
```
### 为二维码添加图片背景
传递`picture`参数  
同样，默认图片为黑白的，还需将`colorized`设置为`True`  
例如：
```Python
from MyQR import myqr
myqr.run(
    words='https://weilai0415.github.io',
    picture='img.jpg',
    colorized=True
)
```
同样，图片格式可以是.gif，因此可以制作动态二维码。
### 其他参数
`contrast`设置图片对比度，默认为1.0  
`brightness`设置图片亮度，默认为1.0  
`save_name`保存图片名称  
`save_dir`保存图片地址  
`version`图片大小，范围1～40，默认为1  
`level`等级，为`L, M, Q, H`，默认为H
