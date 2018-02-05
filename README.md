# AreaAndBanks

[![license](https://img.shields.io/badge/license-WTFPL%20--%20Do%20What%20the%20Fuck%20You%20Want%20to%20Public%20License-green.svg)](https://raw.githubusercontent.com/ALawating-Rex/AreaAndBanks/master/LICENSE)

## 抛砖引玉
现在省市区地址的需求越来越多，但是始终缺少一个官方标准，当然 中华人民共和国民政部-中华人民共和国行政区划代码 这里有官方数据，
却不是程序员拿来即用的，开发也不应该在这里浪费时间，所以希望能够有一个统一的标准数据，value和code能够统一真的能够带来极大的便利。
尤其和快递对接的系统多少也会遇到过城市名不匹配的情况吧。
虽然银行支行数据这个使用案例相对较少了，但是标准数据几乎找不到。以上这些数据难道不是应该公开透明且以服务为目的的吗？
所以希望抛砖引玉，有人能整理一个标准数据。

中华人民共和国行政区划：省份、城市、区县、乡镇（街道）

*   数据来源（民政部、国家统计局）：
    * [中华人民共和国民政部-中华人民共和国行政区划代码](http://www.mca.gov.cn/article/sj/tjbz/a/)
    * [中华人民共和国国家统计局-行政区划代码](http://www.stats.gov.cn/tjsj/tjbz/xzqhdm/)
    * [中华人民共和国国家统计局-统计用区划和城乡划分代码](http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/)
    * [中华人民共和国国家统计局-统计用区划代码和城乡划分代码编制规则](http://www.stats.gov.cn/tjsj/tjbz/200911/t20091125_8667.html)
*   本项目已更新至：
    * [最新县及县以上行政区划代码（截止时间：2016-07-31，发布时间：2017-03-10）](http://www.stats.gov.cn/tjsj/tjbz/xzqhdm/201703/t20170310_1471429.html)
    * [2016年统计用区划代码和城乡划分代码（截止时间：2016-07-31，发布时间：2017-05-16）](http://www.stats.gov.cn/tjsj/tjbz/tjyqhdmhcxhfdm/2016/index.html)

## JSON

| 文件列表                                     | 下载地址       |
|:---------------------------------------------|:---------------|
| 银行支行数据                                        | [banks.json](https://github.com/ALawating-Rex/AreaAndBanks/blob/master/data/banks.json) |
| 银行支行SQL数据                                     | [banks.sql](https://github.com/ALawating-Rex/AreaAndBanks/blob/master/data/banks.sql) |
| 省份数据                                        | [provinces.json](https://github.com/ALawating-Rex/AreaAndBanks/blob/master/data/provinces.json) |
| 城市数据                                        | [cities.json](https://github.com/ALawating-Rex/AreaAndBanks/blob/master/data/cities.json) |
| 区县数据                                        | [areas.json](https://github.com/ALawating-Rex/AreaAndBanks/blob/master/data/areas.json) |
| 乡镇（街道）数据                                | [streets.json](https://github.com/ALawating-Rex/AreaAndBanks/blob/master/data/streets.json) |
| “省份、城市” 二级联动数据                       | [pc.json](https://github.com/ALawating-Rex/AreaAndBanks/blob/master/data/pc.json) |
| “省份、城市” 二级联动数据（带编码）             | [pc-code.json](https://github.com/ALawating-Rex/AreaAndBanks/blob/master/data/pc-code.json) |
| “省份、城市、区县” 三级联动数据                 | [pca.json](https://github.com/ALawating-Rex/AreaAndBanks/blob/master/data/pca.json) |
| “省份、城市、区县” 三级联动数据（带编码）       | [pca-code.json](https://github.com/ALawating-Rex/AreaAndBanks/blob/master/data/pca-code.json) |
| “省份、城市、区县、乡镇” 四级联动数据           | [pcas.json](https://github.com/ALawating-Rex/AreaAndBanks/blob/master/data/pcas.json) |
| “省份、城市、区县、乡镇” 四级联动数据（带编码） | [pcas-code.json](https://github.com/ALawating-Rex/AreaAndBanks/blob/master/data/pcas-code.json) |

## 省市区数据参考自
[modood--Administrative-divisions-of-China](https://github.com/modood/Administrative-divisions-of-China)
具体更新数据的方式也参考此链接

## 银行数据说明
1. 银行支行数据大约10万条，json文件比较大，请谨慎查看
2. 银行支行SQL 是一个表的完整导出 包括表结构和数据，导入之后你完全可以自己修改相应字段类型以及优化长度和索引等。
创建表SQL:(不需要单独运行，因为sql文件会创建表 banks，如果你本来就有 banks 这个表，记得备份下，因为sql本身：DROP TABLE IF EXISTS `banks`;)
``` 
CREATE TABLE `banks` (
  `sub_branch_name` varchar(255) NOT NULL,
  `sub_branch_id` varchar(50) DEFAULT NULL,
  `province_id` int(11) DEFAULT NULL,
  `province` varchar(255) DEFAULT NULL,
  `city_id` int(11) DEFAULT NULL,
  `city` varchar(255) DEFAULT NULL,
  `bank_name` varchar(255) NOT NULL,
  `bank_id` int(11) DEFAULT NULL,
  KEY `idx_banks_name` (`bank_id`,`province_id`,`city_id`,`sub_branch_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8
``` 
3. 银行支行数据有很多数据平台支持接口调用，你可以自行搜索相关平台，这里离线的数据已经较老了（当然银行这个数据更新是不频繁的，勉强也能用）。


## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request

## License

this repo is released under the [WTFPL](http://www.wtfpl.net/) – Do What the Fuck You Want to Public License.
