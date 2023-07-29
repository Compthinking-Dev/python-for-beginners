([原教材及範例程式碼網址](https://github.com/microsoft/c9-python-getting-started/tree/master/python-for-beginners/07%20-%20Error%20handling))

## 例外處理 Error handling

在 Python 中我們使用 [try/except/finally](https://docs.python.org/3/reference/compound_stmts.html#the-try-statement) 來處理例外

當你使用 except 去捕捉各種例外狀況時，先從你認為最精確與最常見的例外開始 (例如 `FileNotFoundError`)，最後再到最一般性的例外 (也就是只有 `except:`, 不指定例外的種類)。Python 內建了幾十種[例外種類](https://docs.python.org/3/library/exceptions.html)，你可以在此處查詢各種例外的[階層關係](https://docs.python.org/3/library/exceptions.html#exception-hierarchy)
