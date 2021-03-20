# EUserv_extend
A simple Python Script which can help you renew your free EUserv IPv6 VPS.

This Script can check the VPS amount in your account automatically and renew the VPS if it can be renewed.

This repo **do not** provide you any tutorials that help you run it on GitHub Action or others like Serverless / Cloud Function.

All in this repo is for learning only.

If you have any disputes about this repo, please contact me or send an Issue.



## How to Use

1、Install Python3 and dependences

```bash
#Install Python3
apt install python3 python3-pip -y
#Intstall dependences
pip install requests beautifulsoup4
```

2、Replace the USERNAME & PASSWORD parms with yours in `main.py` Line 7-8.

Your can add multiple accounts with single space separated.

## 说明

因各种原因，本仓库不提供任何定时运行脚本，本脚本可以在本地运行，如果想要自己配置到云函数平台上可自行配置。劝各位耗子尾汁，**请不要Fork这个仓库然后提供GitHub Workflow再分发，也不要提供任何单仓库Workflow并分发，特别是定时执行确定的那种。谢谢。**

若部署在云函数平台上导致的任何出错，不接受反馈。

(可选)使用sre24.com提供的服务，续期结果通过sre24免费推送微信提醒。（社区提供，未经测试，如有BUG请反馈，请自行确保使用第三方服务的安全性及可靠性），需要的TOKEN在第9行设置。
