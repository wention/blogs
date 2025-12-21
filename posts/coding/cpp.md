CPP 开发
========

## CPP 参数包展开

### 1. 递归函数展开

```cpp
#include <iostream>

// 递归终止条件
void print() {
    std::cout << "End of recursion" << std::endl;
}

// 递归展开
template<typename T, typename... Args>
void print(T first, Args... rest) {
    std::cout << first << std::endl;
    print(rest...); // 递归展开参数包
}

int main() {
    print(1, 2.5, "hello", 'A');
    return 0;
}
```

### 2. 逗号表达式展开

```cpp
#include <iostream>

template<typename... Args>
void print(Args... args) {
    // 利用初始化列表展开参数包
    int arr[] = { (std::cout << args << std::endl, 0)... };
    (void)arr; // 防止未使用警告
}

int main() {
    print(1, 2.5, "hello", 'A');
    return 0;
}

```

#### 和 lambda 结合展开

```cpp
#include <iostream>

template<typename... Args>
void print(Args... args) {
    auto f = [](auto x){ std::cout << x << std::endl; };
    int dummy[] = { (f(args), 0)... };
    (void)dummy;
}

int main() {
    print(1, 2.5, "hello", 'A');
    return 0;
}

```

> 特点：
> 于对每个参数执行更复杂的操作
> 可读性更强

### 3. C++17 折叠表达式

```cpp
template<typename... Args>
void print(Args... args) {
    ((std::cout << args << std::endl), ...);
}
```