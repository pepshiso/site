#operator->(C++11)
```cpp
T* operator->() const noexcept;
```

##概要
ポインタを通してオブジェクトにアクセスする。


##要件

```cpp
get() != nullptr
```
* get()[link ./get.md]


##戻り値
[`get()`](./get.md)


##例
```cpp
#include <iostream>
#include <memory>
#include <string>

int main()
{
  std::shared_ptr<std::string> p(new std::string("hello"));

  std::cout << p->c_str() << std::endl;
}
```

###出力
```
hello
```

##バージョン
###言語
- C++11

###処理系
- [GCC](/implementation#gcc.md): 4.3.6
- [Clang libc++, C++11 mode](/implementation#clang.md): 3.0
- [ICC](/implementation#icc.md): ?
- [Visual C++](/implementation#visual_cpp.md): ?
