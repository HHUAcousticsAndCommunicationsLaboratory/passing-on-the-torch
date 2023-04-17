*pimpl idiom*是一种新式 C++ 技术，用于隐藏实现、最小化耦合和分离接口。
# 实现代码
头文件：
```cpp
class class_name{
public:
    ...
private:
    class impl_name;
    unique_ptr<pimpl_name>pimpl_name;
};
```
cpp文件：
```cpp
class class_name::impl_name{
    //这个类中实现功能
};
class_name::class_name() : pimpl(new impl){
    //初始化impl里的数据
}
```

