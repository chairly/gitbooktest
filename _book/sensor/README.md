# 神策埋点

|                全埋点                |            页面浏览             |          登录注册          |              下单流程              |           其他           |
| :-------------------------------: | :-------------------------: | :--------------------: | :----------------------------: | :--------------------: |
|        [$启动APP](#AppStart)        |   [APP页面浏览](#appPageView)   | [发送验证码](#sendAuthCode) |      [领取优惠券](#getCoupon)       |  [激活APP](#AppInstall)  |
|        [$退出APP](#$AppEnd)         |    [我的页点击](#myPageClick)    |      [登陆](#login)      | [选择支付方式](#selectPaymentMethod) |    [评价商品](#comment)    |
| [$APP启动（被动）](#$AppStartPassively) |      [推荐展示](#recShow)       |     [注册]( #signUp)     |  [加入购物车](#addToShoppingcart)   | [进入AB测试](#enterAbTest) |
| [$App 浏览页面（全埋点）](#$AppViewScreen) |      [推荐点击](#recClick)      |                        |      [提交订单](#submitOrder)      |     [分享商品](#share)     |
|      [$App 元素点击](#$AppClick)      |        [搜索](#search)        |                        |  [提交订单详情](#submitOrderDetail)  |                        |
|                                   |    [搜索点击](#searchClick)     |                        |       [支付订单](#payOrder)        |                        |
|                                   | [浏览商品详情页](#commodityDetail) |                        |   [支付订单详情](#payOrderDetail)    |                        |
|                                   |    [点击底部TAB](#clickTab)     |                        |                                |    |                    |
## <span id="autoTrack"> 全埋点 </span>

## <span id="pageview"> 页面浏览类埋点 </span>

### <span id="appPageView"> APP页面浏览 </span>

变量名：$appPageView

触发条件：当用户打开页面后触发

|  属性英文变量  | 属性中文显示名 | 属性类型 |    枚举值    | 备注                                       |
| :------: | :-----: | :--: | :-------: | ---------------------------------------- |
| pageName |  页面名称   |  文本  |           | 注意：当页面为首页时，pageName为频道名称；当页面为分类时，pageName为年龄/分类/场景；当页面为活动页时，pageName为链接 |
| pageType |  页面类型   |  文本  | 活动页;首页;分类 | 活动页：页面为H5；首页：页面为首页频道；分类：页面为分类页           |

### <span id="myPageClick"> 我的页点击 </span>

变量名：myPageClick

触发条件：当用户点击“我的页面”中的icon时触发

|     属性英文变量     | 属性中文显示名 | 属性类型 |    枚举值     | 备注               |
| :------------: | :-----: | :--: | :--------: | ---------------- |
|  contentName   |  按钮名称   |  文本  |     -      | 该属性标识用户点击的icon名称 |
| buttonCategory |  按钮类型   |  文本  | 我的百宝箱/精选推荐 | -                |

### <span id="recShow"> 推荐展示 </span>

变量名：recShow

触发条件：当为用户展示完推荐结果后触发

|  属性英文变量   | 属性中文显示名 | 属性类型 |        枚举值        | 备注   |
| :-------: | :-----: | :--: | :---------------: | ---- |
| recPlace  |   推荐位   |  文本  | [点击查看](#recPlace) | -    |
| recSource |  推荐来源   |  文本  |     达观/乐友/阿里云     | -    |

### <span id="recClick"> 推荐点击 </span>

变量名：recClick

触发条件：当用户点击推荐结果后触发

|  属性英文变量   | 属性中文显示名 | 属性类型 |        枚举值        | 备注               |
| :-------: | :-----: | :--: | :---------------: | ---------------- |
| recPlace  |   推荐位   |  文本  | [点击查看](#recPlace) | -                |
| recSource |  推荐来源   |  文本  |     达观/乐友/阿里云     | -                |
|    sku    | sku (1) |  文本  |         -         | 需要修改为commodityID |

### <span id="search"> 搜索 </span>

变量名：search

触发条件：当用户搜索后触发

|   属性英文变量    | 属性中文显示名 | 属性类型 |            枚举值            | 备注               |
| :---------: | :-----: | :--: | :-----------------------: | ---------------- |
|   keyWord   |   关键词   |  文本  |             -             | [点击查看](#keyWord) |
| searchFrom  |  搜索来源   |  文本  |    daguan/leyou/aliyun    | -                |
| searchType  |  搜索类型   |  文本  | 促销ID/分类/关键词、关键字（需要合并为关键词） | 有一部分未知数据，需要排查    |
|  resultNum  | 搜索结果数量  |  数值  |             -             | 当前关键词可以搜索出来的结果数量 |
|  isHistory  | 是否是历史词  |  逻辑  |            真/假            | 用户是否是通过历史词访问的    |
| isRecommend | 是否是推荐词  |  逻辑  |            真/假            | 用户是否是通过推荐词访问的    |

### <span id="searchClick"> 搜索点击 </span>

变量名：searchClick

触发条件：当用户点击搜索结果后触发

|   属性英文变量    | 属性中文显示名 | 属性类型 |            枚举值            | 备注               |
| :---------: | :-----: | :--: | :-----------------------: | ---------------- |
|   keyWord   |   关键词   |  文本  |             -             | [点击查看](#keyWord) |
| subKeyWord  |  二级关键词  |  文本  |             -             | **待补充**          |
| searchFrom  |  搜索来源   |  文本  |    daguan/leyou/aliyun    | -                |
| searchType  |  搜索类型   |  文本  | 促销ID/分类/关键词、关键字（需要合并为关键词） | 有一部分未知数据，需要排查    |
| commodityID |   sku   |  文本  |             -             | 用户点击商品的sku       |
| searchIndex | 点击结果位置  |  数值  |             -             | 用户点击商品的位置        |

### <span id="commodityDetail"> 浏览商品详情 </span>

变量名：commodityDetail

触发条件：当用户浏览商品详情后触发

|       属性英文变量        | 属性中文显示名 | 属性类型 |         枚举值         | 备注                  |
| :-----------------: | :-----: | :--: | :-----------------: | ------------------- |
|     commodityID     |   sku   |  文本  |          -          | 商品sku               |
|    commodityName    |  商品名称   |  文本  |          -          | 商品名称                |
|  secondCommodityID  | 二级分类ID  |  文本  |          -          | -                   |
| secondCommodityName | 二级分类名称  |  文本  |          -          | -                   |
|  forthCommodityID   | 四级分类ID  |  文本  |          -          | -                   |
| forthCommodityName  | 四级分类名称  |  文本  |          -          | -                   |
|  sixthCommodityID   | 六级分类ID  |  文本  |          -          | -                   |
| sixthCommodityName  | 六级分类名称  |  文本  |          -          | -                   |
|  commodityBrandID   |  品牌ID   |  文本  |          -          | -                   |
| commodityBrandName  |  品牌名称   |  文本  |          -          | -                   |
|  preferentialPrice  |  实际售价   |  数值  |          -          | -                   |
|     fromModule      |  来源模块   |  文本  | [点击查看](#fromModule) | [点击查看](#fromModule) |
|       fromTag       | 来源一级标签  |  文本  |  [点击查看](#fromTag)   | [点击查看](#fromTag)    |
|     fromSubTag      | 来源二级标签  |  文本  | [点击查看](#fromSubTag) | [点击查看](#fromSubTag) |
|     purchaseNum     |  购买人数   |  数值  |          -          | 购买该商品的用户数量          |

### <span id="clickTab"> 点击底部TAB </span>

变量名：clickTab

触发条件：当用户点击首页底部TAB后触发

| 属性英文变量  | 属性中文显示名 | 属性类型 | 枚举值  | 备注      |
| :-----: | :-----: | :--: | :--: | ------- |
| tabName |  tab名称  |  文本  |  -   | 底部tab名称 |

## <span id="signPoint"> 登录注册类埋点 </span>

### <span id="sendAuthCode"> 发送验证码 </span>

变量名：sendAuthCode

触发条件：当用户分享成功商品后触发

|  属性英文变量   | 属性中文显示名 | 属性类型 |  枚举值  | 备注   |
| :-------: | :-----: | :--: | :---: | ---- |
| isSuccess |  是否成功   |  文本  | 成功/失败 | -    |

### <span id="login"> 登录 </span>

变量名：login

触发条件：当用户登录成功后触发

|   属性英文变量    | 属性中文显示名 | 属性类型 |    枚举值     | 备注   |
| :---------: | :-----: | :--: | :--------: | ---- |
| loginMethod |  登录方式   |  文本  | 密码登录/验证码登录 | -    |

### <span id="signUp"> 注册 </span>

变量名：signUp

触发条件：当用户注册成功后触发

|    属性英文变量     | 属性中文显示名 | 属性类型 | 枚举值  | 备注          |
| :-----------: | :-----: | :--: | :--: | ----------- |
| recommendCode |   推荐码   |  文本  |  -   | 该用户注册绑定的导购码 |

## <span id="orderPoint"> 下单流程类埋点 </span>

### <span id="getCoupon"> 领取优惠券 </span>

变量名：getCoupon

触发条件：当用户领取优惠券后触发

|   属性英文变量    | 属性中文显示名 | 属性类型 |    枚举值     | 备注       |
| :---------: | :-----: | :--: | :--------: | -------- |
|  couponID   |   券ID   |  文本  |     -      | 券ID      |
| couponName  |   券名    |  文本  |     -      | 优惠券名称    |
| couponValue |  优惠券面值  |  文本  |     -      | 优惠券面值    |
|  fromType   |  优惠券来源  |  文本  | 领券中心/商品详情页 | 用户的领取来源  |
| promotionID |  促销ID   |  文本  |     -      | 券对应的促销ID |

### <span id="selectPaymentMethod"> 选择支付方式 </span>

变量名：selectPaymentMethod

触发条件：当用户选择支付方式后触发

|    属性英文变量     | 属性中文显示名 | 属性类型 | 枚举值  | 备注                     |
| :-----------: | :-----: | :--: | :--: | ---------------------- |
| paymentMethod |  支付方式   |  文本  |  -   | [点击查看](#paymentMethod) |

### <span id="addToShoppingcart"> 加入购物车 </span>

变量名：addToShoppingcart

触发条件：当用户加入商品到购物车后触发

|       属性英文变量        | 属性中文显示名 | 属性类型 |         枚举值         | 备注                  |
| :-----------------: | :-----: | :--: | :-----------------: | ------------------- |
|     commodityID     |   sku   |  文本  |          -          | 商品sku               |
|    commodityName    |  商品名称   |  文本  |          -          | 商品名称                |
|  secondCommodityID  | 二级分类ID  |  文本  |          -          | -                   |
| secondCommodityName | 二级分类名称  |  文本  |          -          | -                   |
|  forthCommodityID   | 四级分类ID  |  文本  |          -          | -                   |
| forthCommodityName  | 四级分类名称  |  文本  |          -          | -                   |
|  sixthCommodityID   | 六级分类ID  |  文本  |          -          | -                   |
| sixthCommodityName  | 六级分类名称  |  文本  |          -          | -                   |
|  commodityBrandID   |  品牌ID   |  文本  |          -          | -                   |
| commodityBrandName  |  品牌名称   |  文本  |          -          | -                   |
|  preferentialPrice  |  实际售价   |  数值  |          -          | -                   |
|     fromModule      |  来源模块   |  文本  | [点击查看](#fromModule) | [点击查看](#fromModule) |
|       fromTag       | 来源一级标签  |  文本  |  [点击查看](#fromTag)   | [点击查看](#fromTag)    |
|     fromSubTag      | 来源二级标签  |  文本  | [点击查看](#fromSubTag) | [点击查看](#fromSubTag) |
|     purchaseNum     |  购买人数   |  数值  |          -          | -                   |

### <span id="submitOrder"> 提交订单 </span>

变量名：submitOrder

触发条件：当用户提交订单后触发

|       属性英文变量        |   属性中文显示名   | 属性类型 | 枚举值  | 备注                     |
| :-----------------: | :---------: | :--: | :--: | ---------------------- |
|     deliverInfo     | deliverInfo |  文本  |  -   | [点击查看](#paymentMethod) |
|    receiverArea     |    收货地址     |  文本  |  -   | -                      |
|    receiverCity     |    收货城市     |  文本  |  -   | -                      |
|  receiverProvince   |    收货省份     |  文本  |  -   | -                      |
|       orderID       |    订单流水号    |  文本  |  -   | -                      |
|      orderType      |    订单类型     |  文本  |  -   | -                      |
|     orderAmount     |    订单金额     |  数值  |  -   | -                      |
| transportationCosts |     运费      |  数值  |  -   | -                      |

### <span id="submitOrderDetail"> 提交订单详情 </span>

变量名：submitOrderDetail

触发条件：当用户提交订单后触发，订单中每有一个sku触发一次

|        属性英文变量         | 属性中文显示名 | 属性类型 |         枚举值         | 备注                  |
| :-------------------: | :-----: | :--: | :-----------------: | ------------------- |
|      commodityID      |   sku   |  文本  |          -          | 商品sku               |
|     commodityName     |  商品名称   |  文本  |          -          | 商品名称                |
|   secondCommodityID   | 二级分类ID  |  文本  |          -          | -                   |
|  secondCommodityName  | 二级分类名称  |  文本  |          -          | -                   |
|   forthCommodityID    | 四级分类ID  |  文本  |          -          | -                   |
|  forthCommodityName   | 四级分类名称  |  文本  |          -          | -                   |
|   sixthCommodityID    | 六级分类ID  |  文本  |          -          | -                   |
|  sixthCommodityName   | 六级分类名称  |  文本  |          -          | -                   |
|   commodityBrandID    |  品牌ID   |  文本  |          -          | -                   |
|  commodityBrandName   |  品牌名称   |  文本  |          -          | -                   |
|   preferentialPrice   |  实际售价   |  数值  |          -          | -                   |
|      fromModule       |  来源模块   |  文本  | [点击查看](#fromModule) | [点击查看](#fromModule) |
|        fromTag        | 来源一级标签  |  文本  |  [点击查看](#fromTag)   | [点击查看](#fromTag)    |
|      fromSubTag       | 来源二级标签  |  文本  | [点击查看](#fromSubTag) | [点击查看](#fromSubTag) |
|      purchaseNum      |  购买人数   |  数值  |          -          | -                   |
| totalPriceOfCommodity |  支付金额   |  数值  |          -          | -                   |
|    commodityNumber    |  商品数量   |  数值  |          -          | 购买该商品的数量            |
|     originalPrice     |   市场价   |  数值  |          -          | -                   |
|        orderID        |  订单流水号  |  文本  |          -          | -                   |
|       orderType       |  订单类型   |  文本  |          -          | -                   |
|      purchaseNum      |  购买人数   |  文本  |          -          | -                   |

### <span id="payOrder"> 支付订单 </span>
**应该跟提交订单保持一致**
变量名：payOrder

触发条件：当用户支付订单后触发

|        属性英文变量         | 属性中文显示名 | 属性类型 | 枚举值  | 备注                     |
| :-------------------: | :-----: | :--: | :--: | ---------------------- |
|        orderID        |  订单流水号  |  文本  |  -   | -                      |
|       orderType       |  订单类型   |  文本  |  -   | -                      |
| totalPriceOfCommodity |  订单总金额  |  数值  |  -   | -                      |
|  actualPaymentAmount  | 实际支付金额  |  数值  |  -   | -                      |
|     paymentMethod     |  支付方式   |  文本  |  -   | [点击查看](#paymentMethod) |

### <span id="payOrderDetail"> 支付订单详情 </span>

变量名：payOrderDetail

触发条件：当用户支付订单后触发，订单中每有一个sku触发一次

|        属性英文变量         | 属性中文显示名 | 属性类型 |         枚举值         | 备注                     |
| :-------------------: | :-----: | :--: | :-----------------: | ---------------------- |
|      commodityID      |   sku   |  文本  |          -          | 商品sku                  |
|     commodityName     |  商品名称   |  文本  |          -          | 商品名称                   |
|   secondCommodityID   | 二级分类ID  |  文本  |          -          | -                      |
|  secondCommodityName  | 二级分类名称  |  文本  |          -          | -                      |
|   forthCommodityID    | 四级分类ID  |  文本  |          -          | -                      |
|  forthCommodityName   | 四级分类名称  |  文本  |          -          | -                      |
|   sixthCommodityID    | 六级分类ID  |  文本  |          -          | -                      |
|  sixthCommodityName   | 六级分类名称  |  文本  |          -          | -                      |
|   commodityBrandID    |  品牌ID   |  文本  |          -          | -                      |
|  commodityBrandName   |  品牌名称   |  文本  |          -          | -                      |
|   preferentialPrice   |  实际售价   |  数值  |          -          | -                      |
|      fromModule       |  来源模块   |  文本  | [点击查看](#fromModule) | [点击查看](#fromModule)    |
|        fromTag        | 来源一级标签  |  文本  |  [点击查看](#fromTag)   | [点击查看](#fromTag)       |
|      fromSubTag       | 来源二级标签  |  文本  | [点击查看](#fromSubTag) | [点击查看](#fromSubTag)    |
|      purchaseNum      |  购买人数   |  数值  |          -          | -                      |
|    commodityNumber    |  商品数量   |  数值  |          -          | 购买该商品的数量               |
|     originalPrice     |   市场价   |  数值  |          -          | -                      |
|        orderID        |  订单流水号  |  文本  |          -          | -                      |
|       orderType       |  订单类型   |  文本  |          -          | -                      |
|      purchaseNum      |  购买人数   |  文本  |          -          | -                      |
|     paymentMethod     |  支付方式   |  文本  |          -          | [点击查看](#paymentMethod) |
| totalPriceOfCommodity |  订单总金额  |  数值  |          -          | -                      |

## <span id="elsePoint"> 其他埋点 </span>

### <span id="AppInstall"> App激活 </span>
变量名：AppInstall

触发条件：当设备首次激活后触发

|        属性英文变量         | 属性中文显示名 | 属性类型 | 枚举值  | 备注                     |
| :-------------------: | :-----: | :--: | :--: | ---------------------- |
|        -        |  -  |  -  |  -   | -                      |

### <span id="comment"> 评价商品 </span>
变量名：comment

触发条件：当用户评价商品后触发

|        属性英文变量         | 属性中文显示名 | 属性类型 | 枚举值  | 备注                     |
| :-------------------: | :-----: | :--: | :--: | ---------------------- |
|        commodityID        |  sku  |  文本  |  -   | -                 |
|        commodityName        |  商品名称  |  文本  |  -   | -                 |
|        commodityScore        |  评价分数  |  数值  |  -   | -                 |

### <span id="enterAbTest"> 进入AB测试 </span>
变量名：enterAbTest

触发条件：当用户进入AB测试后触发

|        属性英文变量         | 属性中文显示名 | 属性类型 | 枚举值  | 备注                     |
| :-------------------: | :-----: | :--: | :--: | ---------------------- |
|        ParticipationGrouping        |  参与分组  |  文本  |  -   | testin中的实验分组                 |
|        ExperimentalVariable        |  实验变量  |  文本  |  -   | testin中的实验变量                 |

### <span id="share"> 分享商品 </span>

变量名：share

触发条件：当用户分享成功商品后触发

|    属性英文变量     | 属性中文显示名 | 属性类型 |            枚举值             | 备注        |
| :-----------: | :-----: | :--: | :------------------------: | --------- |
|  commodityID  |   sku   |  文本  |             -              | 分享商品sku   |
|  shareMethod  |  分享方式   |  文本  | 微信好友/复制链接/微信朋友圈/QQ好友/新浪/其他 | -         |
| commodityName |  商品名称   |  文本  |             -              | 分享商品的商品名称 |


## 












