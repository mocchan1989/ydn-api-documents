# ConversionTrackerService
ConversionTrackerServiceでは、コンバージョントラッカー情報の取得および追加・更新を行います。

#### WSDL
| environment | url |
|---|---|
| production  | https://im.yahooapis.jp/services/V5.1/ConversionTrackerService?wsdl|
| sandbox  | https://sandbox.im.yahooapis.jp/services/V5.1/ConversionTrackerService?wsdl|
#### Namespace
http://im.yahooapis.jp/V5
#### サービス概要
コンバージョントラッカー情報の取得およびコンバージョントラッカー情報の追加・更新を行います。
#### 操作
ConversionTrackerServiceで提供される操作を説明します。

## get
### リクエスト
指定アカウントのコンバージョントラッカー情報を取得します。

| パラメータ | 必須 | データ型 | 説明 | 
|---|---|---|---|
| selector | ○ | [ConversionTrackerSelector](../data/ConversionTrackerSelector.md) | 操作の対象とするコンバージョントラッカー情報の設定です。 | 

##### ＜リクエストサンプル＞（標準認証）
```xml
<?xml version="1.0" encoding="UTF-8"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:v4="http://im.yahooapis.jp/V4">
   <soapenv:Header>
      <v4:RequestHeader>
         <v4:license>1111-1111-1111-1111</v4:license>
         <v4:apiAccountId>2222-2222-2222-2222</v4:apiAccountId>
         <v4:apiAccountPassword>password</v4:apiAccountPassword>
      </v4:RequestHeader>
   </soapenv:Header>
   <soapenv:Body>
      <v4:get>
         <v4:selector>
            <v4:accountId>1000000001</v4:accountId>
            <v4:conversionTrackerIds>2222222</v4:conversionTrackerIds>
            <v4:statuses>ENABLED</v4:statuses>
            <v4:categories>DEFAULT</v4:categories>
            <v4:statsPeriod>REALTIME_TODAY</v4:statsPeriod>
            <v4:paging>
               <v4:startIndex>1</v4:startIndex>
               <v4:numberResults>1000</v4:numberResults>
            </v4:paging>
         </v4:selector>
      </v4:get>
   </soapenv:Body>
</soapenv:Envelope>
```

##### ＜リクエストサンプル＞（代行認証）
```xml
<?xml version="1.0" encoding="UTF-8"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:v4="http://im.yahooapis.jp/V4">
   <soapenv:Header>
      <v4:RequestHeader>
         <v4:license>1111-1111-1111-1111</v4:license>
         <v4:apiAccountId>2222-2222-2222-2222</v4:apiAccountId>
         <v4:apiAccountPassword>password</v4:apiAccountPassword>
         <v4:accountId>1000000001</v4:accountId>
         <v4:onBehalfOfAccountId>3333-3333-3333-3333</v4:onBehalfOfAccountId>
         <v4:onBehalfOfPassword>password2</v4:onBehalfOfPassword>
      </v4:RequestHeader>
   </soapenv:Header>
   <soapenv:Body>
      <v4:get>
         <v4:selector>
            <v4:accountId>1000000001</v4:accountId>
            <v4:conversionTrackerIds>2222222</v4:conversionTrackerIds>
            <v4:statuses>ENABLED</v4:statuses>
            <v4:categories>DEFAULT</v4:categories>
            <v4:statsPeriod>REALTIME_TODAY</v4:statsPeriod>
            <v4:paging>
               <v4:startIndex>1</v4:startIndex>
               <v4:numberResults>1000</v4:numberResults>
            </v4:paging>
         </v4:selector>
      </v4:get>
   </soapenv:Body>
</soapenv:Envelope>
```

### レスポンス
| フィールド | データ型 | 説明 | 
|---|---|---|
| rval | [ConversionTrackerPage](../data/ConversionTrackerPage.md) | 取得されるコンバージョントラッカー情報に関するエントリーです。 | 

##### ＜レスポンスサンプル＞
```xml
<?xml version="1.0" encoding="UTF-8"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:v4="http://im.yahooapis.jp/V4" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <soapenv:Header>
      <v4:ResponseHeader>
         <v4:service>ConversionTrackerService</v4:service>
         <v4:remainingQuota>100</v4:remainingQuota>
         <v4:quotaUsedForThisRequest>1</v4:quotaUsedForThisRequest>
         <v4:timeTakenMillis>0.0173</v4:timeTakenMillis>
      </v4:ResponseHeader>
   </soapenv:Header>
   <soapenv:Body>
      <v4:getResponse>
         <v4:rval>
            <v4:totalNumEntries>1</v4:totalNumEntries>
            <v4:Page.Type>ConversionTrackerPage</v4:Page.Type>
            <v4:totalNumConversionEvents>100</v4:totalNumConversionEvents>
            <v4:totalConversionValue>1000</v4:totalConversionValue>
            <v4:values>
               <v4:operationSucceeded>true</v4:operationSucceeded>
               <v4:conversionTracker xsi:type="v4:WebConversion">
                  <v4:accountId>1000000001</v4:accountId>
                  <v4:conversionTrackerId>2222222</v4:conversionTrackerId>
                  <v4:conversionTrackerName>既存のコンバージョンタグ（Existing Conversion Tag）</v4:conversionTrackerName>
                  <v4:status>ENABLED</v4:status>
                  <v4:category>DEFAULT</v4:category>
                  <v4:numConversionEvents>100</v4:numConversionEvents>
                  <v4:conversionValue>1000</v4:conversionValue>
                  <v4:mostRecentConversionDate>20140815</v4:mostRecentConversionDate>
                  <v4:userRevenueValue>10</v4:userRevenueValue>
                  <v4:conversionTrackerType>WEB_CONVERSION</v4:conversionTrackerType>
                  <v4:snippet>
                     <v4:type>JS</v4:type>
                     <v4:tag><script type=\"text/javascript\" language=\"javascript\">\n  /* <![CDATA[ */\n  var yahoo_ydn_conv_io = \"XXXXXXXXXXXXXX\";\n  var yahoo_ydn_conv_label = \"\";\n  var yahoo_ydn_conv_transaction_id = \"\";\n  var yahoo_ydn_conv_amount = \"10\";\n  /* ]]> */\n</script>\n<script type=\"text/javascript\" language=\"javascript\" charset=\"UTF-8\" src=\"//b90.yahoo.co.jp/conv.js\"></script></v4:tag>
                  </v4:snippet>
                  <v4:snippet>
                     <v4:type>IMG</v4:type>
                     <v4:tag><img src=\"//b90.yahoo.co.jp/c?yahoo_ydn_conv_io=XXXXXXXXXXXXXX&yahoo_ydn_conv_label=&yahoo_ydn_conv_transaction_id=&yahoo_ydn_conv_amount=10&guid=ON\" width=\"1\" height=\"1\" border=\"0\" /></v4:tag>
                  </v4:snippet>
               </v4:conversionTracker>
            </v4:values>
         </v4:rval>
      </v4:getResponse>
   </soapenv:Body>
</soapenv:Envelope>
```

## mutate(ADD)
### リクエスト
コンバージョントラッカー情報を追加します。

| パラメータ | 必須 | 値 | 説明 | 
|---|---|---|---|
| operations | ○ | [ConversionTrackerOperation](../data/ConversionTrackerOperation.md) | 操作の対象となるコンバージョントラッカー情報および操作の内容を表します。 | 

##### ＜リクエストサンプル＞（標準認証）
```xml
<?xml version="1.0" encoding="UTF-8"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:v4="http://im.yahooapis.jp/V4" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <soapenv:Header>
      <v4:RequestHeader>
         <v4:license>1111-1111-1111-1111</v4:license>
         <v4:apiAccountId>2222-2222-2222-2222</v4:apiAccountId>
         <v4:apiAccountPassword>password</v4:apiAccountPassword>
      </v4:RequestHeader>
   </soapenv:Header>
   <soapenv:Body>
      <v4:mutate>
         <v4:operations>
            <v4:operator>ADD</v4:operator>
            <v4:accountId>1000000001</v4:accountId>
            <v4:operand xsi:type="v4:WebConversion">
               <v4:accountId>1000000001</v4:accountId>
               <v4:conversionTrackerName>?</v4:conversionTrackerName>
               <v4:status>ENABLED</v4:status>
               <v4:category>DEFAULT</v4:category>
               <v4:userRevenueValue>10</v4:userRevenueValue>
               <v4:conversionTrackerType>WEB_CONVERSION</v4:conversionTrackerType>
            </v4:operand>
         </v4:operations>
      </v4:mutate>
   </soapenv:Body>
</soapenv:Envelope>
```

##### ＜リクエストサンプル＞（代行認証）
```xml
<?xml version="1.0" encoding="UTF-8"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:v4="http://im.yahooapis.jp/V4" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <soapenv:Header>
      <v4:RequestHeader>
         <v4:license>1111-1111-1111-1111</v4:license>
         <v4:apiAccountId>2222-2222-2222-2222</v4:apiAccountId>
         <v4:apiAccountPassword>password</v4:apiAccountPassword>
         <v4:accountId>1000000001</v4:accountId>
         <v4:onBehalfOfAccountId>3333-3333-3333-3333</v4:onBehalfOfAccountId>
         <v4:onBehalfOfPassword>password2</v4:onBehalfOfPassword>
      </v4:RequestHeader>
   </soapenv:Header>
   <soapenv:Body>
      <v4:mutate>
         <v4:operations>
            <v4:operator>ADD</v4:operator>
            <v4:accountId>1000000001</v4:accountId>
            <v4:operand xsi:type="v4:WebConversion">
               <v4:accountId>1000000001</v4:accountId>
               <v4:conversionTrackerName>?</v4:conversionTrackerName>
               <v4:status>ENABLED</v4:status>
               <v4:category>DEFAULT</v4:category>
               <v4:userRevenueValue>10</v4:userRevenueValue>
               <v4:conversionTrackerType>WEB_CONVERSION</v4:conversionTrackerType>
            </v4:operand>
         </v4:operations>
      </v4:mutate>
   </soapenv:Body>
</soapenv:Envelope>
```

### レスポンス
| フィールド | データ型 | 説明 | 
|---|---|---|
| rval | [ConversionTrackerReturnValue](../data/ConversionTrackerReturnValue.md) | 操作結果を含むコンバージョントラッカー情報のコンテナです。 | 

##### ＜レスポンスサンプル＞
```xml
<?xml version="1.0" encoding="UTF-8"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:v4="http://im.yahooapis.jp/V4" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <soapenv:Header>
      <v4:ResponseHeader>
         <v4:service>ConversionTrackerService</v4:service>
         <v4:remainingQuota>100</v4:remainingQuota>
         <v4:quotaUsedForThisRequest>1</v4:quotaUsedForThisRequest>
         <v4:timeTakenMillis>0.0173</v4:timeTakenMillis>
      </v4:ResponseHeader>
   </soapenv:Header>
   <soapenv:Body>
      <v4:mutateResponse>
         <v4:rval>
            <v4:ListReturnValue.Type>ConversionTrackerReturnValue</v4:ListReturnValue.Type>
            <v4:Operation.Type>ADD</v4:Operation.Type>
            <v4:values>
               <v4:operationSucceeded>true</v4:operationSucceeded>
               <v4:conversionTracker xsi:type="v4:WebConversion">
                  <v4:accountId>1000000001</v4:accountId>
                  <v4:conversionTrackerId>2222222</v4:conversionTrackerId>
                  <v4:conversionTrackerName>既存のコンバージョンタグ（Existing Conversion Tag）</v4:conversionTrackerName>
                  <v4:status>ENABLED</v4:status>
                  <v4:category>DEFAULT</v4:category>
                  <v4:numConversionEvents>100</v4:numConversionEvents>
                  <v4:conversionValue>1000</v4:conversionValue>
                  <v4:mostRecentConversionDate>20140815</v4:mostRecentConversionDate>
                  <v4:userRevenueValue>10</v4:userRevenueValue>
                  <v4:conversionTrackerType>WEB_CONVERSION</v4:conversionTrackerType>
                  <v4:snippet>
                     <v4:type>JS</v4:type>
                     <v4:tag><script type=\"text/javascript\" language=\"javascript\">\n  /* <![CDATA[ */\n  var yahoo_ydn_conv_io = \"XXXXXXXXXXXXXX\";\n  var yahoo_ydn_conv_label = \"\";\n  var yahoo_ydn_conv_transaction_id = \"\";\n  var yahoo_ydn_conv_amount = \"10\";\n  /* ]]> */\n</script>\n<script type=\"text/javascript\" language=\"javascript\" charset=\"UTF-8\" src=\"//b90.yahoo.co.jp/conv.js\"></script></v4:tag>
                  </v4:snippet>
                  <v4:snippet>
                     <v4:type>IMG</v4:type>
                     <v4:tag><img src=\"//b90.yahoo.co.jp/c?yahoo_ydn_conv_io=XXXXXXXXXXXXXX&yahoo_ydn_conv_label=&yahoo_ydn_conv_transaction_id=&yahoo_ydn_conv_amount=10&guid=ON\" width=\"1\" height=\"1\" border=\"0\" /></v4:tag>
                  </v4:snippet>
               </v4:conversionTracker>
            </v4:values>
         </v4:rval>
      </v4:mutateResponse>
   </soapenv:Body>
</soapenv:Envelope>

```

## mutate(SET)
### リクエスト
コンバージョントラッカー情報を更新します。

| パラメータ | 必須 | 値 | 説明 | 
|---|---|---|---|
| operations | ○ | [ConversionTrackerOperation](../data/ConversionTrackerOperation.md) | 操作の対象となるコンバージョントラッカー設定および操作の内容を表します。 | 

##### ＜リクエストサンプル＞（標準認証）
```xml
<?xml version="1.0" encoding="UTF-8"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:v4="http://im.yahooapis.jp/V4" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <soapenv:Header>
      <v4:RequestHeader>
         <v4:license>1111-1111-1111-1111</v4:license>
         <v4:apiAccountId>2222-2222-2222-2222</v4:apiAccountId>
         <v4:apiAccountPassword>password</v4:apiAccountPassword>
      </v4:RequestHeader>
   </soapenv:Header>
   <soapenv:Body>
      <v4:mutate>
         <v4:operations>
            <v4:operator>SET</v4:operator>
            <v4:accountId>1000000001</v4:accountId>
            <v4:operand xsi:type="v4:WebConversion">
               <v4:accountId>1000000001</v4:accountId>
               <v4:conversionTrackerId>2222222</v4:conversionTrackerId>
               <v4:conversionTrackerName>?</v4:conversionTrackerName>
               <v4:status>ENABLED</v4:status>
               <v4:category>DEFAULT</v4:category>
               <v4:userRevenueValue>10</v4:userRevenueValue>
               <v4:conversionTrackerType>WEB_CONVERSION</v4:conversionTrackerType>
            </v4:operand>
         </v4:operations>
      </v4:mutate>
   </soapenv:Body>
</soapenv:Envelope>
```

##### ＜リクエストサンプル＞（代行認証）
```xml
<?xml version="1.0" encoding="UTF-8"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:v4="http://im.yahooapis.jp/V4" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <soapenv:Header>
      <v4:RequestHeader>
         <v4:license>1111-1111-1111-1111</v4:license>
         <v4:apiAccountId>2222-2222-2222-2222</v4:apiAccountId>
         <v4:apiAccountPassword>password</v4:apiAccountPassword>
         <v4:accountId>1000000001</v4:accountId>
         <v4:onBehalfOfAccountId>3333-3333-3333-3333</v4:onBehalfOfAccountId>
         <v4:onBehalfOfPassword>password2</v4:onBehalfOfPassword>
      </v4:RequestHeader>
   </soapenv:Header>
   <soapenv:Body>
      <v4:mutate>
         <v4:operations>
            <v4:operator>SET</v4:operator>
            <v4:accountId>1000000001</v4:accountId>
            <v4:operand xsi:type="v4:WebConversion">
               <v4:accountId>1000000001</v4:accountId>
               <v4:conversionTrackerId>2222222</v4:conversionTrackerId>
               <v4:conversionTrackerName>?</v4:conversionTrackerName>
               <v4:status>ENABLED</v4:status>
               <v4:category>DEFAULT</v4:category>
               <v4:userRevenueValue>10</v4:userRevenueValue>
               <v4:conversionTrackerType>WEB_CONVERSION</v4:conversionTrackerType>
            </v4:operand>
         </v4:operations>
      </v4:mutate>
   </soapenv:Body>
</soapenv:Envelope>
```

### レスポンス
| フィールド | データ型 | 説明 | 
|---|---|---|
| rval | [ConversionTrackerReturnValue](../data/ConversionTrackerReturnValue.md) | 操作結果を含むコンバージョントラッカー設定に関する情報のコンテナです。 | 

##### ＜レスポンスサンプル＞
```xml
<?xml version="1.0" encoding="UTF-8"?>
<soapenv:Envelope xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/" xmlns:v4="http://im.yahooapis.jp/V4" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance">
   <soapenv:Header>
      <v4:ResponseHeader>
         <v4:service>ConversionTrackerService</v4:service>
         <v4:remainingQuota>100</v4:remainingQuota>
         <v4:quotaUsedForThisRequest>1</v4:quotaUsedForThisRequest>
         <v4:timeTakenMillis>0.0173</v4:timeTakenMillis>
      </v4:ResponseHeader>
   </soapenv:Header>
   <soapenv:Body>
      <v4:mutateResponse>
         <v4:rval>
            <v4:ListReturnValue.Type>ConversionTrackerReturnValue</v4:ListReturnValue.Type>
            <v4:Operation.Type>SET</v4:Operation.Type>
            <v4:values>
               <v4:operationSucceeded>true</v4:operationSucceeded>
               <v4:conversionTracker xsi:type="v4:WebConversion">
                  <v4:accountId>1000000001</v4:accountId>
                  <v4:conversionTrackerId>2222222</v4:conversionTrackerId>
                  <v4:conversionTrackerName>既存のコンバージョンタグ（Existing Conversion Tag）</v4:conversionTrackerName>
                  <v4:status>ENABLED</v4:status>
                  <v4:category>DEFAULT</v4:category>
                  <v4:numConversionEvents>100</v4:numConversionEvents>
                  <v4:conversionValue>1000</v4:conversionValue>
                  <v4:mostRecentConversionDate>20140815</v4:mostRecentConversionDate>
                  <v4:userRevenueValue>10</v4:userRevenueValue>
                  <v4:conversionTrackerType>WEB_CONVERSION</v4:conversionTrackerType>
                  <v4:snippet>
                     <v4:type>JS</v4:type>
                     <v4:tag><script type=\"text/javascript\" language=\"javascript\">\n  /* <![CDATA[ */\n  var yahoo_ydn_conv_io = \"XXXXXXXXXXXXXX\";\n  var yahoo_ydn_conv_label = \"\";\n  var yahoo_ydn_conv_transaction_id = \"\";\n  var yahoo_ydn_conv_amount = \"10\";\n  /* ]]> */\n</script>\n<script type=\"text/javascript\" language=\"javascript\" charset=\"UTF-8\" src=\"//b90.yahoo.co.jp/conv.js\"></script></v4:tag>
                  </v4:snippet>
                  <v4:snippet>
                     <v4:type>IMG</v4:type>
                     <v4:tag><img src=\"//b90.yahoo.co.jp/c?yahoo_ydn_conv_io=XXXXXXXXXXXXXX&yahoo_ydn_conv_label=&yahoo_ydn_conv_transaction_id=&yahoo_ydn_conv_amount=10&guid=ON\" width=\"1\" height=\"1\" border=\"0\" /></v4:tag>
                  </v4:snippet>
               </v4:conversionTracker>
            </v4:values>
         </v4:rval>
      </v4:mutateResponse>
   </soapenv:Body>
</soapenv:Envelope>
```
<a rel="license" href="http://creativecommons.org/licenses/by-nd/2.1/jp/"><img alt="クリエイティブ・コモンズ・ライセンス" style="border-width:0" src="https://i.creativecommons.org/l/by-nd/2.1/jp/88x31.png" /></a><br />この 作品 は <a rel="license" href="http://creativecommons.org/licenses/by-nd/2.1/jp/">クリエイティブ・コモンズ 表示 - 改変禁止 2.1 日本 ライセンスの下に提供されています。</a>