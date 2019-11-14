#实体生成策略  -> Mybatis-plus生成、可用参考test包中的WxTenthousandNoApplicationTests类方法

#框架  springboot + shiro + mybatis +mybatis-plus + thymeleaf + bootstrap

#包结构划分
com.wanhao.core
                                         - controller
                                         - service 
                                                     - dao(对应mapper中的sql方法)
                 - system 后台管理端                 -  dto(自定义实体-后台传给前台 以Dto结尾)
                                         - presist   - entity(表对应实体)
wx-slash-young                                       - exception(异常信息)
                                                     - model(自定义实体-前台传给后台 以Model结尾)              
                 - mentor     师傅端 (主要针对接口调用，不存在表对应实体)    
                 - user       用户端 (主要针对接口调用,不存在表对应实体)    
                 - common 定义公用的一些工具包
                 - designmode 定义一些常用设计模式
                 - config shiro所需的配置和其它配置文件
                 - constant 放置一些枚举相关的变量值
                 - exception 放置一些全局的异常
                 - filter 登录过滤器

后台管理系统中，添加用户信息的时候要使用到“盐值”来进行加密比对，所以，存入用户密码的时候也需要加盐

#Thymeleaf引入资源格式规范
首先是以.html结尾的文件中，必须要使用
  <html lang="en"  xmlns:th="http://www.thymeleaf.org">替换<html>标签
然后就是资源引入(一下二种样式都写的目的是为了让前端再使用其它前端开发工具只想引入页面的情况下也不会出现资源文件加载不到
也不会让后台再启动服务后加载不到资源未见，一举二得。)
 css样式引入
  <link href="/bootstrap3.3.5/css/bootstrap.min.css" th:href="@{/bootstrap3.3.5/css/bootstrap.min.css}" rel="stylesheet">
 js文件引入
  <script src="/js/ie8-responsive-file-warning.js" th:src="@{/js/ie8-responsive-file-warning.js}"></script>


#前台分页的二种方式
参考decorationUserMain.html和sysUserMain.html



#后台获取用户信息的方法
SysUserEntity userEntity = (SysUserEntity) SecurityUtils.getSubject().getSession().getAttribute("userModel");
#后台获取登录信息的方法
IpUtil.getRemoteIp(RequestHolder.getCurrentRequest())
#前台获取用户信息的方法
[[${session.userModel.属性名}]]   这里的属性名和model对象中的属性要一一对应
#页面刷新的方式
ctrl+F9 (刷新之后，浏览器才可以访问到最新的内容)

                 
                 
                  