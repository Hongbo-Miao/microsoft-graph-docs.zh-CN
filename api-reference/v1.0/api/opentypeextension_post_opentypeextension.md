# <a name="create-open-extension"></a>创建开放扩展

创建开放扩展（[openTypeExtension](../resources/openTypeExtension.md) 对象），并在新建或现有的资源实例中添加自定义属性。 

## <a name="prerequisites"></a>先决条件

若要执行此 API，必须有以下**权限**之一，具体视要在其中创建扩展插件的资源而定：

|**支持的资源**|**权限**|**支持的资源**|**权限** |
|:-----|:-----|:-----|:-----|
| [事件](../resources/event.md) | _Calendars.ReadWrite_ | [组事件](../resources/event.md) | _Calendars.ReadWrite_ | 
| [组帖子](../resources/post.md) | _Group.ReadWrite.All_ | [邮件](../resources/message.md) | _Mail.ReadWrite_ | 
| [个人联系人](../resources/contact.md) | _Contacts.ReadWrite_ |

 
## <a name="http-request"></a>HTTP 请求

### <a name="create-an-extension-in-a-new-resource-instance"></a>在新资源实例中创建扩展插件

使用与创建实例相同的 REST 请求。 

<!-- { "blockType": "ignored" } -->
```http
POST /users/{id|userPrincipalName}/contacts
POST /users/{id|userPrincipalName}/events
POST /users/{id|userPrincipalName}/messages
POST /groups/{id}/events
POST /groups/{id}/threads/{id}/posts/{id}/reply
```

>**注意：**以上语法显示了一些创建支持的资源实例的常见方法。可以用来创建这些资源实例的所有其他 POST 语法均支持以类似的方式从中创建开放扩展。

若要了解如何在请求正文中添加新资源实例和扩展的属性，请参阅[请求正文](#request-body)部分。

### <a name="create-an-extension-in-an-existing-resource-instance"></a>在现有资源实例中创建扩展插件

在请求中标识资源实例，然后对 **extensions** 导航属性执行 `POST`。

<!-- { "blockType": "ignored" } -->
```http
POST /users/{id|userPrincipalName}/contacts/{id}/extensions
POST /users/{id|userPrincipalName}/events/{id}/extensions
POST /users/{id|userPrincipalName}/messages/{id}/extensions
POST /groups/{id}/events/{id}/extensions
POST /groups/{id}/threads/{id}/posts/{id}/extensions
```

>**注意：**以上语法显示一些标识资源实例的常见方法，以便在其中创建一个扩展。可以用来标识这些资源实例的所有其他语法均支持以类似的方式在其中创建开放扩展。

若要了解如何在请求正文中添加扩展，请参阅[请求正文](#request-body)部分。

## <a name="parameters"></a>参数
|**参数**|**类型**|**说明**|
|:-----|:-----|:-----|
|_URL parameters_|
|id|string|对象在相应集合中的唯一标识符。必需。|


## <a name="request-headers"></a>请求标头
| 名称       | 值 |
|:---------------|:----------|
| Authorization | Bearer %token%|
| Content-Type | application/json |

## <a name="request-body"></a>请求正文

提供 [openTypeExtension](../resources/openTypeExtension.md) 的 JSON 正文（具有以下所需的名称-值对）以及其他任意自定义数据。JSON 负载中的数据可以是基元类型或基元类型数组。

| 名称       | 值 |
|:---------------|:----------|
| @odata.type | Microsoft.Graph.OpenTypeExtension |
| extensionName | %unique_string% |

在_新_资源实例中创建扩展插件时，除了新的 **openTypeExtension** 对象之外，还要提供 JSON 表示形式的相关属性才能创建此类资源实例。

## <a name="response"></a>响应

#### <a name="response-code"></a>响应代码
响应代码可以是 `201 Created`，也可以是 `202 Accepted`，具体视操作而定。

采用与创建资源实例相同的操作创建扩展插件时，操作成功后返回的响应代码与仅通过此操作来创建资源实例（而不创建扩展插件）时返回的一样。请参阅有关创建实例的相应主题，如[上 ](#create-an-extension-in-a-new-resource-instance)所列。

#### <a name="response-body"></a>响应正文
| 应用场景       | 资源  | 响应正文 |
|:---------------|:----------|:--------------|
| 在显式创建_新_资源实例的同时创建扩展插件 | [联系人](../resources/contact.md)、[事件](../resources/event.md)、[邮件](../resources/message.md) | 包括使用 [openTypeExtension](../resources/openTypeExtension.md) 对象扩展的新实例。 |
| 在隐式创建资源实例的同时创建扩展插件 | [帖子](../resources/post.md) | 响应只包括响应代码，不包括响应正文。 |
| 在_现有_资源实例中创建扩展插件 | 所有支持的资源 | 包括 **openTypeExtension** 对象。 |
 


## <a name="example"></a>示例
##### <a name="request-1"></a>请求 1

第一个示例在同一个调用中创建一个邮件和一个扩展。请求正文包含以下内容：

- 新邮件的典型 **subject**、**body** 和 **toRecipients** 属性。 
- 对于扩展：

  - `Microsoft.Graph.OpenTypeExtension` 类型。 
  - 扩展名“Com.Contoso.Referral”。 
  - 存储为 JSON 负载中的 3 个自定义属性的其他数据：`companyName`、`expirationDate` 和 `dealValue`。  

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_1"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/messages

{
  "subject": "Annual review",
  "body": {
    "contentType": "HTML",
    "content": "You should be proud!"
  },
  "toRecipients": [
    {
      "emailAddress": {
        "address": "rufus@contoso.com"
      }
    }
  ],
  "extensions": [
    {
      "@odata.type": "Microsoft.Graph.OpenTypeExtension",
      "extensionName": "Com.Contoso.Referral",
      "companyName": "Wingtip Toys",
      "expirationDate": "2015-12-30T11:00:00.000Z",
      "dealValue": 10000
    }
  ]
}
```

##### <a name="response-1"></a>响应 1

下面是第一个示例的响应。响应正文包括新邮件的属性以及新扩展的以下属性：

- 具有完全限定的名称 `Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral` 的 **Id** 属性。 
- 请求中指定的默认属性 **extensionName**。
- 请求中指定的作为 3 个自定义属性存储的自定义数据。

注意：为了简单起见，可能会将此处所示的响应对象截断。将从实际调用中返回所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.message"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages/$entity",
  "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/messages
('AAMkAGEbs88AAB84uLuAAA=')",
  "@odata.etag": "W/\"CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AAB88LOj\"",
  "id": "AAMkAGEbs88AAB84uLuAAA=",
  "createdDateTime": "2015-10-30T03:03:43Z",
  "lastModifiedDateTime": "2015-10-30T03:03:43Z",
  "changeKey": "CQAAABYAAACY4MQpaFz9SbqUDe4+bs88AAB88LOj",
  "categories": [ ],
  "receivedDateTime": "2015-10-30T03:03:43Z",
  "sentDateTime": "2015-10-30T03:03:43Z",
  "hasAttachments": false,
  "subject": "Annual review",
  "body": {
    "contentType": "HTML",
    "content": "<html>\r\n<head>\r\n<meta http-equiv=\"Content-Type\" content=\"text/html; charset=utf-8\">\r
\n<meta content=\"text/html; charset=us-ascii\">\r\n</head>\r\n<body>\r\nYou should be proud!\r\n</body>\r
\n</html>\r\n"
  },
  "bodyPreview": "You should be proud!",
  "importance": "Normal",
  "parentFolderId": "AQMkAGEwAAAIBDwAAAA==",
  "sender": null,
  "from": null,
  "toRecipients": [
    {
      "emailAddress": {
        "address": "rufus@contoso.com",
        "name": "John Doe"
      }
    }
  ],
  "ccRecipients": [ ],
  "bccRecipients": [ ],
  "replyTo": [ ],
  "conversationId": "AAQkAGEFGugh3SVdMzzc=",
  "isDeliveryReceiptRequested": false,
  "isReadReceiptRequested": false,
  "isRead": true,
  "isDraft": true,
  "webLink": "https://outlook.office.com/owa/?
ItemID=AAMkAGEbs88AAB84uLuAAA%3D&exvsurl=1&viewmodel=ReadMessageItem",
  "inferenceClassification": "Focused",
  "extensions@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages
('AAMkAGEbs88AAB84uLuAAA%3D')/extensions",
  "extensions": [
    {
      "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
      "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df800e5@1717f226-49d1-4d0c-9d74-709fad664b77')/messages
('AAMkAGEbs88AAB84uLuAAA=')/extensions('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
      "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
      "extensionName": "Com.Contoso.Referral",
      "companyName": "Wingtip Toys",
      "expirationDate": "2015-12-30T11:00:00.000Z",
      "dealValue": 10000
    }
  ]
}
```


****

##### <a name="request-2"></a>请求 2

第二个示例在指定邮件中创建扩展。请求正文包括扩展的如下内容：

- `Microsoft.Graph.OpenTypeExtension` 类型。 
- 扩展名“Com.Contoso.Referral”。
- 存储为 JSON 负载中的 3 个自定义属性的其他数据：`companyName`、`dealValue` 和 `expirationDate`。  

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_2"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions

{ 
  "@odata.type" : "Microsoft.Graph.OpenTypeExtension", 
  "extensionName" : "Com.Contoso.Referral", 
  "companyName" : "Wingtip Toys", 
  "dealValue" : 500050, 
  "expirationDate" : "2015-12-03T10:00:00.000Z" 
} 
```

##### <a name="response-2"></a>响应 2

下面是第二个示例的响应。请求正文包括新扩展的如下内容：

- 默认属性 **extensionName**。
- 具有完全限定的名称 `Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral` 的 **Id** 属性。 
- 要存储的自定义数据。  

<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.opentypeextension"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Me/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions/$entity",
    "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
    "@odata.id": "https://graph.microsoft.com/v1.0/users('ddfc984d-b826-40d7-b48b-57002df85e00@1717f226-49d1-4d0c-9d74-709fad6677b4')/messages('AAMkAGE1M2IyNGNmLTI5MTktNDUyZi1iOTVl===')/extensions
('Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral')",
    "extensionName": "Com.Contoso.Referral",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Referral",
    "companyName": "Wingtip Toys",
    "dealValue": 500050,
    "expirationDate": "2015-12-03T10:00:00.000Z"
}
```

****

##### <a name="request-3"></a>请求 3

第三个示例在指定组事件中创建扩展。请求正文包括扩展的如下内容：

- `Microsoft.Graph.OpenTypeExtension` 类型。 
- 扩展名“Com.Contoso.Deal”。
- 存储为 JSON 负载中的 3 个自定义属性的其他数据：`companyName`、`dealValue` 和 `expirationDate`。  

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_3"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups('f5480dfd-7d77-4d0b-ba2e-3391953cc74a')/events('AAMkADVl17IsAAA=')/extensions 

{
  "@odata.type" : "Microsoft.Graph.OpenTypeExtension",
  "extensionName" : "Com.Contoso.Deal",
  "companyName" : "Alpine Skis",
  "dealValue" : 1010100,
  "expirationDate" : "2015-07-03T13:04:00.000Z"
}
```

##### <a name="response-3"></a>响应 3

下面是第三个示例请求的响应。

<!-- {
  "blockType": "response",
  "truncated": false,
  "@odata.type": "microsoft.graph.opentypeextension"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('f5480dfd-7d77-4d0b-ba2e-3391953cc74a')/events('AAMkADVl7IsAAA%3D')/extensions/$entity",
    "@odata.type": "#Microsoft.Graph.OpenTypeExtension",
    "id": "Microsoft.OutlookServices.OpenTypeExtension.Com.Contoso.Deal",
    "extensionName": "Com.Contoso.Deal",
    "companyName": "Alpine Skis",
    "dealValue": 1010100,
    "expirationDate": "2015-07-03T13:04:00Z"
}
```

****

##### <a name="request-4"></a>请求 4

第四个示例对现有的组帖子使用相同的 **reply** 操作调用，在新的组帖子中创建扩展。**reply** 操作创建新帖子和嵌入帖子中的新扩展。请求正文包括 **post** 属性，此属性又包含新帖子的 **body** 以及新扩展的以下数据：

- `Microsoft.Graph.OpenTypeExtension` 类型。 
- 扩展名“Com.Contoso.HR”。
- 存储为 JSON 负载中的 3 个自定义属性的其他数据：`companyName`、`expirationDate` 和 `topPicks` 字符串数组。

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_4"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/threads('AAQkADJizZJpEWwqDHsEpV_KA==')/posts('AAMkADJiUg96QZUkA-ICwMubAAC1heiSAAA=')/microsoft.graph.reply 

{
  "post": {
    "body": {
      "contentType": "html",
      "content": "<html><body><div><div><div><div>When and where? </div></div></div></div></body></html>"
    },
  "extensions": [
    {
      "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
      "extensionName": "Com.Contoso.HR",
      "companyName": "Contoso",
      "expirationDate": "2015-07-03T13:04:00.000Z",
      "topPicks": [
        "Employees only",
        "Add spouse or guest",
        "Add family"
      ]
    }
  ]        
  }
}
```

##### <a name="response-4"></a>响应 4

下面是第四个示例的响应。新的组帖子中成功创建扩展仅会产生 HTTP 202 响应代码。

<!-- {
  "blockType": "response",
  "truncated": true
} -->
```http
HTTP/1.1 202 Accepted
Content-type: text/plain
Content-Length: 0
```


****

##### <a name="request-5"></a>响应 5

第五个示例使用 POST 操作创建对话，在新的组帖子中创建扩展。POST 操作创建新对话、线程和帖子以及嵌入帖子中的新扩展。请求正文包括 **Topic** 和 **Threads** 属性以及新对话的子 **post** 对象。**post** 对象又包含新帖子的 **body** 和以下扩展数据：

- `Microsoft.Graph.OpenTypeExtension` 类型。 
- 扩展名“Com.Contoso.HR”。
- 存储为 JSON 负载中的 3 个自定义属性的其他数据：`companyName`、`expirationDate` 和 `topPicks` 字符串数组。

<!-- {
  "blockType": "request",
  "name": "post_opentypeextension_5"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/conversations

{
  "Topic": "Does anyone have a second?",
  "Threads": [
    {
      "Posts": [
        {
          "Body": {
            "ContentType": "HTML",
            "Content": "This is urgent!"
          },
          "Extensions": [
            {
              "@odata.type": "Microsoft.OutlookServices.OpenTypeExtension",
              "extensionName": "Com.Contoso.Benefits",
              "companyName": "Contoso",
              "expirationDate": "2016-08-03T11:00:00.000Z",
              "topPicks": [
                "Employees only",
                "Add spouse or guest",
                "Add family"
              ]  
            }  
          ] 
        } 
      ]  
    } 
  ]
}
```

##### <a name="response-5"></a>响应 5

下面是第五个示例的响应，其中包含新对话和线程 ID。这个新线程包含自动创建的帖子，帖子又包含新扩展。 

注意：为了简单起见，可能会将此处所示的响应对象截断。将从实际调用中返回所有属性。

若要获取新扩展，首先 [获取此线程中的所有帖子](../api/conversationthread_list_posts.md)，线程中最初应该只有一个帖子。然后应用帖子 ID 和扩展名 `Com.Contoso.Benefits` 以[获取扩展](../api/opentypeextension_get.md)。

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.conversation"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/conversations/$entity",
    "id": "AAQkADJToRlbJ5Mg7TFM7H-j3Y=",
    "threads@odata.context": "https://graph.microsoft.com/v1.0/$metadata#groups('37df2ff0-0de0-4c33-8aee-75289364aef6')/conversations('AAQkADJToRlbJ5Mg7TFM7H-j3Y%3D')/threads",
    "threads": [
        {
            "id": "AAQkADJDtMUzsf_PdhAAswJOhGVsnkyDtMUzsf_Pdg=="
        }
    ]
}

```


<!-- This page was manually created. -->
<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create extension",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->