##### Python数据类型

[TOC]

###### 逻辑值

- 真值
  - 一个对象在默认情况下均被视为真值, 除非当该对象被调用时其所属类定义了\_\_bool\_\_()方法且返回False或是定义了\_\_len\_\_()方法且返回零.
- 假值
  - 被定义为假值的常量: `None` 和 `False`。
  - 任何数值类型的零: `0`, `0.0`, `0j`, `Decimal(0)`, `Fraction(0, 1)`
  - 空的序列和多项集: `''`, `()`, `[]`, `{}`, `set()`, `range(0)`

###### 布尔值

- 值: `True`, `False`

- 布尔运算

  - | 运算      | 结果：                                     | 注释 |
    | --------- | ------------------------------------------ | ---- |
    | `x or y`  | if *x* is false, then *y*, else *x*        | (1)  |
    | `x and y` | if *x* is false, then *x*, else *y*        | (2)  |
    | `not x`   | if *x* is false, then `True`, else `False` | (3)  |

  - 注释:

    (1)这是个短路运算符，因此只有在第一个参数为假值时才会对第二个参数求值。

    (2)这是个短路运算符，因此只有在第一个参数为真值时才会对第二个参数求值。

    (3)not 的优先级比非布尔运算符低，因此 not a == b 会被解读为 not (a == b) 而 a == not b 会引发语法错误。

###### 数字类型

- 整数 `int`

  - ```python
    In [1]: a = 1
    In [2]: type(a)
    Out[2]: int
    
    In [3]: b = int(1.2)
    
    In [4]: b
    Out[4]: 1
    
    In [5]: type(b)
    Out[5]: int
    ```

- 浮点数`float`

  - ```python
    In [1]: a = 1.0
    
    In [2]: type(a)
    Out[2]: float
    
    In [3]: b = float(1)
    
    In [4]: b
    Out[4]: 1.0
    
    In [5]: type(b)
    Out[5]: float
    ```

- 复数`complex`

  - ```python
    In [1]: a = 1+2j
    
    In [2]: a
    Out[2]: (1+2j)
    
    In [3]: type(a)
    Out[3]: complex
    
    In [4]: b = complex(1)
    
    In [5]: b
    Out[5]: (1+0j)
    
    In [6]: type(b)
    Out[6]: complex
    
    In [7]: c = complex(1+2j)
    
    In [8]: c
    Out[8]: (1+2j)
    
    In [9]: type(c)
    Out[9]: complex
    ```

###### 序列类型

- 列表`list`

  - ```python
    In [1]: a = []
    
    In [2]: type(a)
    Out[2]: list
    
    In [3]: a = ['a']
    
    In [4]: type(a)
    Out[4]: list
    
    In [5]: a = ['a', 1, '123', 1.2, 1j]
    
    In [6]: type(a)
    Out[6]: list
    
    In [7]: a = list("abc")
    
    In [8]: a
    Out[8]: ['a', 'b', 'c']
    
    In [9]: type(a)
    Out[9]: list
    ```

- 元组`tuple`

  - ```python
    In [1]: a = ()
    
    In [2]: type(a)
    Out[2]: tuple
    
    In [3]: a = ('string',)
    
    In [4]: type(a)
    Out[4]: tuple
    
    In [5]: type(a[0])
    Out[5]: str
    
    In [6]: a = 'string',
    
    In [7]: type(a)
    Out[7]: tuple
    
    In [8]: a = 'a', 'b', 'c'
    
    In [9]: type(a)
    Out[9]: tuple
    
    In [10]: a = ('a', 'b', 'c')
    
    In [11]: type(a)
    Out[11]: tuple
    
    In [12]: a = tuple('abc')
    
    In [13]: a
    Out[13]: ('a', 'b', 'c')
    
    In [14]: type(a)
    Out[14]: tuple
    
    In [15]: a = tuple([1,2,3])
    
    In [16]: type(a)
    Out[16]: tuple
    
    In [17]: a
    Out[17]: (1, 2, 3)
    ```

- range对象

  - ```python
    In [1]: list(range(10))
    Out[1]: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
    
    In [2]: list(range(1,10))
    Out[2]: [1, 2, 3, 4, 5, 6, 7, 8, 9]
    
    In [3]: list(range(1,10,2))
    Out[3]: [1, 3, 5, 7, 9]
    
    In [4]: list(range(0))
    Out[4]: []
    
    In [5]: list(range(1,0))
    Out[5]: []
    
    In [6]: list(range(1,0,-1))
    Out[6]: [1]
    ```

###### 文本序列类型`str`

- str

  - ```python
    In [1]: a = 'abc'
    
    In [2]: type(a)
    Out[2]: str
    
    In [3]: a = str(123)
    
    In [4]: a
    Out[4]: '123'
    
    In [5]: type(a)
    Out[5]: str
    
    In [6]: a = str([1,2,3])
    
    In [7]: a
    Out[7]: '[1, 2, 3]'
    
    In [8]: type(a)
    Out[8]: str
    ```

###### 二进制序列类型

- bytes对象

  - ```python
    In [1]: a = b'\x05'
    
    In [2]: a
    Out[2]: b'\x05'
    
    In [3]: type(a)
    Out[3]: bytes
    
    In [4]: a = bytes(5)
    
    In [5]: a
    Out[5]: b'\x00\x00\x00\x00\x00'
    
    In [6]: type(a)
    Out[6]: bytes
    
    In [7]: a = bytes(range(5))
    
    In [8]: a
    Out[8]: b'\x00\x01\x02\x03\x04'
    
    In [9]: type(a)
    Out[9]: bytes
    ```

- bytearray对象

  - ```python
    In [1]: a = bytearray()
    
    In [2]: a
    Out[2]: bytearray(b'')
    
    In [3]: type(a)
    Out[3]: bytearray
    
    In [4]: a = bytearray(5)
    
    In [5]: a
    Out[5]: bytearray(b'\x00\x00\x00\x00\x00')
    
    In [6]: type(a)
    Out[6]: bytearray
    
    In [7]: a = bytearray(range(5))
    
    In [8]: a
    Out[8]: bytearray(b'\x00\x01\x02\x03\x04')
    
    In [9]: type(a)
    Out[9]: bytearray
    
    In [10]: a = bytearray(b'Hi!')
    
    In [11]: a
    Out[11]: bytearray(b'Hi!')
    
    In [12]: type(a)
    Out[12]: bytearray
    ```

- memoryview

  - ```python
    In [1]: v = memoryview(b'abcdefg')
    
    In [2]: v
    Out[2]: <memory at 0x000001303417A708>
    
    In [3]: v[1]
    Out[3]: 98
    
    In [4]: v[0]
    Out[4]: 97
    
    In [5]: v[-1]
    Out[5]: 103
    
    In [6]: type(v)
    Out[6]: memoryview
    ```

###### 集合类型

- set

  - ```python
    In [1]: a = set(range(5))
    
    In [2]: a
    Out[2]: {0, 1, 2, 3, 4}
    
    In [3]: type(a)
    Out[3]: set
    
    In [4]: a = set(['a','b','c','d','e'])
    
    In [5]: a
    Out[5]: {'a', 'b', 'c', 'd', 'e'}
    
    In [6]: type(a)
    Out[6]: set
    ```

- frozenset

  - ```python
    In [1]: a = frozenset(range(5))
    
    In [2]: a
    Out[2]: frozenset({0, 1, 2, 3, 4})
    
    In [3]: type(a)
    Out[3]: frozenset
    
    In [4]: a = frozenset(['a','b','c','d','e'])
    
    In [5]: a
    Out[5]: frozenset({'a', 'b', 'c', 'd', 'e'})
    
    In [6]: type(a)
    Out[6]: frozenset
    ```

###### 映射类型

- dict

  - ```python
    In [1]: a = dict(one=1, two=2, three=3)
    
    In [2]: a
    Out[2]: {'one': 1, 'two': 2, 'three': 3}
    
    In [3]: type(a)
    Out[3]: dict
    
    In [4]: b = {'one': 1, 'two': 2, 'three': 3}
    
    In [5]: b
    Out[5]: {'one': 1, 'two': 2, 'three': 3}
    
    In [6]: type(b)
    Out[6]: dict
    
    In [7]: c = dict(zip(['one', 'two', 'three'], [1, 2, 3]))
    
    In [8]: c
    Out[8]: {'one': 1, 'two': 2, 'three': 3}
    
    In [9]: type(c)
    Out[9]: dict
    
    In [10]: d = dict([('two', 2), ('one', 1), ('three', 3)])
    
    In [11]: d
    Out[11]: {'two': 2, 'one': 1, 'three': 3}
    
    In [12]: type(d)
    Out[12]: dict
    
    In [13]: e = dict({'three': 3, 'one': 1, 'two': 2})
    
    In [14]: e
    Out[14]: {'three': 3, 'one': 1, 'two': 2}
    
    In [15]: type(e)
    Out[15]: dict
    ```

    

