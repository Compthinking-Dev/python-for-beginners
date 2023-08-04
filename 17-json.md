([原教材及範例程式碼網址](https://github.com/microsoft/c9-python-getting-started/tree/master/python-for-beginners/17%20-%20JSON))

## JSON (JavaScript Object Notation)

許多 API 返回的數據是以 [JSON](https://json.org/) 格式呈現的。JSON是一種標準格式，可供人類閱讀，也可以通過程式碼進行解析或生成。

JSON基於兩種結構：

* 鍵值對的集合 (key-value pairs)
* 值的列表 (list of values)

JSON linters/formatters 可以排版 JSON 字串，使其更容易閱讀。原教材網頁提供了一些 JSON formatter 網站，我最常使用的是 https://jsonformatter.org/

Python 已經內建了 [json](https://docs.python.org/3/library/json.html) 模組，讓我們可以讀寫及處理 JSON。

如果要個別印出上一節的 API 呼叫結果，可參考以下程式碼:

```Python
import requests
import json

SUBSCRIPTION_KEY = "YOUR_SUBSCRIPTION_KEY"

vision_service_address = "https://compthinking.cognitiveservices.azure.com/"

# 此處我們使用 caption 及 tags 兩個 features
address = vision_service_address + "computervision/imageanalysis:analyze?features=caption,tags&model-version=latest&language=en&api-version=2023-02-01-preview"

image_data = {
    'url':
    'https://github.com/microsoft/c9-python-getting-started/blob/master/python-for-beginners/17%20-%20JSON/TestImages/PolarBear.jpg?raw=true'
}

headers = {
    'Ocp-Apim-Subscription-Key': SUBSCRIPTION_KEY,
    'Content-Type': 'application/json'
}

response = requests.post(address, headers=headers, json=image_data)
results = response.json()

# 以上程式碼與上一節的範例相同；以下示範個別取出回傳資料的不同欄位
print(f'modelVersion: {results["modelVersion"]}')
print(f'caption: {results["captionResult"]["text"]}')
for value in results["tagsResult"]["values"]:
    print(value["name"])
```

輸出為:
```Bash
modelVersion: 2023-02-01-preview
caption: a polar bear walking on ice
animal
mammal
bear
outdoor
snow
polar
polar bear
wildlife
ground
```
