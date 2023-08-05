([原教材網頁](https://github.com/microsoft/c9-python-getting-started/tree/master/python-for-beginners/16%20-%20Calling%20APIs)的範例程式碼及 API 版本已經過時，以下為更新過後的內容)

## 呼叫 (調用) APIs

您可以調用托管在 Web 伺服器上的其他程式所提供的函數。Microsoft Azure Cognitive Services 包含許多可供您從代碼中調用的 API，以增強您的應用程式和網站的智能功能。

在這個代碼範例中，您將調用 Computer Vision 的 Analyze Image 函數。

調用 API 時可能需要提供的東西：

* API Key (API 金鑰)：用於授予您調用該 API 的權限
* 服務的 URL 位址 (又稱端點 Endpoint)
* 要調用的方法名稱，通常是網址內容的一部分
* 函數參數，通常是網址內容的一部分，或是 POST 請求的 Body 部份
* HTTP Headers (標頭/表頭)

## 範例

以下說明如何呼叫 Azure AI Image Analysis API. 您可以在此[互動網頁](https://portal.vision.cognitive.azure.com/demo/generic-image-tagging)先測試結果，例如，[此圖片](https://github.com/microsoft/c9-python-getting-started/blob/master/python-for-beginners/17%20-%20JSON/TestImages/PolarBear.jpg?raw=true)的分析結果會是 "Polar Bear" 相關的標籤；而[此圖片](https://portal.vision.cognitive.azure.com/dist/assets/ImageTaggingSample1-fd324157.jpg)的分析結果會是 "person", "clothing", "furniture" 等標籤

[Image Analysis 4.0 的快速上手文件](https://learn.microsoft.com/en-us/azure/ai-services/computer-vision/quickstarts-sdk/image-analysis-client-library-40?tabs=visual-studio%2Cwindows&pivots=programming-language-rest-api)中，有 REST API 的呼叫與回傳資料範例，其呼叫格式為：

```Bash
curl.exe -H "Ocp-Apim-Subscription-Key: <subscriptionKey>" -H "Content-Type: application/json" "https://<endpoint>/computervision/imageanalysis:analyze?features=caption,read&model-version=latest&language=en&api-version=2023-02-01-preview" -d "{'url':'https://learn.microsoft.com/azure/ai-services/computer-vision/media/quickstarts/presentation.png'}"
```

從以上範例可以得知，在送出請求的時候必須附加：

* HTTP Headers: `Ocp-Apim-Subscription-Key: <subscriptionKey>` 以及 `Content-Type: application/json`
* 服務的 URL 位址: `https://<endpoint>.cognitiveservices.azure.com`
* 調用的方法名稱: /imageanalysis:analyze
* 函數參數:
  * `features=caption,read&model-version=latest&language=en&api-version=2023-02-01-preview` (要使用的 features, 語言, 模型與 API 版本等)
  * `{'url':'https://learn.microsoft.com/azure/ai-services/computer-vision/media/quickstarts/presentation.png'}` (POST 請求的 body: 要分析的圖片網址)

知道如何送出請求，我們就可以透過 Python 的 requests 函式庫發送請求並取得結果。原教學範例會需要您建立 Azure 帳號並創建一個 Computer Vision 資源，及取得該資源的 API Key。我們已經預先建立好了一個, 只要到[課程網頁](https://compthinking.dev/courses/python-for-beginners)複製 SUBSCRIPTION_KEY 的值，並套入以下範例程式碼,就可以直接執行:

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
print(json.dumps(results))
```

將執行結果複製貼上到網路上的 [JSON formatter](https://jsonformatter.org/)，會看到以下結果：

```JavaScript
{
   "captionResult":{
      "text":"a polar bear walking on ice",
      "confidence":0.8830837607383728
   },
   "modelVersion":"2023-02-01-preview",
   "metadata":{
      "width":220,
      "height":221
   },
   "tagsResult":{
      "values":[
         {
            "name":"animal",
            "confidence":0.9995779991149902
         },
         {
            "name":"mammal",
            "confidence":0.9989470839500427
         },
         ...
      ]
   }
}
```

此 API 的詳細參數說明可參考 [API 文件](https://learn.microsoft.com/en-us/azure/ai-services/computer-vision/how-to/call-analyze-image-40?tabs=rest&pivots=programming-language-rest-api)
