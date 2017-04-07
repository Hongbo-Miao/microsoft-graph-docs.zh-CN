# <a name="nameditem-resource-type"></a>NamedItem 资源类型

表示单元格区域或值的定义名称。名称可以为基元的已命名对象（如以下类型中所示）、range 对象或对区域的引用。此对象可用于获取与名称相关的 range 对象。


## <a name="methods"></a>方法

| 方法           | 返回类型    |说明|
|:---------------|:--------|:----------|
|[获取 NamedItem](../api/nameditem_get.md) | [NamedItem](nameditem.md) |读取 nameditem 对象的属性和关系。|
|[更新](../api/nameditem_update.md) | [NamedItem](nameditem.md)    |更新 NamedItem 对象。 |
|[区域](../api/nameditem_range.md)|[Range](range.md)|返回与名称相关的 range 对象。如果已命名项目的类型不是区域，将引发异常。|
|[列出](../api/nameditem_list.md) | [NamedItem](nameditem.md) 集合 |获取 namedItem 对象集合。 |

## <a name="properties"></a>属性
| 属性       | 类型    |说明|
|:---------------|:--------|:----------|
|name|string|对象的名称。只读。|
|type|string|指示与名称相关的引用类型。可能的值是：`String`、`Integer`、`Double`、`Boolean`、`Range`。只读。|
|value|对象|表示名称定义为引用的公式。例如 =Sheet14!$B$2:$H$12、=4.75 等。只读。|
|visible|boolean|指定对象是否可见。|

## <a name="relationships"></a>关系
无


## <a name="json-representation"></a>JSON 表示形式

下面是资源的 JSON 表示形式。

<!-- {
  "blockType": "resource",
  "optionalProperties": [

  ],
  "@odata.type": "microsoft.graph.namedItem"
}-->

```json
{
  "name": "string",
  "type": "string",
  "value": {"@odata.type": "microsoft.graph.range"},
  "visible": true
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "NamedItem resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->