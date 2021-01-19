# EUserv_extend
使用Github Action自动续期EUserv免费IPv6 VPS脚本

## 说明

自动获取账号内所有的VPS项目，并检测是否需要续期，需要续期会自动续期。

(可选)续期结果通过sre24免费推送微信提醒。

请详细浏览下面的使用说明。

## 使用说明

~~1、Star本项目~~

1、Fork 本仓库，然后点击你的仓库右上角的 Settings，找到 Secrets 这一项，添加两个秘密环境变量`USERNAME`和`PASSWORD`。支持同时添加多个帐户，数据之间用单个空格 ` ` 隔开即可，帐户名和帐户密码需一一对应。**之前是用半角逗号分割的，更换成空格后，更新脚本后记得修改原变量的值**

```
USERNAME: 你的EUserv账户邮箱或Customer ID 第二个账户
PASSWORD: 第一个账户密码 第二个账户密码
TOKEN: (可选)微信扫码免费登录 https://sre24.com 在「设置」页面复制值
```

2、设置好环境变量后点击你的仓库上方的 Actions 选项，点击 `I understand...` 按钮确认在 Fork 的仓库上启用 GitHub Actions 。

3、最后在你这个 Fork 的仓库内修改一下```.github/workflows/action.yml ```文件（这个本项目的Workflow的配置文件）。请见这一段落：

```
schedule:
  - cron: '50 1 * * 0,3'
```

这一Cron表达式规定了本脚本的执行时间，即默认每周日、每周三1:50 UTC执行脚本。请修改这一文件否则脚本可能无法正常工作。

如果你在Github上编辑此文件，Github会为你提供即时的注释，即类似“Runs at 01:50 UTC on Sun and Wed”，请根据这一注释自行设置脚本执行时间。

如果你的账号下只有一台VPS，建议选在这一VPS需要续期的附近时间，并设置每月执行一次以减少资源的过度浪费。

修改之后，请打开Actions 选项，查看脚本是否正常工作。

**（重要！！！请不要向本仓库提交无关的PR，请在你自己Fork的仓库上提交。测试发现在 Fork 的仓库上 GitHub Actions 的定时任务不会自动执行，必须要手动触发一次后才能正常工作）** 。

4、仓库内包含的 GitHub Actions 配置文件会在你设置的时间。自动执行检查账号的脚本文件，如果检查到有需要续期的VPS，会自动续期，你也可以通过 `Push` 操作手动触发执行。

**注意：** 为了实现某个帐户访问出错时不中断程序继续尝试下一个，除非特殊情况（如账号密码对应个数不对等），GitHub Actions 的状态可能将永远是“通过”（显示绿色的✔），请自行检查 GitHub Actions 日志 `Auto renew` 项的输出确定程序执行情况。

## 其他说明

1、若使用Github Actions运行本脚本，将会公开你的账号中VPS个数以及VPS的ID（**Contract**）

~~2、由于Github Workflow的限制，你可能需要每两个月重新启动一下，方法是随便改下本README.md~~（本项目目前每月会自动向仓库提交commit，Workflow应该不会被自动暂停了）

## 参考（及本文档）

hostloc-auto-get-points: https://github.com/inkuang/hostloc-auto-get-points  MIT License