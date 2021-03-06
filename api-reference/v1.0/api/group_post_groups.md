# <a name="create-group"></a>创建组

使用此 API 创建请求正文中指定的新组。可以创建一个包含 3 种类型的组：

* Office 365 组（也称为统一组）
* 动态组
* 安全组


## <a name="prerequisites"></a>先决条件
要执行此 API，需要以下**范围**：_Group.ReadWrite.All_ 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /groups
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| Authorization  | string  | Bearer <token>. Required. |

## <a name="request-body"></a>请求正文
下表显示了创建组时至少必须指定的[组](../resources/group.md)资源的属性。 

| 属性 | 类型 | 说明|
|:---------------|:--------|:----------|
| displayName | string | 要在组的通讯簿中显示的名称。 |
| mailEnabled | 布尔 | 对于已启用邮件的组，请设置为 **true**。如果创建 Office 365 组，则将此设置为 **true**。如果创建动态或安全组，则将此设置为 **false**。|
| mailNickname | string | 组的邮件别名。 |
| securityEnabled | 布尔 | 对于启用安全机制的组，请设置为 **true**。如果创建动态或安全组，则将此设置为 **true**。如果创建 Office 365 组，则将此设置为 **false**。 |

如果你正在创建的是 Office 365 或动态组，则按如下所述指定 **groupTypes** 属性。

| 组类型 | **groupTypes** 属性 |
|:--------------|:------------------------|
| Office 365（也称为统一组）| "Unified" | 
| Dynamic | "DynamicMembership" | 
| 安全性 | 请勿设置。 | 

根据需要为你的组指定其他可写属性。有关详细信息，请参阅[组](../resources/group.md)资源的属性。

## <a name="response"></a>响应
如果成功，此方法在响应正文中返回 `201, Created` 响应代码和 [group](../resources/group.md) 对象。

## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是创建 Office 365 组的请求的示例。
<!-- {
  "blockType": "request",
  "name": "create_group_from_groups"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups
Content-type: application/json
Content-length: 244

{
  "description": "Self help community for library",
  "displayName": "Library Assist",
  "groupTypes": [
    "Unified"
  ],
  "mailEnabled": true,
  "mailNickname": "library",
  "securityEnabled": false
}
```

##### <a name="response"></a>响应
下面是一个响应示例。注意：为了简单起见，可能会将此处所示的响应对象截断。将从实际调用中返回更多属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.group"
} -->
```http
HTTP/1.1 201 Created
Content-type: application/json
Content-length: 244

{
  "description": "Self help community for library",
  "displayName": "Library Assist",
  "groupTypes": [
    "Unified"
  ],
  "mail": "library@contoso.onmicrosoft.com",
  "mailEnabled": true,
  "mailNickname": "library",
  "securityEnabled": false
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Create group",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
