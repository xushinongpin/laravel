当为数据库表添加或编辑当前的BREAD时，您将首先看到BREAD信息，该信息允许您设置显示名称，slug，图标，模型和控制器名称空间，策略名称。您也可以选择是否要为该BREAD类型生成权限。

当您向下滚动时，您将看到与该表格关联的每一行，您可以在其中选择视图中您希望看到每个字段的位置：

BROWSE \(字段将在您浏览当前数据时显示\)

* READ \(字段将在您点击查看当前数据时显示\)
* EDIT \(字段将可见，并允许您编辑数据\)
* ADD \(字段将在您选择创建新数据类型时可见\)
* DELETE \(不涉及删除，因此可以选中或取消选中\)

您也可以选择指定要为每个字段使用的表单类型。这可以是一个TextBox，TextArea，Checkbox，Image和许多其他类型的表单元素。

每个领域还有其他可以包含的细节或选项。这些类型是checkbox，dropdown，radio button和image。

### ①

其他字段选项

#### Text \(Text Box, Text Area, Rich Textbox and Hidden\)【文本（文本框，文本区域，富文本框和隐藏）】

文本框，文本区域，富文本框和隐藏都是文本输入。在JSON中，您可以指定输入的默认值。

```
{
    "default" : "Default text"
}
```

#### Check Box 【复选框】

在Voyager中，复选框转换为切换开关，正如您在看到的那样，on 将包含切换开关打开时的值，off 将包含开关关闭时设置的值。如果 `checked`设置为true，则复选框将打开;否则默认情况下它将关闭。

```
{
    "on" : "On Text",
    "off" : "Off Text",
    "checked" : true
}
```

#### Drop Down【下拉 】

指定输入类型应该是下拉菜单时，您需要指定该下拉列表的值。在JSON中，如果它没有值，则可以指定下拉列表的 default 。此外，在 options 对象中，您将指定 **left **选项的值和 **right **显示的文本。

```
{
    "default" : "option1",
    "options" : {
        "option1": "Option 1 Text",
        "option2": "Option 2 Text"
    }
}
```

#### Image【图片】

图像输入有很多选项。默认情况下，如果你没有指定任何选项没有问题...你的图片仍然会上传。但是，如果您想调整图像大小，设置图像的质量，或者为上传的图像指定缩略图，则需要指定这些详细信息。

**resize： **如果你想指定一个大小，你需要将它包含在resize对象中。如果将高度或宽度设置为空，它将根据设置的**height**或**width**来保持高宽比。因此，对于这个示例，宽度设置为1000像素，并且由于`height`设置为null，因此会将图像宽度调整为1000像素，并根据当前宽高比调整高度。

**quality： **如果您希望以百分比质量压缩图像，则可以在`quality`密钥中指定该百分比。通常70％到100％之间几乎没有图像质量的通知，但图像尺寸可能会大大降低。

**upsize： **这只有在您设置图像的大小时才有效。如果将图像指定为1000像素，并且图像默认小于1000像素，则不会将该图像的大小扩大为1000像素;然而，如果你将upsize设置为true。它会将所有图像升高到指定的调整大小值。

**thumbnails： **缩略图需要一个对象数组。每个对象都是一个新创建的缩略图。每个对象包含2个值，`name`和`scale`。该 `name`将附加到您的缩略图图像上（例如，您上传的图像是ABC.jpg现在将在ABC-medium.jpg中创建一个带有介质名称的缩略图）。比例是您希望缩略图缩放的百分比数量。如果指定，此值将是调整大小宽度和高度的百分比

```
{
    "resize": {
        "width": "1000",
        "height": null
    },
    "quality" : "70%",
    "upsize" : true,
    "thumbnails": [
        {
            "name": "medium",
            "scale": "50%"
        },
        {
            "name": "small",
            "scale": "25%"
        },
        {
            "name": "cropped",
            "crop": {
                "width": "300",
                "height": "250"
            }
        }
    ]
}
```

#### Date & Timestamp

日期和时间戳输入字段是您可以输入日期的地方。在JSON中，您可以指定日期输出的格式值。它允许您使用Carbon的formatLocalized（）方法在浏览和阅读视图中显示格式化的日期

```
{
    "format" : "%Y-%m-%d"
}
```

### ②

# Description

所有类型都可以包含说明，以帮助未来的自己或使用Voyager管理面板的其他用户准确理解特定BREAD输入字段的用途，可以在可选详细信息JSON输入字段中对其进行定义：

```
{
    "description": "A helpful description text here for your future self."
}
```

### ③

# Validation

在BREAD中每行的可选细节部分内部，您还可以使用一些简单的JSON指定验证规则。以下是如何添加验证规则或必填项和最大长度为12的示例

```
{
    "validation": {
        "rule": "required|max:12"
    }
}
```

此外，您可能希望添加一些自定义错误消息，可以这样完成：

```
{
    "validation": {
        "rule": "required|max:12",
        "messages": {
            "required": "This :attribute field is a must.",
            "max": "This :attribute field maximum :max."
        }
    }
}
```

从v.10.10.13开始，您可以通过以下方式执行必需和最大：12规则：

```
{
    "validation": {
        "rules": [
            "required",
            "max:12"
        ]
    }
}
```

### ④

# Generating Slugs

使用面包生成器，您可能希望自动生成特定输入的slug。可以说你有一些职位，有一个标题和一个slug。如果你想从标题属性自动生成slug，你可以包含以下可选细节：

```
{
    "slugify": {
        "origin": "title", 
        "forceUpdate": true
    }
}
```

这将自动从title字段的输入中生成slug。如果slug已经存在，只有在forceUpdate设置为启用时才会更新，默认情况下禁用。

### ⑤

# Relationships

使用BREAD构建器，您可以轻松创建表之间的关系。在页面底部，你会看到一个新的按钮，说'创建关系'

[更多介绍](https://voyager.readme.io/docs/relationships)

### 

### ⑥

# Null Values

您可能希望将输入字段保存为`null`而不是空字符串。 简而言之，在BREAD中，您可以在该字段中包含以下可选详细信息：

```
{
    "null": ""
}
```

这会将空字符串转换为`null`。但是，您可能希望能够为该字段的数据库添加空字符串和`null`。然而，你必须选择一个`null`的替代品，但它可以是任何你想要的。例如，如果您希望字段将字符串（例如Nothing）更改为空值，则可以包含该字段的以下可选详细信息：

```
{
    "null": "Nothing"
}
```

现在在该字段中输入Nothing将最终以数据库中的`null`结束。

### ⑦

# Display options

还有一些选项可以用来改变BREAD的显示方式。您可以将 display 键添加到您的json对象，并更改特定字段的宽度，甚至指定一个自定义ID。

```
{
    "display": {
        "width": "3",
        "id": "custom_id"
    }
}
```

宽度显示在12格系统上。宽度设置为3将占据宽度的25％。 该ID将让你指定一个自定义的ID包装你的元素。例：

```
<div id="custom_id">
    <!-- Your field element -->
</div>
```

textarea行的默认数量是5.这可以更改：

```
{
    "display": {
        "rows": "10"
    }
}
```



