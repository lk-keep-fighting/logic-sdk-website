---
sidebar_position: 2
---

# 在线体验

## 1. 新建
- 打开[演示环境](http://101.34.115.220:4052/)
- 点击逻辑编排-[新建]，输入唯一标识ID等，确人；
- 列表第一项为刚添加的编排，点击[设计]打开设计界面；
<img src="/img/capture/新建编排.png" height='400'/>
## 2. 在线设计
### 2.1 布局介绍
- 左侧为可用节点，选中可拖拽到中间画布；
- 右侧为节点属性配置，双击节点可打开，保存配置需点下方提交按钮；
- 上方工具栏
  - 保存：用于整个配置的生成并保存到服务器；
  - 配置参数：可配置逻辑入参、局部变量和依赖的环境变量（环境变量在运行时env.dev.json中配置）
  - 调试：可输入入参、环境变量运行逻辑获取返回值；
  - 当前版本：根据时间在每次保存时生成的版本号，用于版本控制；
### 2.2 设计与配置
- 左侧选择js脚本节点拖入右侧；
- 双击节点右侧弹出属性配置框；
- 输入`return 1;`点击提交保存；
<img src="/img/capture/design-online.png" height='400'/>
## 3. 在线调试
- 选择上方调试按钮，点击确定；
- 返回的data为1，即刚才配置的js脚本返回。
<img src="/img/capture/debug-online.png" height='400'/>
## 4. 内置API调用
- 逻辑服务有标准的API前缀，通过id定位执行的逻辑。
```
post:/api/runtime/logic/v1/run-api/{id}
post:/api/runtime/logic/v1/run-biz/{id}/{bizId}
```
- 运行实例回放
<img src="/img/capture/实例回放.png" height='400'/>
