## API
#### getip
获取公网出口IP，无需参数
#### gettime
获取服务器时间戳，用于编码认证信息，无需参数，有调用频率限制
#### getuserinfo
获取用户信息，参数为token=用户登陆时返回的token
#### getdomaininfo
获取指定域名信息，参数为token=用户登陆时返回的token&domian=sample.com
#### getauthcode
仅获取指定域名信息中的auth_code字段，参数同getdomaininfo
#### getdomainlist
获取用户所拥有的所有域名，参数为token=用户登陆时返回的token
#### update
向服务器提交指定域名所指向的ip，通过get参数version区分不同的方式
#####（1）version=safe
`http://yourdomain.com/api/update?version=safe`
post参数为auth=时间认证码；ip=当前公网出口IP  ；domain=域名  
时间认证码可通过getauthcode方式获取auth_code并根据时间戳计算取得
返回值：(string)'success'|(json)error_info
#####（2）version=username
`http://yourdomain.com/api/update?version=username&domain=域名&ip=公网ip&username=用户名&password=密码`
其他get参数：domain=__HOSTNAME__&ip=__MYIP__&user=__USERNAME__&password=__PASSWORD__
返回值：(string)'success'|(json)error_info
（该方法有泄露用户名密码风险，慎用）
#####（3）version=authcode
`http://yourdomain.com/api/update?version=authcode&auth=auth_code&domain=域名&ip=公网ip`
其他get参数：auth=auth_code; domain=域名；ip=公网ip
返回值：(string)'success'|(json)error_info
（该方法有泄露当前域名认证信息的风险）

#### auth
向服务器post方式提交用户名/密码  
参数为user=xxx;password=xxx
返回值：(string)'err'|token_code
#### keepalive
向服务器发送心跳包，post方式，参数为token=用户token  

## 其他说明
#### auth_code 生成
MD5（'auth' + time + rand(10000,99999))
#### 时间认证码计算方法
时间认证码计算方法如下：
1. 客户端启动时，从服务器获取服务器的时间戳，与本地时间做差并记录该时间偏移量
2. 计算服务器时间time=本地时间+时间偏移量
3. 计算认证信息：auth = md5((int)time/30 + (string)auth_code)
4. 向服务器post信息，包括以下字段：auth,domain,ip；服务器端将（最多）检查提交时间前/后1个时间片的auth值
5. 根据返回值重复第2~4步或返回错误信息

