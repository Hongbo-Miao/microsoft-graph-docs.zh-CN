# <a name="update-organization"></a>更新组织

更新当前经过身份验证的组织的属性。
## <a name="prerequisites"></a>先决条件
要执行此 API，需要以下**范围**之一：
## <a name="http-request"></a>HTTP 请求
<!-- { "blockType": "ignored" } -->
```http
PATCH /organization

```
## <a name="request-headers"></a>请求标头
| 名称       | 类型 | 说明|
|:-----------|:------|:----------|
| Authorization  | string  | Bearer <token>. Required. |

## <a name="request-body"></a>请求正文
在请求正文中，提供应更新的相关字段的值。请求正文中不包括的现有属性将保留其以前的值，或根据对其他属性值的更改重新计算。为了获得最佳性能，不应包括尚未更改的现有值。

| 属性       | 类型    |说明|
|:---------------|:--------|:----------|
|assignedPlans|AssignedPlan|与租户相关的服务计划的集合。                          **注意：**不可为 null。            |
|城市|String|            |
|companyLastDirSyncTime|DateTimeOffset|租户上次与本地目录同步的时间和日期。|
|country|String|            |
|countryLetterCode|String|            |
|deletionTimestamp|DateTimeOffset||
|dirSyncEnabled|Boolean|如果此对象从本地目录同步，则为 **true**；如果此对象最初从本地目录同步，但以后不再同步，则为 **false**；如果此对象从未从本地目录同步，则为 **null**（默认值）。|
|displayName|String|租户的显示名称。|
|marketingNotificationEmails|String|                                        **注意：**不可为 null。            |
|objectType|String|一个标识对象类型的字符串。对于租户，该值始终为“公司”。继承自 [directoryObject](../resources/directoryobject.md)。|
|postalCode|String|            |
|preferredLanguage|String|            |
|provisionedPlans|ProvisionedPlan|                                        **注意：**不可为 null。            |
|provisioningErrors|ProvisioningError|                                        **注意：**不可为 null。            |
|securityComplianceNotificationMails|String||
|securityComplianceNotificationPhones|String||
|state|String|            |
|street|String|            |
|technicalNotificationMails|String|                                        **注意：**不可为 null。            |
|telephoneNumber|String|            |
|verifiedDomains|VerifiedDomain|与该租户相关联的域集合。                          **注意：**不可为 null。            |

## <a name="response"></a>响应
如果成功，此方法在响应正文中返回 `200 OK` 响应代码和 [organization](../resources/organization.md) 对象。
## <a name="example"></a>示例
##### <a name="request"></a>请求
下面是一个请求示例。
<!-- {
  "blockType": "request",
  "name": "update_organization"
}-->
```http
PATCH https://graph.microsoft.com/v1.0/organization
Content-type: application/json
Content-length: 411

{
  "assignedPlans": [
    {
      "assignedDateTime": "datetime-value",
      "capabilityStatus": "capabilityStatus-value",
      "service": "service-value",
      "servicePlanId": "servicePlanId-value"
    }
  ],
  "businessPhones": [
    "businessPhones-value"
  ],
  "city": "city-value",
  "country": "country-value",
  "countryLetterCode": "countryLetterCode-value",
  "displayName": "displayName-value"
}
```
##### <a name="response"></a>响应
下面是一个响应示例。注意：为了简单起见，可能会将此处所示的响应对象截断。将从实际调用中返回所有属性。
<!-- {
  "blockType": "response",
  "truncated": true,
  "@odata.type": "microsoft.graph.organization"
} -->
```http
HTTP/1.1 200 OK
Content-type: application/json
Content-length: 411

{
  "assignedPlans": [
    {
      "assignedDateTime": "datetime-value",
      "capabilityStatus": "capabilityStatus-value",
      "service": "service-value",
      "servicePlanId": "servicePlanId-value"
    }
  ],
  "businessPhones": [
    "businessPhones-value"
  ],
  "city": "city-value",
  "country": "country-value",
  "countryLetterCode": "countryLetterCode-value",
  "displayName": "displayName-value"
}
```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "Update organization",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
