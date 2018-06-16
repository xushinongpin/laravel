当为数据库表添加或编辑当前的BREAD时，您将首先看到BREAD信息，该信息允许您设置显示名称，slug，图标，模型和控制器名称空间，策略名称。您也可以选择是否要为该BREAD类型生成权限。

当您向下滚动时，您将看到与该表格关联的每一行，您可以在其中选择视图中您希望看到每个字段的位置：

BROWSE \(字段将在您浏览当前数据时显示\)

* READ \(字段将在您点击查看当前数据时显示\)
* EDIT \(字段将可见，并允许您编辑数据\)
* ADD \(字段将在您选择创建新数据类型时可见\)
* DELETE \(不涉及删除，因此可以选中或取消选中\)

您也可以选择指定要为每个字段使用的表单类型。这可以是一个TextBox，TextArea，Checkbox，Image和许多其他类型的表单元素。

每个领域还有其他可以包含的细节或选项。这些类型是checkbox，dropdown，radio button和image。

①

其他字段选项

#### Text \(Text Box, Text Area, Rich Textbox and Hidden\)【文本（文本框，文本区域，富文本框和隐藏）】

文本框，文本区域，富文本框和隐藏都是文本输入。在JSON中，您可以指定输入的默认值。

```
{
    "default" : "Default text"
}
```

#### Check Box 【复选框】

在Voyager中，复选框转换为切换开关，正如您在上面看到的那样，on 将包含切换开关打开时的值，off 将包含开关关闭时设置的值。如果 `checked `设置为true，则复选框将打开;否则默认情况下它将关闭。

```
{
    "on" : "On Text",
    "off" : "Off Text",
    "checked" : true
}
```



