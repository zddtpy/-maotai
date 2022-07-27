# -maotai
#黔彩会员小程序小程序授权、加解密及抓包过程，maotai

需要对小程序源码反编译。其登录过程是采用根据appid得到auth_code，然后根据auth_code进行授权。  
登录成功后查询个人信息（information），10点整开始进入商城-查询可预约门店-选择的预约门店的所有商品-选择商品后提交订单。  
其涉及两个秘钥，一个是请求头headers里面有个s和t参数，t是授权后返回的token，s是加密得到的。已破解其加密方式。c#源码，加qq356780493交流。
# 抓包结果  
## 登录  
POST https://crm.zsmart.me/user/account/auth_login HTTP/1.1  
Host: crm.zsmart.me  
Connection: keep-alive  
Content-Length: 128  
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36 MicroMessenger/7.0.9.501 NetType/WIFI MiniProgramEnv/Windows WindowsWechat  
content-type: application/x-www-form-urlencoded  
***s: 273ed508daba9a9864091e27894aa0f5***  
***t: 空***  
Referer: https://servicewechat.com/wx353efcadef581089/55/page-frame.html  
Accept-Encoding: gzip, deflate, br  

请求内容：appid=wx353efcadef581089&auth_code=0014slml2nY1z944wQml2SwZqs04slmD&time_stamp=1658759453&nonce=Y3qAheewL74OngqBnE8wSyhvGlCJGH67  
## 查询个人信息  
POST https://crm.zsmart.me/user/member/infomation HTTP/1.1  
Host: crm.zsmart.me  
Connection: keep-alive  
Content-Length: 69  
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36 MicroMessenger/7.0.9.501 NetType/WIFI MiniProgramEnv/Windows WindowsWechat  
content-type: application/x-www-form-urlencoded  
***s: 加密得到的字符串***  
***t: 授权返回的token***  
Referer: https://servicewechat.com/wx353efcadef581089/55/page-frame.html  
Accept-Encoding: gzip, deflate, br  
请求内容：type=all&time_stamp=1658759453&nonce=bjYKon97WfTh1yMvt4bAIEAD8lT5aDYS
## 抢购  
### 1、先进行query_config  
POST https://qc-crm.zsmart.me/user/qcd_mall/query_config HTTP/1.1  
Host: qc-crm.zsmart.me  
Connection: keep-alive  
Content-Length: 60  
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36 MicroMessenger/7.0.9.501 NetType/WIFI MiniProgramEnv/Windows WindowsWechat  
content-type: application/x-www-form-urlencoded  
***s: 加密得到的字符串***  
***t: 授权返回的token***  
Referer: https://servicewechat.com/wx353efcadef581089/55/page-frame.html  
Accept-Encoding: gzip, deflate, br  

请求内容：time_stamp=1658759473&nonce=uZih3AR6jEJY3dXOn3WOlzxDFfw70jcj  
### 2、查询可预约店铺  
POST https://qc-crm.zsmart.me/user/qcd_mall/available_stores HTTP/1.1  
Host: qc-crm.zsmart.me  
Connection: keep-alive  
Content-Length: 86  
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36 MicroMessenger/7.0.9.501 NetType/WIFI MiniProgramEnv/Windows WindowsWechat  
content-type: application/x-www-form-urlencoded  
***s: 加密得到的字符串***  
***t: 授权返回的token***  
Referer: https://servicewechat.com/wx353efcadef581089/55/page-frame.html  
Accept-Encoding: gzip, deflate, br  

请求内容：lad=30.5702&lod=104.06476&time_stamp=1658759480&nonce=3seeqV91tJXdy51Fe6iDsjGUIZS9HO7a 
其中lad与lod是经纬度  
### 3、查询店铺内商品信息  
### 4、提交订单  
## 最重要的有以下几个参数：s、t、auth_code，只要拿到了这些，就可以愉快的写代码进行自动抢maotai了。  
## 不过这个平台对于抢maotai要求比较高，抢的人少，中签率也是高！！  
# 分享的资源仅供学习交流、参考，任何组织和个人禁止公开传播，禁止商业用途及非法用途，否则一切后果由该组织或个人承担，本人不承担任何法律责任及连带责任！所有下载的资源请在24小时内自行删除，如有侵权，请联系我们删除，谢谢！
