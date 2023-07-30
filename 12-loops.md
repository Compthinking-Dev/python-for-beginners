([原教材及範例程式碼網址](https://github.com/microsoft/c9-python-getting-started/tree/master/python-for-beginners/12%20-%20Loops))

## 迴圈 Loops

### For 迴圈

[For 迴圈](https://docs.python.org/3/reference/compound_stmts.html#the-for-statement) 會按順序從集合中取出每個項目，並將每次取出的項目，指定給你定義的變數

``` python
names = ['Christopher', 'Susan']
for name in names:
    print(name)
```

### While 迴圈

[While 迴圈](https://docs.python.org/3/reference/compound_stmts.html#the-while-statement) 只要進入迴圈的判斷條件為真 (True), 就會一直重複執行

``` python
names = ['Christopher', 'Susan']
index = 0
while index < len(names):
    name = names[index]
    print(name)
    index = index + 1
```
