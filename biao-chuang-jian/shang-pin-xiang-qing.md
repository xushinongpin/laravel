# foods.json【 商品表 】

# city.json【 城市表 】

# goods.json【 分类表+商品表 】

# index.json【 分类表 + 商品表 】

```
商品表
id          ---  自增id
tid         ---  分类id
sid         ---  商家id
cid         ---  城市id
name        ---  商品名称
price       ---  商品当前价格
oldPrice    ---  商品原价
sellCount   ---  月销售额
rating      ---  好评率
description ---  商品描述
info        ---  商品信息
icon        ---  商品小图 114*114 链接地址
image       ---  商品大图 750*750 链接地址
recommend   ---  是否推荐 1推荐 2或其他不推荐 默认2

评论关联表
id          ---  自增id
gid         ---  商品id
uid         ---  关联用户id
rid         ---  评论关联id
username    ---  评论人名称
rateTime    ---  评论时间
rateType    ---  好评或差评手势  0 好评 1差评
text        ---  评论描述
avatar      ---  评论人头像

城市表
id          ---  自增id
cid         ---  关联id
spell       ---  地区英文名
name        ---  地区中文名

分类表
id          ---  分类id
name        ---  分类名称
type        ---  0减 1折 2特 3票 4保
imgUrl      ---  分类icon链接地址
sort        ---  排序
attribute   ---  属性 1首页显示 2不显示
```

# 



