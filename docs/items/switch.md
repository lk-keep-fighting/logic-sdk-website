---
sidebar_position: 3
---

# switch

:::tip

分支条件判断节点，类似代码中的switch

:::

## 配置说明

### 条件表达式
可根据上下文的局部变量(_var)、入参变量(_par)组成js表达式，也可以直接是变量，分支的case条件将会根据这里的值匹配，case值都未命中则走default分支。
- 示例：通过入参中的a变量判断分支
```js

_par.a

```