# 跨域SSO
## Usage：
修改本地hosts文件，随意映射3个域名，例如：  
127.0.0.1 web1.com  
127.0.0.1 web2.com  
127.0.0.1 localhost  
  
prot:8080  
  
[http://web1.com:8080/WebSSODemo/index.jsp](http://web1.com:8080/WebSSODemo/index.jsp)  
[http://web2.com:8080/WebSSODemo/index.jsp](http://web1.com:8080/WebSSODemo/index.jsp)  
  
若第二次直接登录成功，则实现跨域登录  

## 登录原理
**方式：给每个应用系统cookie's url设置该用户认证系统的ticket**  
![sso流程](https://github.com/BreadKid/SSO/blob/master/pic/SSO.png?raw=true)  

* 用户在浏览器输入信息，登录指定应用系统
* 到认证系统登录验证  
  
      auth_ticket check(info){
		if(true){
			return auth_ticket;
		}else{
			login(info){
				if(true){
					return auth_ticket;
				}else{
					//sth else
				}
			}
		}
	  }

* 成功后返回浏览器 *认证 ticket*
* 浏览器再返给指定应用系统 *认证 ticket* set cookie's url (方式不安全)
* 指定应用系统返给浏览器 *该应用系统 ticket*
* 重定向页面





参考:  
[跨域单点登录](http://blog.csdn.net/ghsau/article/details/20545513)  [ticket验证过程](http://blog.csdn.net/ghsau/article/details/20466351)