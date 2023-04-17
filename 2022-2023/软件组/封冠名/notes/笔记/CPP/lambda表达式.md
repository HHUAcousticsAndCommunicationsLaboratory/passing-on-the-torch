# lambda表达式构成
![lambda图片](../img/lambda.png)

1.  Lambda 引导
2.  参数列表（可选）
3.  mutable 规范（可选）
4.  异常说明（可选）
5.  返回值类型（可选）
6.  Lambda体

# Lambda引导部分
## 捕获
c++14后，在lambda体中，可以引入新的变量。lambda也可以捕获周围的变量，捕获时可以确定是通过值（相当于const，不能对变量修改），还是引用。

以下是以值/引用捕获变量的例子：
```cpp
[&total, factor]//两个都是引用
[factor, &total]//factor是值，total是引用
[&, factor]//默认都是引用捕获
[=, &total]//默认都是值捕获
```