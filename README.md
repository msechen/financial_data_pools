### 重新编写了获取历史交易数据
需要下载的包：`akshare`；通过 `pip install akshare` 安装。

### 新增同花顺操作文件，通过操作同花顺进行自动化交易
需要下载的包：`pyperclip`、`pywinauto`、`pandas`；通过`pip install` 安装即可。

### 多进程、多线程、协程秒级爬取A股市场交易数据

#### 目前能够获取的数据包括：
- 业绩报表，秒级爬取一个季度数据
- 资产负债表，秒级爬取一个季度数据
- 现金流量表，秒级爬取一个季度数据
- 利润表，秒级爬取一个季度数据
- 停复牌信息，秒级爬取两年数据
- 解禁个股信息，秒级爬取两年数据
- 板块概念，秒级爬取所有数据
- 历史交易数据程序重新编写，速度再次提升50%左右，6分钟左右完成
- 个股公告，秒级爬取两年公告数据
- 沪深港通，秒级爬取盘后所有数据
- 以上数据支持全量下载，比如根据时间下载任何季度的业绩报表

#### 代码需要的运行环境：
- Python3，本机的Python版本为3.7.9，[下载地址](https://www.python.org/downloads/)
- redis，代码使用了redis作为队列临时存储数据
- MySQL，作为数据存储，[下载地址](https://www.mysql.com/downloads/)
- Python的第三方包，包括pandas，pymysql等，详情参照requirements.txt文件及**安装依赖**项

##### 安装依赖:

```bash
pip3 install -r requirements.txt
```
附依赖包：

```
numpy==1.19.2
pandas==1.1.2
Pillow==7.2.0
PyMySQL==0.10.1
redis==3.5.3
requests==2.20.0
seaborn==0.11.0
selenium==3.141.0
SQLAlchemy==1.4.22
lxml==4.6.3
akshare==1.0.90
```


##### 配置文件
- window环境配置文件名为config.yaml

- 包括数据本地保存路径和名字、MySQL和redis等配置
###### 列出的配置中只需要将对应的配置值改成自己的

```
...
# 本地保存路径
save_path:
    stock:              # A股
        detail:         # 每日交易数据
            path: F:\csv\detail
            file_name: <<date>>.csv

        daily:                                # 日线
            path: F:\csv\daily                # 日k保存地址
            file_name: <<stock_code>>.csv     # 保存的名称，如 000001.csv

        weekly:
            path: F:\csv\weekly               # 周k保存地址
            file_name: <<stock_code>>.csv     # 保存的名称，如 000001.csv

        monthly:
            path: F:\csv\monthly              # 月k保存地址
            file_name: <<stock_code>>.csv     # 保存的名称，如 000001.csv
```

#### 代码的文件及说明
- create_tables 文件夹，里面放的是数据库建表语句，导入或者当个执行建表
- data_urls.py，数据接口链接地址
- config.yaml，配置文件地址
- comm_funcs.py，公用的方法/类库
- coroutine_balancesheets_down.py，资产负债表下载程序，里面附有示例
- coroutine_cashflow_down.py，现金流量表下载程序，附有使用示例
- coroutine_financial_down.py，利润表下载程序，附有使用示例
- coroutine_statements_down.py，业绩报表下载程序，附有使用示例
- coroutine_suspended_down.py，停复牌信息下载程序，附有使用示例
- coroutine_unlocked_down.py，解禁个股信息下载程序，附有使用示例
- coroutine_tradedetail_down.py，个股每日交易信息下载程序，附有使用示例
- history_trade_down.py，历史交易数据下载(重新编写后的)
- coroutine_lhblist_down.py，龙虎榜数据下载
- financing_notices_down.py，公告下载
- concepts_down.py 个股概念板块下载
- coroutine_hsgt_down.py 沪深港通下载

#### 问题反馈
任何问题欢迎在[Issues]中反馈, 你的反馈会让此项目变得更加完美。


