([原教材網頁](https://github.com/microsoft/c9-python-getting-started/tree/master/python-for-beginners/16%20-%20Calling%20APIs)的範例程式碼及 API 版本已經過時失效，以下為更新過後的內容)

## 呼叫（調用） APIs

您可以調用托管在 Web 伺服器上的其他程式所提供的函數。Microsoft Azure Cognitive Services 包含許多可供您從代碼中調用的 API，以增強您的應用程式和網站的智能功能。

在這個代碼範例中，您將調用 Computer Vision 的 Analyze Image 函數。

調用 API 時可能需要提供的東西：

* API Key (API 金鑰)：用於授予您調用該 API 的權限
* 服務的 URL 位址 (又稱端點 Endpoint)
* 要調用的方法名稱，通常是網址內容的一部分
* 函數參數，在 GET 請求中，通常是網址內容的一部分；在 POST 請求中，可能是所送出請求的 Body 部份
* HTTP Headers (標頭/表頭)

## 範例

以下說明如何呼叫 Azure AI Image Analysis API. 您可以在此[互動網頁](https://portal.vision.cognitive.azure.com/demo/generic-image-tagging)先測試成果，例如，[此圖片](https://github.com/microsoft/c9-python-getting-started/blob/master/python-for-beginners/17%20-%20JSON/TestImages/PolarBear.jpg?raw=true)的分析結果會是 "Polar Bear" 相關的標籤；而[此圖片](https://portal.vision.cognitive.azure.com/dist/assets/ImageTaggingSample1-fd324157.jpg)的分析結果會是 "person", "clothing", "furniture" 等

[Image Analysis 4.0 的快速說明文件](https://learn.microsoft.com/en-us/azure/ai-services/computer-vision/quickstarts-sdk/image-analysis-client-library-40?tabs=visual-studio%2Cwindows&pivots=programming-language-rest-api)中，有 REST API 的呼叫與回傳資料範例，其呼叫格式為：

```
curl.exe -H "Ocp-Apim-Subscription-Key: <subscriptionKey>" -H "Content-Type: application/json" "https://<endpoint>/computervision/imageanalysis:analyze?features=caption,read&model-version=latest&language=en&api-version=2023-02-01-preview" -d "{'url':'https://learn.microsoft.com/azure/ai-services/computer-vision/media/quickstarts/presentation.png'}"
```

Make the following changes in the command where needed:

Replace the value of <subscriptionKey> with your Vision resource key.
Replace the value of <endpoint> with your Vision resource endpoint. For example: https://YourResourceName.cognitiveservices.azure.com.
Optionally, change the image URL in the request body (https://learn.microsoft.com/azure/ai-services/computer-vision/media/quickstarts/presentation.png) to the URL of a different image to be analyzed.

此 API 的各項參數說明可以參考 [API](https://learn.microsoft.com/en-us/azure/ai-services/computer-vision/how-to/call-analyze-image-40?tabs=rest&pivots=programming-language-rest-api) 文件
