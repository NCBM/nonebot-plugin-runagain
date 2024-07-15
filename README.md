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
