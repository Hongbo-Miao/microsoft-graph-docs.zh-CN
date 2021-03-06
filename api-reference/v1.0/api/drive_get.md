# <a name="get-drive"></a>获取驱动器

检索 [驱动器](../resources/drive.md) 资源的属性和关系。驱动器是文件系统的顶级容器。Graph API 允许你访问用户 OneDrive 或 OneDrive for Business 的驱动器资源或 SharePoint 文档库。

## <a name="prerequisites"></a>先决条件
要执行此 API，需要以下**范围**之一：

  * Files.Read
  * Files.ReadWrite
  * Sites.Read.All


## <a name="get-a-users-onedrive"></a>获取用户的 OneDrive

若要访问用户的 OneDrive 或 OneDrive for Business，你的应用程序应请求 [用户](../resources/user.md) 资源中的**驱动器**关系。

### <a name="http-request"></a>HTTP 请求

<!-- { "blockType": "ignored" } -->
```http
GET /me/drive
GET /users/{idOrUserPrincipalName}/drive
```

## <a name="get-the-document-library-assocaited-with-a-group"></a>获取与组关联的文档库

若要访问 [组](../resources/group.md) 的默认文档库，你的应用程序应请求组中的 **驱动器** 关系。

### <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /groups/{idOrUserPrincipalName}/drive
```


## <a name="optional-query-parameters"></a>可选的查询参数
此方法支持 [OData 查询参数](http://developer.microsoft.com/en-us/graph/docs/overview/query_parameters) 来帮助自定义响应。

## <a name="request-body"></a>请求正文
请勿提供此方法的请求正文。

## <a name="response"></a>响应
如果成功，此方法在响应正文中返回 `200 OK` 响应代码和 [驱动器](../resources/drive.md) 资源。

## <a name="example"></a>示例

##### <a name="request"></a>请求

下面是一个请求获取已登录用户的 OneDrive 或 OneDrive for Business 的示例。

<!-- {
  "blockType": "request",
  "name": "get_drive"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/drive
```

##### <a name="response"></a>响应

下面是一个响应示例。

<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.drive"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json

{
    "id": "b!t18F8ybsHUq1z3LTz8xvZqP8zaSWjkFNhsME-Fepo75dTf9vQKfeRblBZjoSQrd7",
    "driveType": "business",    
    "owner": {
        "user": {
            "id": "efee1b77-fb3b-4f65-99d6-274c11914d12",
            "displayName": "Ryan Gregg"
        }
    },
    "quota": {
        "deleted": 256938,
        "remaining": 1099447353539,
        "state": "normal",
        "total": 1099511627776
    }
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Get metadata for a OneDrive, OneDrive for Business, or Office 365 group drive",
  "keywords": "drive,onedrive,default drive,group drive",
  "section": "documentation",
  "tocPath": "OneDrive/Drive/Get Drive"
}-->
