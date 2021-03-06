# <a name="user-reminderview"></a>user: reminderView
返回指定开始时间和结束时间范围内的日历提醒列表。 

## <a name="prerequisites"></a>先决条件
要执行此 API，需要以下**范围**之一：*Calendars.Read；Calendars.ReadWrite*
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
GET /users/{id | userPrincipalName}/reminderView(startDateTime=startDateTime-value,endDateTime=endDateTime-value)
```

## <a name="function-parameters"></a>函数参数
在请求 URL 中，提供以下包含值的函数参数。

| 参数       | 类型    |说明|
|:---------------|:--------|:----------|
|startDateTime|String|事件（已设置提醒）的开始日期和时间。该值用 ISO 8601 格式表示，例如，“2015-11-08T19:00:00.0000000”。|
|endDateTime|String|事件（已设置提醒）的结束日期和时间。该值用 ISO 8601 格式表示，例如，“2015-11-08T20:00:00.0000000”。|


## <a name="request-headers"></a>请求标头
| 标头       | 值|
|:-----------|:------|
| Authorization  | Bearer <token>. Required.  |
| Content-Type   | application/json |
| Prefer | <Time-zone>。可选，如果缺省，则采用 UTC。| 

## <a name="request-body"></a>请求正文
请勿提供此方法的请求正文。

## <a name="response"></a>响应
如果成功，此方法在响应正文中返回 `200, OK` 响应代码和 [reminder](../resources/reminder.md) 集合对象。

## <a name="example"></a>示例
下面是一个如何调用此 API 的示例。
##### <a name="request"></a>请求
下面是一个请求示例。
<!-- {
  "blockType": "request",
  "name": "user_reminderview"
}-->
```http
GET https://graph.microsoft.com/v1.0/me/reminderView?startDateTime=startDateTime-value&endDateTime=endDateTime-value
```

##### <a name="response"></a>响应
下面是一个响应示例。注意：为了简单起见，可能会将此处所示的响应对象截断。将从实际调用中返回所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.reminder",
  "isCollection": true
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 673

{
  "value": [
    {
      "eventId": "eventId-value",
      "eventStartTime": {
        "dateTime": "dateTime-value",
        "timeZone": "timeZone-value"
      },
      "eventEndTime": {
        "dateTime": "dateTime-value",
        "timeZone": "timeZone-value"
      },
      "changeKey": "changeKey-value",
      "eventSubject": "eventSubject-value",
      "eventLocation": {
        "displayName": "displayName-value",
        "address": {
          "street": "street-value",
          "city": "city-value",
          "state": "state-value",
          "countryOrRegion": "countryOrRegion-value",
          "postalCode": "postalCode-value"
        }
      }
    }
  ]
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "user: reminderView",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
