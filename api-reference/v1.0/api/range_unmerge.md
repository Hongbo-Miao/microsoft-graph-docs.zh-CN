# <a name="range-unmerge"></a>Range: unmerge

将区域单元格拆分为单个单元格。
## <a name="prerequisites"></a>先决条件
要执行此 API，需要以下**范围**： 
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
POST /workbook/names(<name>)/range/unmerge
POST /workbook/worksheets(<id|name>)/range(<address>)/unmerge
POST /workbook/tables(<id|name>)/columns(<id|name>)/range/unmerge

```
## <a name="request-headers"></a>请求标头
| 名称       | 说明|
|:---------------|:----------|
| Authorization  | Bearer <code>|


## <a name="request-body"></a>请求正文

## <a name="response"></a>响应
如果成功，此方法返回 `200, OK` 响应代码。它不在响应正文中返回任何内容。

## <a name="example"></a>示例
下面是一个如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是一个请求示例。
<!-- {
  "blockType": "request",
  "name": "range_unmerge"
}-->
```http
POST https://graph.microsoft.com/v1.0/me/drive/items/{id}/workbook/names(<name>)/range/unmerge
```

##### <a name="response"></a>响应
下面是一个响应示例。 
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.none"
} -->
```http
HTTP/1.1 200 OK
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Range: unmerge",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->