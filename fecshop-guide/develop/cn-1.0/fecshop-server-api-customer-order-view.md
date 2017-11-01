Api- Customer Order 查新订单详细
================

> 在账户中心的订单列表,点击view查看订单详情执行的api

URL: `/customer/order/view`

格式：`json`

方式：`get`


一：请求部分
---------

#### 1.Request Header


| 参数名称          | 是否必须    |  类型        |  描述     |
| ------------------| -----:      | :----:       |:----:     |
| access-token      | 必须        |   String     | 从localStorage取出来的值，识别用户登录状态的标示，用户登录成功，服务端返回access-token，VUE保存到localStorage中，在下一次请求从localStorage取出来放到request header中   |
| fecshop-uuid      | 必须        |   String     | 从localStorage取出来的值，用户的唯一标示，VUE第一次访问服务端，服务端会返回fecshop-uuid ，VUE将其保存到本地，后面的每一次请求都需要加上fecshop-uuid    |
| fecshop-currency  | 必须        |   String     | 从localStorage取出来的值，当前的货币值  |
| fecshop-lang      | 必须        |   String     | 从localStorage取出来的值，当前的语言code  |


#### 2.Request Body Form-Data：


| 参数名称        | 是否必须    |  类型       |  描述     |
| ----------------| -----:      | :----:      |:----:     |
| order_id        | 必须        |   String     | Order Id    |


**请求参数示例如下：**

```
{
    order_id:907
}
```

二：返回部分
----------

#### 1.Reponse Header

| 参数名称          | 是否必须    |  类型        |  描述     |
| ------------------| -----:      | :----:       |:----:     |
| access-token      | 选填        |   String     | 用户登录成功，服务端返回access-token，VUE保存到localStorage中，在下一次请求从localStorage取出来放到request header中   |
| fecshop-uuid      | 必须        |   String     | 用户的唯一标示，VUE第一次访问服务端，服务端会返回fecshop-uuid ，VUE将其保存到本地，后面的每一次请求都需要加上fecshop-uuid    |

#### 2.Reponse Body Form-Data：

格式：`json`

| 参数名称        | 是否必须    |  类型       |  描述        |
| ----------------| -----:      | :----:      |:----:        | 
| code            | 必须        |   Number    | 返回状态码，200 代表完成，完整的返回状态码详细参看:[Api- 状态码](fecshop-server-return-code.md) |
| message         | 必须        |   String    | 返回状态字符串描述  |
| data            | 必须        |   Array     | 返回详细数据        |

返回数据举例：

```
{
    "code": 200,
    "message": "process success",
    "data": {
        "order": {
            "order_id": 907,
            "increment_id": "1100000907",
            "order_status": "pending",
            "store": "fecshop.appserver.fancyecommerce.com",
            "created_at": "2017-10-31 12:13:12",
            "updated_at": 1509423192,
            "items_count": 15,
            "total_weight": "825.00",
            "order_currency_code": "EUR",
            "order_to_base_rate": "0.9300",
            "grand_total": "179.55",
            "base_grand_total": "193.00",
            "subtotal": "58.65",
            "base_subtotal": "63.00",
            "subtotal_with_discount": "0.00",
            "base_subtotal_with_discount": "0.00",
            "is_changed": 1,
            "checkout_method": "standard",
            "customer_id": 46,
            "customer_group": null,
            "customer_email": "fdfd@3232.com",
            "customer_firstname": "2121",
            "customer_lastname": "2121",
            "customer_is_guest": 2,
            "remote_ip": null,
            "coupon_code": null,
            "payment_method": "paypal_standard",
            "shipping_method": "fast_shipping",
            "shipping_total": "120.90",
            "base_shipping_total": "130.00",
            "customer_telephone": "2121",
            "customer_address_country": "AT",
            "customer_address_state": "NO",
            "customer_address_city": "2121",
            "customer_address_zip": "2121",
            "customer_address_street1": "2121",
            "customer_address_street2": "2121",
            "txn_type": null,
            "txn_id": null,
            "payer_id": null,
            "ipn_track_id": null,
            "receiver_id": null,
            "verify_sign": null,
            "charset": null,
            "payment_fee": null,
            "payment_type": null,
            "correlation_id": null,
            "base_payment_fee": null,
            "protection_eligibility": null,
            "protection_eligibility_type": null,
            "secure_merchant_account_id": null,
            "build": null,
            "paypal_order_datetime": null,
            "theme_type": null,
            "if_is_return_stock": 2,
            "payment_token": "EC-4VA86601S0151002F",
            "version": 0,
            "customer_address_state_name": "Niederösterreich",
            "customer_address_country_name": "Austria",
            "currency_symbol": "€",
            "products": [
                {
                    "imgUrl": "//img.fancyecommerce.com/media/catalog/product/cache/bd935443df1c50537d4edaab4af5d446/100/100/2/01/20160905101021_28071.jpg",
                    "name": "Raglan Sleeves Letter Printed Crew Neck Sweatshirt kahaki-xl",
                    "sku": "p10001-kahaki-xl",
                    "qty": "15",
                    "row_total": "58.65",
                    "product_id": "580835d0f656f240742f0b7c",
                    "custom_option_info": {
                        "color": "khaki",
                        "size": "XL",
                        "test3": "t_1"
                    }
                }
            ]
        }
    }
}
```