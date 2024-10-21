<div align="center">

# nonebot-plugin-runagain

_✨ 适用于 NoneBot2 实例的停机与重启控制插件 ✨_

<a href="./LICENSE">
    <img src="https://img.shields.io/github/license/NCBM/nonebot-plugin-runagain.svg" alt="license">
</a>
<a href="https://pypi.python.org/pypi/nonebot-plugin-runagain">
    <img src="https://img.shields.io/pypi/v/nonebot-plugin-runagain.svg" alt="pypi">
</a>
<img src="https://img.shields.io/badge/python-3.9+-blue.svg" alt="python">

</div>

## 📖 介绍

允许使用指令控制 Bot 的停机与重启。

## 特性对比

|              特性              |          此项目         | [nonebot-plugin-reboot](https://github.com/18870/nonebot-plugin-reboot) |
| :----------------------------: | :---------------------: | :------------------------------------------------------------------: |
|            平台支持            | Linux, <s>Windows[1]<s> |                            Windows, Linux                            |
|            启动方式            |      nb-cli,`bot.py`    |                                `bot.py`                              |
|  `fastapi_reload`/`--reload`   |         ✅              |                                   ❌                                  |

[1] 由于 Windows 本身限制，重启 Bot 会导致产生新的孤立进程从而无法正常控制，详见[实现原理](#实现原理)。

## 💿 安装

通过 `nb-cli`:

```console
nb plugin install nonebot-plugin-runagain
```

## 📖 用法

- `@` `{COMMAND_START}` `stop|shutdown|停机`

  停止 Bot 运行。

  使用者需要为 Bot 的 SuperUser。

- `@` `{COMMAND_START}` `restart|reboot|重启`

  停止运行并重启 Bot。

  使用者需要为 Bot 的 SuperUser。

## 实现原理

本插件通过反射操作来获得 `uvicorn` 中的管理对象并进行相应控制（针对 `fastapi` 和 `quart` driver），并使用了 `exec` 函数族实现了在 Unix-like 系统下的重启操作。

由于 Windows 下没有对于进程替换的支持，其 `exec` 函数族只能调用 `CreateProcess` 系列函数进行类似操作。此时利用此插件重启会新建一个**孤立**的子进程，导致其无法通过正常方式停止。
