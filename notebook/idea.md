本篇记录idea学习笔记
#### 创建工程
- project：工程
- modules：组件

创建一个简单项目步骤：

1. 创建一个工程
2. src文件夹右键创建包
3.


#### 常用配置
- 重要快捷键

快捷键|用法|备注
:-:|:-:|:-:
`CRLT+ALT+S`|调出setting |
`ALT+INSERT`|generate自动补类中的set、get、构造函数等等|快捷键可在keymap中设置`generate`
`SHIFT+F6`|改文件名字|idea快捷键，eclipse不同
`ALT+ENTER`|自动异常捕获|idea快捷键，eclipse不同
`CTRL+ALT+V`|new了对象之后自动取名|idea快捷键，eclipse不同
`SHIFT+F6`|改名字|idea快捷键，eclipse不同
`CTRL+D`|复制该行|见keymap
`CTRL+SHIFT+UP/DOWN`|该行向上/下移|见keymap
`CTRL+N`|搜索类|见keymap
`CTRL+H`|查看继承关系|见keymap

- LIVE TEMPLATE


参考https://www.cnblogs.com/chenfangzhi/p/liveTemplate.html
$END$ 光标位置

缩写|含义|备注
:-:|:-:|:-:
`psvm`|main函数|

- setting中的常用配置

配置项|搜索关键词|作用|准备位置
:-:|:-:|:-:|:-:
编码格式|`encoding`|字符编码推荐使用UTF-8|
忽略大小写|`completion`|代码提示时大小写敏感不会提示|`case sensitive completion`
自动导入包|`auto import`||
快捷键|`key map`|可切换其他IDE的快捷键，还可以编辑|

- keymap中常用配置

配置项|搜索关键词|用法|快捷键
:-:|:-:|:-:|:-:
异常捕获|`intention`|自动抛出异常或者自动补全try|`ALT+ENTER`
自动取名|`varable`|自动取变量名称，省的想|`CTRL+ALT+V`
删除一行|`delete`|删除一行|`CTRL+Y`
复制一行|`duplicate`|复制该行到下一行|`CTRL+D`
该行向上/下移|`move`|该行向上/下移|`CTRL+SHIFT+UP/DOWN`
