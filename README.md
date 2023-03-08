Cloudflare API v4 Dynamic DNS Update in Bash, without unnecessary requests
Now the script also supports v6(AAAA DDNS Recoards)

修改脚本

# API key, see https://www.cloudflare.com/a/account/my-account,
# 上一步获取的CFKEY
CFKEY=
#输入你需要解析用来DDNS解析的根域名 eg: example.com
CFZONE=
# 暂时空着
CFID=
# 登陆CF的Username, eg: user@example.com
CFUSER=
# 填写用来DDNS解析的二级域名，与上面设置的要一致, eg: ddns.yourdomain.com
CFHOST=
# Cloudflare TTL for record, between 120 and 86400 seconds
CFTTL=3600
# Get domain ID from Cloudflare using awk/sed and python json.tool
GETID=true
# Ignore local file, update ip anyway
FORCE=false
# 填写上一步能正确返回咱的当前IP的网址, other examples are: bot.whatismyipaddress.com, https://api.ipify.org/ ...
WANIPSITE="myip.dnsomatic.com"

#运行脚本
chmod +x cf-ddns.sh
./cf-ddns.sh

#第一次运行后，会显示咱用于DDNS解析的二级域名的CFID，记录下来将CFID填入到配置文件中的CFID处
#再次运行
./cf-ddns.sh

#设置自动运行
crontab -e
#不知道这样写对不对xD
0 * * * * /root/cf-ddns.sh >/dev/null 2>&1
 
