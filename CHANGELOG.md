# Changelog

## 计划更新

1. 会话管理
    - 对在线用户session管理和基本信息查看;可以手动踢出.
2. 字典管理

## 更新日志

### 2018年2月4日

1. 解决通用mapper替换为Mybatis-Plus遇到的坑
    > 参考: [加入 mybatisplus-spring-boot后，@ConfigurationProperties( prefix = "task.pool" ) 注解报错了](https://gitee.com/baomidou/mybatisplus-spring-boot/issues/IHR21#only_comment)
2. 修复字符串转日期转换器异常

### 2018年2月3日

1. sql文件分类整理
2. 升级spring boot 1.5.4到spring boot 1.5.9
3. 升级thymeleaf 3.0.0到thymeleaf 3.0.9
4. 升级Hutool 2.16.0到Hutool 4.0.4
5. 通用mapper替换为Mybatis-Plus
6. 数据库操作添加乐观锁支持

### 2017年9月24日

1. 解决quartz 触发器是CronTrigger模式时 调用scheduler.rescheduleJob方法后会立即执行任务的问题
2. 解决修改定时任务cron表达式后执行日志没有更新的问题

### 2017年9月7日

1. 解决定时任务里无法通过注解自动注入spring容器中的bean的问题

### 2017年8月20日

1. 权限列表使用treetable展示,增加用户体验

### 2017年8月14日

1. 解决授权时无法只选择列表的BUG
    - zTree取消全部子节点时，父节点不会取消

### 2017年8月12日

1. 重新设计登录页设计，开启炫酷模式
2. 解决字符串自动去除前后空格的BUG

### 2017年8月11日

1.  校验上传文件是否合法
     - 校验文件后缀扩展名是否合法
     - 校验上传文件的头信息，防止非法用户通过更改文件后缀名绕过第一步校验

### 2017年8月9日

1. 解决退出登录时无法清除认证缓存的问题.
    - 由于认证成功存入缓存的是整个对象,shiro提供的退出方法无法清除,还有之前所有的操作都是针对该对象进行的,所以重写了退出过滤器，自己手动去清除认证缓存,这样改动是最小的.

### 2017年8月5日

1. 定义welcome-file-list页面
2. 部署外网演示地址
    - http://139.224.112.51:8082/admin/index 
    - 账号:test  密码:test
3. 配置Nginx访问图片(配置文件见群共享)
4. 修改当前登录密码后，退出登录的逻辑走的是shiro的提供的默认方法，无法清除当前账号登录的次数的相关信息，所以再次登录明明是执行过了退出，确还提醒已经在别的地方登录了
    > 解决办法
    > 1. 执行退出走自定义退出过滤器
    > 2. 后台对shiro的退出做二次封装(未实现)

### 2017年8月1日

1. 重写规划包的目录结构，按模块进行划分
2. 判断如果已经登录了，还访问login登录地址，做重定向到原来的地址

### 2017年7月31日

1. 引入feilong-core 1.10.5包
2. 并发登录人数控制，限制一个账号只能一处登录，踢出前者(自定义KickoutSessionControlFilter和LoginFilter)
    - Ajax请求,前端给出选择框，选择重新登录后执行退出并跳转到登录页面
    - 传统请求，被踢出后跳转到登录页面，弹窗提示
    - 添加登录过滤器，判断登录账号是否已经在其他地方登录，并进行踢出询问，并展示已经登录用户的信息包括IP和登录时间   
3. 自定义退出过滤器，实现清除缓存

### 2017年7月20日

1. 修复BUG
2. 重构角色授权功能和添加角色分离
3. 富文本编辑器更换为UEditor(待完成),去除h-ui中多余的依赖
4. 升级springBoot版本到1.5.4
5. 升级Mybatis到3.4.4,mapper-spring-boot-starter到1.3.0,pagehelper-spring-boot-starter到1.1.2
6. 升级druid-spring-boot-starter到1.1.2 注:V1.1.1不支持connectionPropreties配置，所以无法配置ConfigFilter进行密码加密访问.
7. 重新配置和实现文件上传

### 2017年7月18日

1. 解决修改角色授权时不能立即生效问题，目前只解决了当前用户角色授权时立即生效,对其他用户不能马上生效(之前遗留问题)
2. 去除浏览器地址栏中url中JSESSIONID参数

### 2017年7月14日

1. 解决通用mapper用resultType返回时 无法绑定到对象的问题
2. 排除对二进制文件的过滤,解决字体图标无法显示

### 2017年6月28日

1. 添加SpringBoot jar方式打包时,下载jar包内的文件和响应jar包内文本文件内容的例子

### 2017年6月27日

1. 添加druid-spring-boot-starter
2. 数据库密码加密
3. druid配置细化

### 2017年5月27日

1. 对异常进行细分
    - Service层抛出指定类型的RuntimeException异常
    - Controller层抛出带状态码RumtimeException异常
    - 对异常进行统一转化,并响应到客户端
2. 重构表单重复提交校验(包括:重复提交后的提示和数据校验未通过token的刷新),全部向外抛出异常,进行统一处理
3. 将后端数据校验结果进行客户端页面展示(待处理)

### 2017年5月26日

1. 添加统一异常处理,并进行了细分
2. 添加后端数据校验,支持分组、排序,前后端双层校验,保证数据安全性

### 2017年5月25日

1. 封装layer提示插件,ajax添加遮罩层,增强客户体验度

### 2017年5月24日

1. 后台对Ajax操作的,无权限、登陆超时、表单重复提交等情况响应头信息进行统一配置,前台提示的逻辑重新改造

### 2017年5月23日

1. 添加防止表单重复提交校验前端js+后端token的方式
    - 对Ajax请求,提交时由于验证机制未通过,比如:用户名已存在,返回页面修改后再次提交出现token无法验证通过做处理
    > 解决方案: 利用ajax的全局方法 提交时自动加上token值 判断如果有返回的X-Refresh-Token-Form就更新页面所有的tokenForm值
    - 由于session是存储在服务器内存中的,在集群环境下不能保证生成token的服务器和验证token的服务器就是同一台,所以需要一种机制可以解决多服务器节点的数据共享. 
    > 解决方案: 使用spring session实现session共享或者将token放入redis中
    - 对于多开窗口操作同一个功能 比如: 添加用户，进行限制
    > 采用最后打开的窗口有效的方式,并进行页面过期弹窗友好提示
    - 安全考虑,可以给formToken设置一个有效期
    > 比如后期放入redis,可以方便借助它的生命周期控制;或者在formToken中加入时间戳进行比对.
    - 前端Ajax请求前全局禁用页面submit按钮既可以一定程度防止表单的重复提交，又能大大减轻服务器端访问压力,响应后重新启用按钮.

### 2017年5月22日

1. 新增调度任务查看详情
2. 新增调度日志查看
3. 正在执行，执行完成(待实现)

###  2017年5月4日

1. 动态任务调度
2. 改造权限管理模块
3. 日志UI界面展示

### 2017年4月24日

1. spring boot yml文件多环境配置
2. thymeleaf 布局调整