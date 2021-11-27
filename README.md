# 用于CloudFlare的DDNS动态域名

## 使用方法

需要支持Curl

下载脚本至路由器，并赋予权限

```shell
chmod +x /脚本路径
```

```she
sh ddns.sh
```

运行检查

cron定时任务条件
```shell
#秒 每小时 天 周 月 
0 */1 * * *
```

# 更新changerlog
```shell
2021-11-27
优化返回结果，修复ipv4API
建议使用API版本
```

```shell
2021-11-24
更新ipv4 api
```
