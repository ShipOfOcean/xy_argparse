# xy_argparse

- zh_CN [简体中文](README_zh_CN.md)
- zh_TW [繁体中文](README_zh_TW.md)
- en [English](README_en.md)

# 说明
简单Python控制台输入输出工具封装.

<a href="https://github.com/ShipOfOcean/xy_argparse.git" target="_blank">Github地址</a>

## 安装

```bash
pip install xy_argparse
```

## 开始

```python
# main.py
from argparse import Namespace
from xy_argparse.ArgParse import ArgParse

class Runner(ArgParse):
    work_list = [
        "backup",
        "install",
        "install_pack",
        "load",
    ]
    @property
    def version(self):
        return "0.0.1"
    
    def __init__(self):
        self.prog = "xy_conda"
        self.description = "conda相关工具"

    def main(self):
        self.default_parser()
        self.add_arguments()
        self.parse_arguments()
        if self.work:
            self.run_arguments()
        else:
            self.parser.print_help()

    def add_arguments(self):
        self.add_argument(
            flag="-w",
            name="--work",
            help_text="""
                工作方式:
                "backup",
                "install",
                "install_pack",
                "load",
            """,
        )

    def on_arguments(
        self,
        name,
        value,
        arguments=None,
    ):
        # "backup",
        # "install",
        # "install_pack",
        # "load",
        if name == "work":
            if value == "backup":
                self.backup()
                return False
            elif value == "load":
                self.load()
                return False
            elif value == "install":
                self.install()
                return False
            elif value == "install_pack":
                self.install_pack()
                return False
        return True

    def backup(self):
        print("output backup")

    def load(self):
        print("output load")

    def install(self):
        print("output install")

    def install_pack(self):
        print("output install_pack")

    @property
    def work(self):
        arguments = self.arguments()
        if isinstance(arguments, Namespace):
            return arguments.work
        return None

if __name__ == "__main__":
    runner = Runner()
    runner.main()
```

##### Shell
```bash
python main.py -w backup
# output backup
```

## 捐赠

如果小伙伴们觉得这些工具还不错的话，能否请咱喝一杯咖啡呢
<br />
![微信](WeChat.png)
![支付宝](Alipay.png)


## 联系方式

```
微信: yuyangitt
邮箱: 845262968@qq.com
```