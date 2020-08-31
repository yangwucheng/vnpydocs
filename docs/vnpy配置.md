# vnpy配置

`vnpy.trader.setting` 可以通过 `vt_setting.json` 文件覆盖默认配置，配置文件格式如下

```json
{
    "font.family": "Arial",
    "font.size": 12,

    "log.active": True,
    "log.level": CRITICAL,
    "log.console": True,
    "log.file": True,

    "email.server": "smtp.qq.com",
    "email.port": 465,
    "email.username": "",
    "email.password": "",
    "email.sender": "",
    "email.receiver": "",

    "rqdata.username": "",
    "rqdata.password": "",

    "database.timezone": get_localzone().zone,
    "database.driver": "sqlite",
    "database.database": "database.db",
    "database.host": "localhost",
    "database.port": 3306,
    "database.user": "root",
    "database.password": "",
    "database.authentication_source": "admin",

    "genus.parent_host": "",
    "genus.parent_port": "",
    "genus.parent_sender": "",
    "genus.parent_target": "",
    "genus.child_host": "",
    "genus.child_port": "",
    "genus.child_sender": "",
    "genus.child_target": "",
}
```



`vt_setting.json` 存放在个人目录，例如 `/root/.vntrader/vt_setting.json` ，配置 `mongodb` 的 `vt_setting.json` 如下：

```json
{
    "database.driver": "mongodb",
    "database.database": "vnpy",
    "database.host": "localhost",
    "database.port": 27017
}
```



