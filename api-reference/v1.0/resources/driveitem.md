# <a name="driveitem-resource-type"></a>DriveItem 资源类型

**DriveItem** 资源表示驱动器中的项目。OneDrive 中的所有顶级文件系统对象将作为项目资源返回。 

可使用 `/items/{item-id}` 语法通过其 **id**，或使用 `/drive/root:/path/to/file` 语法通过其文件系统路径访问 **DriveItems**。

项拥有作为属性进行模块化的多个 Facet，用于提供项的标识和功能相关数据。文件夹具有[**文件夹 Facet**](folder.md)，文件具有[**文件 Facet**](file.md)。除了文件 Facet，图像还具有[**图像 Facet**](image.md)。使用照相机拍摄的图像（照片）具有[**照片 Facet**](photo.md)，用于将项标识为照片，并提供照片的拍摄时间和拍摄所用设备等属性。

具有 **文件夹** Facet 的项目充当项目的容器，因此具有指向文件夹下的项目集合的 `children` 引用。


## <a name="json-representation"></a>JSON 表示形式

下面是资源的 JSON 表示形式。

<!-- {
  "blockType": "resource",
  "optionalProperties": [ "children", "createdByUser", "lastModifiedByUser", "permissions", "thumbnails"],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.driveItem"
}-->

```json
{
  "audio": {"@odata.type": "microsoft.graph.audio"},
  "cTag": "string",
  "content": "stream",
  "createdBy": {"@odata.type": "microsoft.graph.identitySet"},
  "createdDateTime": "String (timestamp)",
  "deleted": {"@odata.type": "microsoft.graph.deleted"},
  "eTag": "string",
  "file": {"@odata.type": "microsoft.graph.file"},
  "fileSystemInfo": {"@odata.type": "microsoft.graph.fileSystemInfo"},
  "folder": {"@odata.type": "microsoft.graph.folder"},
  "id": "string (identifier)",
  "image": {"@odata.type": "microsoft.graph.image"},
  "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
  "lastModifiedDateTime": "String (timestamp)",
  "location": {"@odata.type": "microsoft.graph.geoCoordinates"},
  "name": "string",
  "package": {"@odata.type": "microsoft.graph.package"},
  "parentReference": {"@odata.type": "microsoft.graph.itemReference"},
  "photo": {"@odata.type": "microsoft.graph.photo"},
  "remoteItem": {"@odata.type": "microsoft.graph.remoteItem"},
  "searchResult": {"@odata.type": "microsoft.graph.searchResult"},
  "shared": {"@odata.type": "microsoft.graph.shared"},
  "size": 1024,
  "specialFolder": {"@odata.type": "microsoft.graph.specialFolder"},
  "video": {"@odata.type": "microsoft.graph.video"},
  "webDavUrl": "string",
  "webUrl": "string",

  "createdByUser": { "@odata.type": "microsoft.graph.user" },
  "lastModifiedByUser": { "@odata.type": "microsoft.graph.user" },
  "children": [ { "@odata.type": "microsoft.graph.driveItem" }],
  "thumbnails": [ {"@odata.type": "microsoft.graph.thumbnailSet"}],
  "permissions": [ {"@odata.type": "microsoft.graph.permission"} ]
}

```

## <a name="properties"></a>属性

| 属性             | 类型                                | 说明                                                                                                                                                               |
|:---------------------|:------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| audio                | [音频](audio.md)                   | 音频元数据（如果此项是一个音频文件）。只读。                                                                                                                  |
| content              | 流                              | 内容流（如果此项表示一个文件）。                                                                                                                        |
| createdBy            | [identitySet](identityset.md)       | 识别创建项目的用户、设备和应用程序。只读。                                                                                          |
| createdDateTime      | DateTimeOffset                      | 创建项的日期和时间。只读。                                                                                                                                |
| cTag                 | String                              | 项目内容的 eTag。如果只有元数据更改，此 eTag 不会更改。**注意** 如果项目是文件夹，则不返回此属性。只读。 |
| deleted              | [删除](deleted.md)               | 有关项目删除状态的信息。只读。                                                                                                               |
| eTag                 | String                              | 整个项目（元数据和内容）的 eTag。只读。                                                                                                                 |
| 文件                 | [文件](file.md)                     | 文件元数据（如果此项是一个文件）。只读。                                                                                                                          |
| fileSystemInfo       | [fileSystemInfo](filesysteminfo.md) | 客户端上的文件系统信息。读写。                                                                                                                            |
| 文件夹               | [文件夹](folder.md)                 | 文件夹元数据（如果此项是一个文件夹）。只读。                                                                                                                      |
| id                   | String                              | 项在驱动器中的唯一标识符。只读。                                                                                                            |
| image                | [图像](image.md)                   | 图像元数据（如果此项是一个图像）。只读。                                                                                                                       |
| lastModifiedBy       | [identitySet](identityset.md)       | 上次修改项目的用户、设备和应用程序的标识。只读。                                                                                    |
| lastModifiedDateTime | DateTimeOffset                      | 上次修改项目的日期和时间。只读。                                                                                                                      |
| location             | [geoCoordinates](geoCoordinates.md) | 位置元数据（如果此项包含位置数据）。只读。                                                                                                              |
| name                 | String                              | 项目名称（文件名和扩展名）。读写。                                                                                                                |
| 包              | [包](package.md)               | 如果存在，则表示此项是一个包，而不是文件夹或文件。包被视为某些上下文中的文件和其他上下文中的文件夹。只读。         |
| parentReference      | [itemReference](itemreference.md)   | 父信息（如果此项具有父级）。读写。                                                                                                                 |
| 照片                | [照片](photo.md)                   | 照片元数据（如果此项包含照片）。只读。                                                                                                                        |
| remoteItem           | [remoteItem](remoteitem.md)         | 远程项目数据（如果此项是从驱动器共享的项目，而不是被访问的项目）。只读。                                                                        |
| searchResult         | [searchResult](searchresult.md)     | 搜索元数据（如果此项目来自搜索结果）。只读。                                                                                                          |
| 共享               | [共享](shared.md)                 | 表示此项已与他人共享，并提供有关项目共享状态的信息。只读。                                               |
| size                 | Int64                               | 项目大小，以字节为单位。只读。                                                                                                                                     |
| specialFolder        | [specialFolder](specialfolder.md)   | 如果当前项同时也是一个特殊的文件夹，则返回此 facet。只读。                                                                             |
| video                | [视频](video.md)                   | 视频元数据（如果此项是一个视频）。只读。                                                                                                                        |
| webUrl               | String                              | 在浏览器中显示此资源的 URL。只读。                                                                                                                 |

**注意：**ETag 和 cTag 属性在容器（文件夹）中以不同的方式工作。更改任意文件夹后代的内容或元数据时，也会修改 CTag 值。除了从后代派生的属性（例如 **childCount** 或 **lastModifiedDateTime**），仅在更改文件夹的属性时修改 eTag 值。

## <a name="instance-attributes"></a>实例属性

实例属性是具有特殊行为的属性。这些属性是临时的，并且 a) 定义服务应执行的行为或 b) 提供短期的属性值，例如过期项目的下载 URL。

| 属性名称                     | 类型   | 说明                                                                                                                                                         |
|:----------------------------------|:-------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| @microsoft.graph.conflictBehavior | string | 为创建新项目的操作解决冲突的行为。你可以使用值 *fail*、*replace* 或 *rename*。PUT 的默认值是*replace*。绝不会返回包含该批注的项目。只写。                               |
| @microsoft.graph.downloadUrl      | string | 一个可用于下载此文件的内容的 URL。不需要使用此 URL 进行身份验证。只读。                                                    |
| @microsoft.graph.sourceUrl        | string | 发出 PUT 请求时，此实例批注可用于指示服务下载 URL 内容并将其存储为文件。只写。 |

**注意：**@microsoft.graph.downloadUrl 值是一个短期 URL，不能缓存。此 URL 在失效前只能使用很短的时间。

## <a name="relationships"></a>关系

| 关系       | 类型                                       | 说明                                                                                                                                                                       |
|:-------------------|:-------------------------------------------|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| children           | [driveitem](driveitem.md) 集合       | 包含项目直接子项的 Item 对象的集合。仅表示文件夹的项目包含子项。只读。可为 Null。                                        |
| createdByUser      | [用户](user.md)                            | 识别创建项目的用户、设备和应用程序。只读。                                                                                                  |
| lastModifiedByUser | [用户](user.md)                            | 上次修改项目的用户、设备和应用程序的标识。只读。                                                                                            |
| 权限        | [权限](permission.md) 集合     | 项目的权限集。只读。可为 Null。                                                                                                                         |
| 缩略图         | [thumbnailSet](thumbnailset.md) 集合 | 包含与项目关联的 [ThumbnailSet](thumbnailSet.md) 对象的集合。有关详细信息，请参阅 [获取缩略图](../api/thumbnailset_get.md)只读。可为 Null。 |


## <a name="methods"></a>方法

| 方法                                                 | REST 路径                                |
|:-------------------------------------------------------|:-----------------------------------------|
| [获取项目](../api/item_get.md)                         | `GET /drive/items/{item-id}`             |
| [列出子项](../api/item_list_children.md)          | `GET /drive/items/{item-id}/children`    |
| [创建项目](../api/item_post_children.md)            | `POST /drive/items/{item-id}/children`   |
| [更新项目](../api/item_update.md)                   | `PATCH /drive/items/{item-id}`           |
| [上载内容](../api/item_uploadcontent.md)         | `PUT /drive/items/{item-id}/content`     |
| [下载内容](../api/item_downloadcontent.md)     | `GET /drive/items/{item-id}/content`      |
| [删除项目](../api/item_delete.md)                   | `DELETE /drive/items/{item-id}`          |
| [移动项目](../api/item_move.md)                       | `PATCH /drive/items/{item-id}`           |
| [复制项目](../api/item_copy.md)                       | `POST /drive/items/{item-id}/copy`       |
| [搜索项目](../api/item_search.md)                  | `GET /drive/items/{item-id}/search(q='text')`  |
| [查找更改](../api/item_delta.md)                   | `GET /drive/root/delta`                  |
| [列出缩略图](../api/item_list_thumbnails.md)      | `GET /drive/items/{item-id}/thumbnails`  |
| [创建共享链接](../api/item_createlink.md)       | `POST /drive/items/{item-id}/createLink` |
| [添加权限](../api/item_invite.md)               | `POST /drive/items/{item-id}/invite`     |
| [列出权限](../api/item_list_permissions.md)    | `GET /drive/items/{item-id}/permissions` |
| [删除权限](../api/permission_delete.md)       | `DELETE /drive/items/{item-id}/permissions/{perm-id}` |


## <a name="remarks"></a>注解

在 OneDrive for Business 或 SharePoint 文档库中，如果该项目是一个 [文件夹](folder.md)，则不返回 **cTag** 属性。

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "item resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
