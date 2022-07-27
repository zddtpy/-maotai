# -maotai
#黔彩会员小程序小程序授权、加解密及抓包过程，maotai

需要对小程序源码反编译。其登录过程是采用根据appid得到auth_code，然后根据auth_code进行授权。  
登录成功后查询个人信息（information），10点整开始进入商城-查询可预约门店-选择的预约门店的所有商品-选择商品后提交订单。  
其涉及两个秘钥，一个是请求头headers里面有个s和t参数，t是授权后返回的token，s是加密得到的。已破解其加密方式。c#源码，加qq356780493交流。
#抓包结果  
##登录  
POST https://crm.zsmart.me/user/account/auth_login HTTP/1.1  
Host: crm.zsmart.me  
Connection: keep-alive  
Content-Length: 128  
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/53.0.2785.143 Safari/537.36 MicroMessenger/7.0.9.501 NetType/WIFI MiniProgramEnv/Windows WindowsWechat  
content-type: application/x-www-form-urlencoded  
**s: 273ed508daba9a9864091e27894aa0f5**  
**t: 603e8b9c8f587735**  
Referer: https://servicewechat.com/wx353efcadef581089/55/page-frame.html  
Accept-Encoding: gzip, deflate, br  

响应：appid=wx353efcadef581089&auth_code=0014slml2nY1z944wQml2SwZqs04slmD&time_stamp=1658759453&nonce=Y3qAheewL74OngqBnE8wSyhvGlCJGH67  
