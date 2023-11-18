---
sidebar_position: 3
---

# 快速开始

示例项目git：[logic-sdk-demo](https://gitee.com/codingchangtheworld/logic-sdk-demo)
## 1. 三步在已有项目集成：
### 1.1 添加jar包引用与私服地址
```
<dependency>
    <groupId>com.aims.logic</groupId>
    <artifactId>logic-sdk</artifactId>
    <version>0.0.5-SNAPSHOT</version>
</dependency>
<repositories>
    <repository>
        <id>nexus</id>
        <name>科大智联镜像仓库</name>
        <url>https://nexus.kdznwl.cn/repository/maven-public</url>
    </repository>
</repositories>
```
### 1.2 在入口添加包扫描路径
``` java
@SpringBootApplication(scanBasePackages = {"com.aims.logic", "原项目的包名"})
@SpringBootConfiguration
```
### 1.3 执行脚本添加依赖表
[logic_demo.sql](/file/logic_demo.sql)
- 若项目未使用mybatis-plus，则在application.xml添加mybatis-plus配置
```
spring:
  datasource:
    driver-class-name: com.mysql.cj.jdbc.Driver
    url: jdbc:mysql://localhost:3306/logic_demo?useUnicode=true&characterEncoding=gbk&autoReconnect=true&failOverReadOnly=false
    username: xxx
    password: xxx
```
## 2. 开始使用
### 2.1 启动项目，进入/logic设计
参照[在线体验](/online-demo)进行逻辑设计；
### 2.2 执行逻辑
#### 2.2.1 使用内置webapi
sdk内置运行时服务，通过id定位逻辑。
```
post:/api/runtime/logic/v1/run-api/{id}
post:/api/runtime/logic/v1/run-biz/{id}/{bizId}
post:/api/runtime/logic/v1/biz/{id}/{startCode}/{bizId}
```
实现源码：
```
@PostMapping("/api/runtime/logic/v1/run-api/{id}")
public ApiResult run(@RequestHeader Map<String, String> headers, @RequestBody(required = false) JSONObject body, @PathVariable String id, @RequestParam(value = "debug", required = false, defaultValue = "false") boolean debug) {
    JSONObject customEnv = new JSONObject();
    customEnv.put("HEADERS", headers);
    var rep = runner.run(id, body, customEnv);
    var res = ApiResult.fromLogicRunResult(rep);
    if (debug) {
        res.setDebug(rep.getLogicLog());
    }
    return res;
}
```
#### 2.2.2 自定义集成
```
@Autowired
LogicRunner runner;

@PostMapping("/wms-agg/open/logic/{logicId}")
public LogicRunResult runLogic(@PathVariable String logicId, @RequestBody String body) {
    return runner.run(logicId, body);
}
```

## 3. 相关类型
```
LogicRunResult：返回类型
//返回类型
public class LogicRunResult {
    public LogicRunResult(){
    }
    boolean success=true;
    String msg;
    Object data;
    //执行日志
    LogicLog logicLog;
}
```
