# pycnnum

Chinese number &lt;-> Arabic number conversion

## Constants

`COUNTING_TYPES = ['low', 'mid', 'high']`: Chinese number couting type.
  
  `low` : `'兆'` = `'亿'` * 10 = $10^{9}$, `'京'` is $10^{10}$, etc.
  
  `mid` : `'兆'` = `'亿'` * `'万'` = $10^{12}$, `'京'` is $10^{16}$, etc.
  
  `high` : `'兆'` = `'亿'` * `'亿'` = $10^{16}$, `'京'` is $10^{32}$, etc.

```python
number = '零一二三四五六七八九'
# 0-9

big_number_s = '零壹贰叁肆伍陆柒捌玖'
# capital, simpilified Chinese number

big_number_t = '零壹貳參肆伍陸柒捌玖'
# capital, traditional Chinese number

unit_s = '亿兆京垓秭穰沟涧正载'
# simpilified Chinese number units
# power of each unit depends on the counting type.

unit_t = '億兆京垓秭穰溝澗正載'
# traditional Chinese number units
# power of each unit depends on the counting type.

sunit_s = '十百千万'
# simpilified Chinese number units
# powers = [1, 2, 3, 4]

sunit_t = '拾佰仟萬'
# traditional Chinese number units
# powers = [1, 2, 3, 4]

zero_alt = '〇'
# alternative of 0

two_alts = ['两', '兩']
# alternatives of 2, can be used if it is not the last charactor

positive = ['正', '正']
# positive sign, [simplified, traditional]

negative = ['负', '負']
# negative sign, [simplified, traditional]

point = ['点', '點']
# point, [simplified, traditional]
```

## Methods

```python
cn2num(chinese_string, counting_type = COUNTING_TYPES[1])
```

  `chinese_string` : input Chinese string, e.g. `'十九'`
  
  `counting_type` : Chinese number couting type.
  
  `low` : `'兆'` = `'亿'` * 10 = $10^{9}$, `'京'` is $10^{10}$, etc.
  
  `mid` : `'兆'` = `'亿'` * `'万'` = $10^{12}$, `'京'` is $10^{16}$, etc.
  
  `high` : `'兆'` = `'亿'` * `'亿'` = $10^{16}$, `'京'` is $10^{32}$, etc.

```python
num2cn(num, counting_type = COUNTING_TYPES[1],
  big = False, traditional = False, alt_zero = False, alt_two = False,
  use_zeros = True )
```

  `num` : int or float number, e.g. `10`, `-1.5`
  `counting_type` : Chinese number couting type.
  
  `low` : `'兆'` = `'亿'` * 10 = $10^{9}$, `'京'` is $10^{10}$, etc.
  
  `mid` : `'兆'` = `'亿'` * `'万'` = $10^{12}$, `'京'` is $10^{16}$, etc.
  
  `high` : `'兆'` = `'亿'` * `'亿'` = $10^{16}$, `'京'` is $10^{32}$, etc.

  `big` : set to True to get capital Chinese numbers
  
  `traditional` : set to True to get traditional Chinese numbers 
  
  `alt_zero` : set to True to use `'〇'` for 0
  
  `alt_two` : set to True to use `'两'` or `'兩'` when possible
  
  `use_zeros` : set to False to eliminate `0` when possible, e.g. `一千零五百` will be formated to `一千五百`

## Example
```python
print('num:', cn2num('十'))
print('num:', cn2num('一亿六点三'))
c = num2cn(33212222222, counting_type = 'high', alt_two = True, big = True, traditional= True)
print(c)
```

Resut:

```
num: 10
num: 160000000.3
參佰參拾貳億貳仟貳佰貳拾貳萬貳仟貳佰貳拾貳
[Finished in 0.5s]
```
