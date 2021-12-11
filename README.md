# 用于CloudFlare的DDNS动态域名

## 使用方法
### 测试是否支持
```shell
运行curl（必需）
curl
运行wget（必需）
wget
运行nslookup（不必需）
nslookup baidu.com
```
### 使用步骤
#### SET 1
前往https://dash.cloudflare.com/profile/api-tokens
获取 Global API Key
#### SET 2
前往https://dash.cloudflare.com/
获取 需要解析的dns域名（需要提前使用cloudflare接管域名
#### SET 3
```shell
（如果你会用 wget 和 vi） 直接ssh链接服务器然后wget用vi修改）
````

下载并编辑 https://github.com/n0raml/cloudflare-ddns-v4v6/blob/main/api-ddns.sh
```shell
邮箱
email="qq@email.com"

获取的Global API Key
GAK="11231232132413241325qwdqer1312312345e"

做 DDNS 的根域名
zone_name="ym.com" 

更新的二级域名，如果想不用，直接填写根域名
record_name="www.ym.com"

域名类型，IPv4 为 A，IPv6 则是 AAAA
record_type="A"

是否代理dns解析 cdn加速。否：false 是：true。  dns页面的小云朵
proxy="false"
```
#### SET 4
编辑并保存，使用SCP或者 winscp传输至路由器任意目录，你记得就好。
列
```shell
    文件目录           用户@ip:/目录
scp api-ddns.sh root@192.168.1.1:/root
```
#### SET 5
SSH链接之后执行（赋予权限并执行
```shell
chmod +x /root/ddns.sh
sh /root/ddns.sh
```


# cron定时任务条件
```shell
#秒 每小时 天 周 月 
0 */1 * * * sh /home/root/api-ddns.sh
```



# 更新log
```shell
2021-12-11
测试：正常运行
新增：PUSHplus推送: http://www.pushplus.plus/      pushplus处添加一对一推送token或者一对多推送token
```

```shell
2021-11-27
优化返回结果，修复ipv4API
建议使用API版本
```

```shell
2021-11-24
更新ipv4 api
```
