# <a name="group-getmembergroups"></a>group: getMemberGroups
返回指定组所属的所有组。检查是可传递的，这和读取 [memberOf](../api/group_list_memberof.md) 导航属性不同，后者仅返回该组是其直接成员的组。

此功能支持 Office 365 和 Azure AD 中设置的其他类型的组。每个请求可以返回的最大组数为 2046 组。注意：Office 365 组不能包含组。因此，Office 365 组中的成员身份始终是直接的。

## <a name="prerequisites"></a>先决条件
若要执行此 API，必须有以下**范围**之一：*Group.Read.All；Directory.Read.All；Directory.ReadWrite.All；Directory.AccessAsUser.All*

## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /groups/{id}/getMemberGroups
```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:---------------|:--------|:----------|
| Authorization  | string  | Bearer <token>. Required. |

## <a name="request-body"></a>请求正文
在请求正文中，提供具有以下参数的 JSON 对象。

| 参数       | 类型    |说明|
|:---------------|:--------|:----------|
|securityEnabledOnly|Boolean|设置为 **false**。只支持对用户仅返回启用安全机制的组。|

## <a name="response"></a>响应
如果成功，此方法将在包含该组所属组 ID 的响应正文中返回 `200, OK` 响应代码和字符串集合。

## <a name="example"></a>示例
下面是一个如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是一个请求示例。
<!-- {
  "blockType": "request",
  "name": "group_getmembergroups"
}-->
```http
POST https://graph.microsoft.com/v1.0/groups/{id}/getMemberGroups
Content-type: application/json
Content-length: 33

{
  "securityEnabledOnly": false
}
```

##### <a name="response"></a>响应
下面是一个响应示例。注意：为了简单起见，可能会将此处所示的响应对象截断。将从实际调用中返回所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "string",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 39

{
  "value": [
    "string-value"
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "group: getMemberGroups",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
