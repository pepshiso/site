#operator==(C++11)
```cpp
namespace std {
  template<class T, class U>
  bool operator==(const shared_ptr<T>& a, const shared_ptr<U>& b) noexcept; // (1)

  template <class T>
  bool operator==(const shared_ptr<T>& x, nullptr_t) noexcept;              // (2)

  template <class T>
  bool operator==(nullptr_t, const shared_ptr<T>& x) noexcept;              // (3)
}
```
* nullptr_t[link /reference/cstddef/nullptr_t.md]

##概要
等値比較。


##戻り値
- (1) : `a.`[`get()`](./get.md) `==` `b.`[`get()`](./get.md)
- (2), (3) : `!x`


##例
```cpp
#include <iostream>
#include <memory>

int main()
{
  std::shared_ptr<int> p1(new int(3));
  std::shared_ptr<int> p2 = p1;
  if (p1 == p2) {
    std::cout << "equal" << std::endl;
  }

  std::shared_ptr<int> p3;
  if (p3 == nullptr) {
    std::cout << "p3 is nullptr" << std::endl;
  }

  if (nullptr == p3) {
    std::cout << "p3 is nullptr" << std::endl;
  }
}
```

###出力
```
equal
p3 is nullptr
p3 is nullptr
```

##バージョン
###言語
- C++11

###処理系
- [GCC](/implementation#gcc.md): 4.3.6 (`nullptr`バージョン以外), 4.6.4
- [Clang libc++, C++11 mode](/implementation#clang.md): 3.0 (`nullptr`バージョン以外), 3.3
- [ICC](/implementation#icc.md): ?
- [Visual C++](/implementation#visual_cpp.md): ?
