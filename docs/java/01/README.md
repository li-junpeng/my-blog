# SpringBoot 无法访问子模块的Controller

最近在搭建DB兔的后端，发现配置了maven模块后，访问子模块的Controller是404，然后我各种检查maven依赖没有发现哪里配置的不对啊，突然就想到SpringBoot启动时，默认扫描当前启动类所在的包以及子包下的所有Bean，如果想要扫描不同包下的bean，需要配置`@ComponentScan`注解来指定需要扫描的包名，然后我就找到启动类，发现启动类竟然在`com.dbtu.server.starter`包下，我的子模块包名是`com.dbtu.server.api`，这肯定是扫描不到的嘛，然后我把启动类放到了上一级目录，也就是`com.dbtu.server`目录下，重新启动，Controller访问200，成功了！！！