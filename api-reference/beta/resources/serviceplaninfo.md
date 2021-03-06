# <a name="serviceplaninfo-resource-type"></a>servicePlanInfo 资源类型

包含与订阅的 SKU 相关的服务计划有关的信息。[subscribedSku](subscribedsku.md) 实体的 **servicePlans** 属性是一个 **servicePlanInfo** 集合。


## <a name="properties"></a>属性
| 属性       | 类型    |说明|
|:---------------|:--------|:----------|
|servicePlanId|Guid|服务计划的唯一标识符。|
|servicePlanName|String|服务计划的名称。|
|provisioningStatus|String|服务计划的预配状态。|
|appliesTo|String||


## <a name="json-representation"></a>JSON 表示形式

下面是资源的 JSON 表示形式。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.servicePlanInfo"
}-->

```json
{
  "appliesTo": "string",
  "provisioningStatus": "string",
  "servicePlanId": "guid",
  "servicePlanName": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "servicePlanInfo resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
