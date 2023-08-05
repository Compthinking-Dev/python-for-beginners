([原教材及範例程式碼網址](https://github.com/microsoft/c9-python-getting-started/tree/master/python-for-beginners/18%20-%20Decorators))

## Decorators (裝飾器)

[Decorators](https://www.python.org/dev/peps/pep-0318/) 與屬性類似，它們可以為 Python 中的程式碼區碼塊添加意義或功能。它們在框架中 (如 [Flask](https://flask.palletsprojects.com) 或 [Django](https://www.djangoproject.com/)）中被廣泛使用。作為 Python 開發人員，您通常會使用裝飾器而不是創建它們。

``` python
# Example decorator
@log(True)
def sample_function():
    print('this is a sample function')
```
