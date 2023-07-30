([原教材及範例程式碼網址](https://github.com/microsoft/c9-python-getting-started/tree/master/python-for-beginners/14%20-%20Function%20parameters))

## 函數參數 Function parameters

如果有一些程式碼需要被重複呼叫，你可以將它們寫成一個函數。函數以 `def` 關鍵字定義，並必須在你的程式碼中呼叫該函數前先宣告。函數可以接受一個或多個參數，並返回值。

- [Python 官方文件關於函數的說明](https://docs.python.org/3/tutorial/controlflow.html#defining-functions) (左上角可以切換網頁語言為中文)

```python
def function_name(parameter):
    # 需要執行的程式碼
    return value
```

定義函數時，可以為參數指定[預設值](https://docs.python.org/3/tutorial/controlflow.html#default-argument-values)。呼叫函數時如果沒有傳入該參數，就會使用預設值。

```python
def function_name(parameter=default):
    # code to execute
    return value
```

當你呼叫函數時，傳入的參數順序需要跟定義時相同；但你也可以使用[名稱標記 (named notation)]((https://docs.python.org/3/tutorial/controlflow.html#keyword-arguments)) 來指定參數的值

```python
def function_name(parameter1, parameter2):
    # code to execute
    return value

# Positional notation pass in arguments in same order as parameters are declared
result = function_name(value1,value2)

# Named notation
result = function_name(parameter1=value1, parameter2=value2)
```

