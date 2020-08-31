# DataManager (app.data_manager.engine)

# import_data_from_csv

CSV文件导入数据进入底层数据库

```python
import_data_from_csv(
    self,
    file_path: str, # csv文件路径
    symbol: str, # 合约代码
    exchange: Exchange, # 交易所
    interval: Interval, # 数据时间间隔
    datetime_head: str, # datetime表头
    open_head: str, # open表头
    high_head: str, # high表头
    low_head: str, # low表头
    close_head: str, # close表头
    volume_head: str, # volume表头
    open_interest_head: str, # open_interest表头
    datetime_format: str # datetime格式字符串
) -> Tuple:
```

# BaseDatabaseManager(trader.database.databse)

`trader.databse.__init__ ` 文件中判断是否设置 `VNPY_TESTING` 环境变量，如果没有设置，则通过 `vnpy.trader.setting.get_settings` 获取数据库配置，然后通过 `vnpy.trader.database.initialize.init` 获得数据管理器。



