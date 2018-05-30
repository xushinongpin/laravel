# foods.json【 商品表 】

# city.json【 城市表 】

# goods.json【 分类表+商品表 】

# index.json【 分类表 + 商品表 】

# ratings.json【 评论表 】

# search.json 【 商品表 】

# seller.json【 商家表 】

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
score       ---  评分 1-5 【 五颗星 】
rateType    ---  好评或差评手势  0 好评 1差评
text        ---  评论描述
avatar      ---  评论人头像
recommend   ---  推荐标签【 关键词，多个用逗号隔开 】

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

商家表+用户表
id           --- 商家id
count        --- 
name         --- 名称
description  --- 描述
deliveryTime --- 上菜时间或送达时间
score        --- 综合平分，最高5
serviceScore --- 服务态度，最高5
foodScore    --- 商品平分，最高5
rankRate     --- 等级率 【 高于周边商家百分之多少 】
minPrice     --- 起送价
deliveryPrice--- 配送费
ratingCount  --- 总评论数
sellCount    --- 月销售
bulletin     --- 公告
supports     --- 活动【 数组 】
avatar       --- 商家主头像
pics         --- 商家实景图片 【 数组，多个逗号隔开 】
infos        --- 商家信息 【 数组，多个逗号隔开 】
```

# 



