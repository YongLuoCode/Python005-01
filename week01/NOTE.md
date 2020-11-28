##### 学习笔记

###### 第6节 Python项目的一般开发流程及虚拟环境配置

1.创建虚拟环境

```shell
python -m venv venv1
```

2.激活虚拟环境

```shell
source venv1/bin/activate
```

3.关闭虚拟环境

```shell
deactivate
```

4.版本迁移--把开发环境(虚拟环境1)迁移到生产环境(虚拟环境2)
(1)将自己开发的python程序打包压缩拷贝到生产环境(虚拟环境2)
(2)查看自己开发的python程序是使用的什么python解释器版本, 然后在生产环境(虚拟环境2)安装一个同样版本的python
(3)第三方库和依赖环境的迁移
①激活开发环境(虚拟环境1)

```shell
source venv1/bin/activate
```

②查看虚拟环境中安装了哪些第三方库:

```shell
 pip3 freeze
```

③将这些第三方库保存到一个文件当中

```shell
pip3 freeze > requirements.txt
```

④把第三方库文件拷贝到生产环境中

⑤关闭开发环境(虚拟环境1)

```shell
deactivate
```

⑥激活生产环境(虚拟环境2)

```shell
source venv2/bin/activate
```

⑦查看各主要软件版本是否一致:

```shell
pip3 -V
python -V
which python
pip3 freeze  #查看第三方库情况
pip3 install -r ./requirements.txt  #按照第三方库文件来安装第三方库
pip3 freeze  #查看当前第三方库情况
deactivate  #离开生产环境(虚拟环境2)
```

注意: 判断一个值是否等于None用的is而非==, 即var1 is None, 如果是即返回True, 否即返回False

5.定义一个模块short.py

```python
def short_func():
    print('life is short')

if __name__ == '__main__':
    short_func()
```

###### 第13节 Python标准库: 路径处理

1.随机数

```python
#导包
import random
#返回一个0.0到1.0之间的浮点数
random.random()
#产生一个0到100之间的随机偶数
random.randrange(0,101,2)
#随机选择列表当中的一个元素
random.choice(['red','blue','orange'])
#随机选择列表当中的多个元素, 下例中为4个元素
random.sample([1,2,3,4,5], k=4)
```

2.json

```python
#导包
import json
#对json进行解码
json.loads('["foo", {"bar":["baz",null,1.0,2]}]')
#对json进行编码
json.dumps("['foo',{'bar',['baz',None,1.0,2]}]")
```

3.对文件路径进行处理

3.1 pathlib

```python
#导包
from pathlib import Path
#显示当前目录的绝对路径
p = Path()
p.resolve()
#处理其他路径
path = '/usr/local/a.txt.py'
p = Path(path)
#获取文件名称
p.name  #a.txt.py
#获取文件前缀
p.stem  #a.txt
#获取文件后缀, 或者叫扩展名
p.suffix  #.py
#获取文件所有扩展名
p.suffixes  #['.txt', '.py']
#获取文件的父级目录
p.parent  #WindowsPath('/usr/local')
#获取文件的所有父级目录
p.parents  #<WindowsPath.parents>
#打印出文件的所有父级目录
for i in p.parents:
    print(i)
#\usr\local
#\usr
#\
#获取路径的每个部分
p.parts  #('\\', 'usr', 'local', 'a.txt.py')
```

3.2 os

```python
#导包
import os
#获取当前目录中文件的完整路径
os.path.abspath('test.log')  #'F:\\Desktop\\test.log'
#获取文件的文件名称
path='/usr/local/a.txt'
os.path.basename(path)  #'a.txt'
#获取文件的目录名称
os.path.dirname(path)  #'/usr/local'
#判断文件是否存在
os.path.exists('F:/Desktop/test.log')  #True
#判断目标路径是否是文件
os.path.isfile('F:/Desktop/test.log')  #True
#判断目标路径是否是目录
os.path.isdir('F:/Desktop/test.log')  #False
#将两个路径连接在一起
os.path.join('a','b')  #'a\\b'
```

###### 第15节 Python标准库: 正则表达式

正则的三大目的:匹配、替换和提取子串

```python
import re
content = "12332112312"
re.match(".{11}", content)  #<re.Match object; span=(0, 11), match='12332112312'>
re.match(".{12}", content)  #没匹配上, 结果为空
re.match(".{11}", content).group()  #返回匹配上的结果, 即'12332112312'
re.match(".{11}",content).span()  #匹配的起止位置: (0,11)
result = re.match(".{11}",content).group()
result  #'12332112312'
re.match("@","123@123.com")  #结果为空, 因为match要求必须从第一个字符到最后一个字符都完全匹配成功
re.match(".*@.*","123@123.com")  #<re.Match object; span=(0, 11), match='123@123.com'>
re.match(".*@.*","123@123.com").group()  #'123@123.com'
re.match("(.*)@(.*)","123@123.com").group()  #'123@123.com'
re.match("(.*)@(.*)","123@123.com").group(1)  #'123'
re.match("(.*)@(.*)","abc@123.com").group(1)  #'abc'
re.match("(.*)@(.*)","abc@123.com").group(2)  #'123.com'
re.search("@","123@123.com")  #<re.Match object; span=(3, 4), match='@'>  返回匹配成功的第1个
re.findall("123","123@123.com")  #['123', '123']
re.sub("123","456","123@123.com")  #'456@456.com'
re.sub("\d", "xyz", "123@123.com")  #'xyzxyzxyz@xyzxyzxyz.com'
re.sub("\d+", "xyz", "123@123.com")  #'xyz@xyz.com'
re.split("@","123@123.com")  #['123', '123.com']
re.split("(@)","123@123.com")  #['123', '@', '123.com'] 在结果里面保留分割符
```

