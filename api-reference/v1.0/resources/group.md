# <a name="group-resource-type"></a>组资源类型

表示 Azure Active Directory 组，可以是 Office 365 组、动态组或安全组。继承自 [directoryObject](directoryobject.md)。


## <a name="methods"></a>方法

| 方法       | 返回类型  |说明|
|:---------------|:--------|:----------|
|[创建组](../api/group_post_groups.md) | [组](group.md) |创建新组。它可以是 Office 365 组、动态组或安全组。|
|[获取组](../api/group_get.md) | [组](group.md) |读取 group 对象的属性。|
|[列出组](../api/group_list.md) |[组](group.md) 集合 |列出 group 对象及其属性。|
|[更新组](../api/group_update.md) | [组](group.md) |更新 group 对象的属性。 |
|[删除组](../api/group_delete.md) | 无 |删除组对象。 |
|[添加成员](../api/group_post_members.md) |无| 通过发布到 **members** 导航属性将用户或组添加到此组（仅支持安全组和启用邮件的安全组）。|
|[列出成员](../api/group_list_members.md) |[directoryObject](directoryobject.md) 集合| 从 **members** 导航属性中获取属于此组的直接成员的用户和组。|
|[删除成员](../api/group_delete_members.md) | 无 |通过 **members** 导航属性删除 Office 365 组、安全组或启用邮件的安全组中的成员。可以删除用户或其他组。 |
|[列出 memberOf](../api/group_list_memberof.md) |[directoryObject](directoryobject.md) 集合| 从 **memberOf** 导航属性中获取此组是其直接成员的组。|
|[添加所有者](../api/group_post_owners.md) |无| 通过发布到 **owners** 导航属性添加此组的新所有者（仅支持安全组和启用邮件的安全组）。|
|[列出所有者](../api/group_list_owners.md) |[directoryObject](directoryobject.md) 集合| 从 **owners** 导航属性中获取此组的所有者。|
|[删除所有者](../api/group_delete_owners.md) | 无 |通过 **owners** 导航属性删除 Office 365 组、安全组或启用邮件的安全组中的所有者。|
|[checkMemberGroups](../api/group_checkmembergroups.md)|String collection|在一列组中检查此组的成员身份。此函数是可传递的。|
|[getMemberGroups](../api/group_getmembergroups.md)|String collection|返回此组是其成员的所有组。此函数是可传递的。|
|[getMemberObjects](../api/group_getmemberobjects.md)|String collection|返回此组是其成员的所有组。此函数是可传递的。 |
|[创建事件](../api/group_post_events.md) |[Event](event.md)| 通过发布到事件集合创建新事件。|
|[列出事件](../api/group_list_events.md) |[事件](event.md) 集合| 获取 Event 对象集合。|
|[列出 calendarView](../api/group_list_calendarview.md) |[事件](event.md) 集合| 获取指定时间范围内的事件集合。|
|[创建对话](../api/group_post_conversations.md) |[对话](conversation.md)| 通过发布到对话集合创建新对话。|
|[列出对话](../api/group_list_conversations.md) |[对话](conversation.md) 集合| 获取 Conversation 对象集合。|
|[列出线程](../api/group_list_threads.md) |[ConversationThread](conversationthread.md) 集合| 获取某个组的所有线程。|
|[列出 acceptedSenders](../api/group_list_acceptedsenders.md) |[directoryObject](directoryobject.md) 集合| 获取此组 acceptedSenders 列表中的用户或组列表。|
|[添加 acceptedSender](../api/group_post_acceptedsenders.md) |[directoryObject](directoryobject.md)| 将用户或组添加到 acceptSenders 集合。|
|[删除 acceptedSender](../api/group_delete_acceptedsenders.md) |[directoryObject](directoryobject.md)| 从 acceptedSenders 集合中删除用户或组。|
|[添加 rejectedSender](../api/group_post_rejectedsenders.md) |[directoryObject](directoryobject.md)| 将新用户或组添加到 rejectedSenders 集合。|
|[列出 rejectedSenders](../api/group_list_rejectedsenders.md) |[directoryObject](directoryobject.md) 集合| 获取此组 rejectedSenders 列表中的用户或组列表。|
|[删除 rejectedSender](../api/group_delete_rejectedsenders.md) |[directoryObject](directoryobject.md)| 从 rejectedSenders 集合中删除新用户或组。|
|[addFavorite](../api/group_addfavorite.md)|无|将组添加到当前用户的收藏夹组列表中。仅支持 Office 365 组。|
|[removeFavorite](../api/group_removefavorite.md)|无|从当前用户收藏夹组列表中删除组。仅支持 Office 365 组。|
|[subscribeByMail](../api/group_subscribebymail.md)|无|将 isSubscribedByMail 属性设置为 **true**。使当前用户可以接收电子邮件对话。仅支持 Office 365 组。|
|[unsubscribeByMail](../api/group_unsubscribebymail.md)|无|将 isSubscribedByMail 属性设置为 **false**。禁止当前用户接收电子邮件对话。仅支持 Office 365 组。|
|[resetUnseenCount](../api/group_resetunseencount.md)|无|将当前用户自上次访问后未查看的所有帖子的 unseenCount 重置为 0。仅支持 Office 365 组。|


## <a name="properties"></a>属性
| 属性       | 类型    |说明|
|:---------------|:--------|:----------|
|allowExternalSenders|Boolean|默认为 **false**。指明组织外部人员能否向群组发送邮件。|
|autoSubscribeNewMembers|Boolean|默认为 **false**。指示添加到组中的新成员是否将自动订阅接收电子邮件通知。可以在 PATCH 请求中设置组的该属性；不要在创建该组的初始 POST 请求中设置该属性。|
|说明|String|可选的组说明。 |
|displayName|String|组的显示名称。此属性是在创建组时所必需的，并且在更新过程中不能清除。支持 $filter 和 $orderby。|
|groupTypes|String collection| 指定要创建的组类型。可能的值是 **Unified**（创建 Office 365 组）或 **DynamicMembership**（创建动态组）。对于所有其他类型的组（例如启用安全机制的组和启用电子邮件的安全组）则不设置此属性。支持 $filter。|
|id|String|组的唯一标识符。继承自 [directoryObject](directoryobject.md)。键。不可为 null。只读。|
|isSubscribedByMail|Boolean|默认值为 **True**。指示当前用户是否订阅接收电子邮件对话。|
|邮件|String|组的 SMTP 地址，例如，“serviceadmins@contoso.onmicrosoft.com”。只读。支持 $filter。|
|mailEnabled|Boolean|指定该组是否启用邮件。如果 **securityEnabled** 属性也为 **true**，则该组是已启用邮件的安全组；否则是 Microsoft Exchange 通讯组。|
|mailNickname|String|组的邮件别名。创建组时必须指定此属性。支持 $filter。|
|onPremisesLastSyncDateTime|DateTimeOffset|指示组最后一次与本地目录同步的时间。时间戳类型表示使用 ISO 8601 格式的日期和时间信息，并且始终处于 UTC 时间。例如，2014 年 1 月 1 日午夜 UTC 如下所示：`'2014-01-01T00:00:00Z'`。只读。支持 $filter。|
|onPremisesSecurityIdentifier|String|包含从本地同步到云的组的本地安全标识符 (SID)。只读。 |
|onPremisesSyncEnabled|Boolean|如果此组从本地目录同步，则为 **true**；如果此组最初从本地目录同步，但以后不再同步，则为 **false**；如果此对象从未从本地目录同步，则为 **null**（默认值）。只读。支持 $filter。|
|proxyAddresses|String collection| 需要多值属性筛选器表达式的 **any** 运算符。只读。不可为 null。支持 $filter。 |
|securityEnabled|Boolean|指定是否为安全组。如果 **mailEnabled** 属性也为 true，则该组是已启用邮件的安全组；否则为安全组。对于 Office 365 组，必须为 **false**。支持 $filter。|
|unseenCount|Int32|当前用户自上次访问后未查看的帖子计数。|
|visibility|String| 指定 Office 365 组的可见性。可能的值是：**专用**、**公用**或空（解释为**公用**）。|

## <a name="relationships"></a>关系
| 关系 | 类型    |说明|
|:---------------|:--------|:----------|
|acceptedSenders|[directoryObject](directoryobject.md) 集合|允许在此组中创建帖子或日历事件的用户或组列表。如果此列表为非空，则仅允许此处列出的用户或组发布内容。|
|日历|[日历](calendar.md)|组日历。只读。|
|calendarView|[事件](event.md) 集合|日历的日历视图。只读。|
|conversations|[对话](conversation.md) 集合|组对话。|
|createdOnBehalfOf|[directoryObject](directoryobject.md)| 创建组的用户（或应用程序）。注意：如果用户是管理员，则不设置此关系。只读。|
|驱动器|[驱动器](drive.md)|组的驱动器。只读。|
|events|[事件](event.md) 集合|组的日历事件。|
|memberOf|[directoryObject](directoryobject.md) 集合|此组所属的组。HTTP 方法：GET（支持所有组）只读。可为 Null。|
|members|[directoryObject](directoryobject.md) 集合| 属于此组成员的用户和组。HTTP 方法：GET（支持所有组），POST（支持 Office 365 组、安全组和启用邮件的安全组）、DELETE（支持 Office 365 组和安全组），可为 Null。|
|owners|[directoryObject](directoryobject.md) 集合|组的所有者。所有者是一组允许修改此对象的非管理员用户。仅限 10 个所有者。HTTP 方法：GET（支持所有组），POST（支持 Office 365 组、安全组和启用邮件的安全组）、DELETE（支持 Office 365 组和安全组）。可为 Null。|
|照片|[profilePhoto](profilephoto.md)| 组的个人资料照片 |
|rejectedSenders|[directoryObject](directoryobject.md) 集合|不允许在此组中创建帖子或日历事件的用户或组列表。可为 Null|
|threads|[conversationThread](conversationthread.md) 集合| 组的对话线程。可为 Null。|


## <a name="json-representation"></a>JSON 表示形式

下面是资源的 JSON 表示形式。

<!-- {
  "blockType": "resource",
  "optionalProperties": [
    "acceptedSenders",
    "appRoleAssignments",
    "calendar",
    "calendarView",
    "conversations",
    "createdOnBehalfOf",
    "drive",
    "events",
    "memberOf",
    "members",
    "owners",
    "photo",
    "rejectedSenders",
    "threads"
  ],
  "keyProperty": "id",
  "@odata.type": "microsoft.graph.group"
}-->

```json
{
  "allowExternalSenders": false,
  "autoSubscribeNewMembers": true,
  "description": "string",
  "displayName": "string",
  "groupTypes": ["string"],
  "id": "string (identifier)",
  "isSubscribedByMail": true,
  "mail": "string",
  "mailEnabled": true,
  "mailNickname": "string",
  "onPremisesLastSyncDateTime": "String (timestamp)",
  "onPremisesSecurityIdentifier": "string",
  "onPremisesSyncEnabled": true,
  "proxyAddresses": ["string"],
  "securityEnabled": true,
  "unseenCount": 1024,
  "visibility": "string",
  "acceptedSenders": [ { "@odata.type": "microsoft.graph.directoryObject"} ],
  "calendar": { "@odata.type": "microsoft.graph.calendar" },
  "calendarView": [{ "@odata.type": "microsoft.graph.event" }],
  "conversations": [ { "@odata.type": "microsoft.graph.conversation" }],
  "createdOnBehalfOf": { "@odata.type": "microsoft.graph.directoryObject" },
  "drive": { "@odata.type": "microsoft.graph.drive" },
  "events": [ { "@odata.type": "microsoft.graph.event" }],
  "memberOf": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "members": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "owners": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "photo": { "@odata.type": "microsoft.graph.profilePhoto" },
  "rejectedSenders": [ { "@odata.type": "microsoft.graph.directoryObject" } ],
  "threads": [ { "@odata.type": "microsoft.graph.conversationThread" }]
}

```

<!-- uuid: 8fcb5dbc-d5aa-4681-8e31-b001d5168d79
2015-10-25 14:57:30 UTC -->
<!-- {
  "type": "#page.annotation",
  "description": "group resource",
  "keywords": "",
  "section": "documentation",
  "tocPath": ""
}-->
