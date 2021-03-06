# <a name="contactfolder-resource-type"></a>contactFolder 资源类型

包含联系人的文件夹。

## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[获取 contactFolder](../api/contactfolder_get.md) | [contactFolder](contactfolder.md) |通过使用联系人文件夹 ID 获取联系人文件夹。|
|[更新](../api/contactfolder_update.md) | [contactFolder](contactfolder.md) |更新 contactFolder 对象。 |
|[删除](../api/contactfolder_delete.md) | 无 |删除 contactFolder 对象。 |
|[列出 childFolder](../api/contactfolder_list_childfolders.md) |[ContactFolder](contactfolder.md) 集合| 获取指定联系人文件夹下的子文件夹的集合。|
|[创建子 ContactFolder](../api/contactfolder_post_childfolders.md) |[ContactFolder](contactfolder.md)| 创建新的 contactFolder 作为指定文件夹的子文件夹。|
|[列出文件夹中的联系人](../api/contactfolder_list_contacts.md) |[联系人](contact.md) 集合| 从已登录用户的默认联系人文件夹 (`.../me/contacts`) 或指定的联系人文件夹中获取联系人集合。|
|[在文件夹中创建联系人](../api/contactfolder_post_contacts.md) |[联系人](contact.md)| 将联系人添加到联系人根文件夹或其他联系人文件夹的 `contacts` 端点中。|
|[创建单值扩展属性](../api/singlevaluelegacyextendedproperty_post_singlevalueextendedproperties.md) |[contactFolder](contactFolder.md)  |在新建或现有的 contactFolder 中创建一个或多个单值扩展属性。   |
|[获取包含单值扩展属性的 contactFolder](../api/singlevaluelegacyextendedproperty_get.md)  | [contactFolder](contactFolder.md) | 通过使用 `$expand` 或 `$filter` 获取包含一个单值扩展属性的 contactFolder。 |
|[创建多值扩展属性](../api/multivaluelegacyextendedproperty_post_multivalueextendedproperties.md) | [contactFolder](contactFolder.md) | 在新建或现有的 contactFolder 创建一个或多个多值扩展属性。  |
|[获取包含多值扩展属性的 contactFolder](../api/multivaluelegacyextendedproperty_get.md)  | [contactFolder](contactFolder.md) | 使用 `$expand` 获取包含一个多值扩展属性的 contactFolder。 |



## <a name="properties"></a>属性
| 属性       | 类型    |说明|
|:---------------|:--------|:----------|
|displayName|String|文件夹的显示名称。|
|id|String|联系人文件夹的唯一标识符。只读。|
|parentFolderId|String|文件夹的父文件夹 ID。|

## <a name="relationships"></a>关系
| 关系 | 类型    |说明|
|:---------------|:--------|:----------|
|childFolders|[ContactFolder](contactfolder.md) 集合|文件夹中的子文件夹集合。导航属性。只读。可为 Null。|
|联系人|[联系人](contact.md) 集合|文件夹中的联系人。导航属性。只读。可为 Null。|
|multiValueExtendedProperties|[multiValueLegacyExtendedProperty](multivaluelegacyextendedproperty.md) 集合| 为 contactFolder 定义的多值扩展属性的集合。只读。可为 Null。|
|singleValueExtendedProperties|[singleValueLegacyExtendedProperty](singlevaluelegacyextendedproperty.md) collection| 为 contactFolder 定义的单值扩展属性的集合。只读。可为 Null。|


## <a name="json-representation"></a>JSON 表示形式

下面是资源的 JSON 表示形式。

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "childFolders",
    "contacts",
    "multiValueExtendedProperties",
    "singleValueExtendedProperties"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.contactFolder"
}-->

```json
{
  "displayName": "string",
  "id": "string (identifier)",
  "parentFolderId": "string"
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "contactFolder resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
