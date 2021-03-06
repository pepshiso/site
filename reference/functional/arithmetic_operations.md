#算術演算関数オブジェクト
```cpp
namespace std {
  template <typename T>
  struct plus {
    T operator ()(const T &x, const T &y) const;
    typedef T first_argument_type, second_argument_type, result_type;
  };

  template <typename T>
  struct minus {
    T operator ()(const T &x, const T &y) const;
    typedef T first_argument_type, second_argument_type, result_type;
  };

  template <typename T>
  struct multiplies {
    T operator ()(const T &x, const T &y) const;
    typedef T first_argument_type, second_argument_type, result_type;
  };

  template <typename T>
  struct divides {
    T operator ()(const T &x, const T &y) const;
    typedef T first_argument_type, second_argument_type, result_type;
  };

  template <typename T>
  struct modulus {
    T operator ()(const T &x, const T &y) const;
    typedef T first_argument_type, second_argument_type, result_type;
  };

  template <typename T>
  struct negate {
    T operator ()(const T &x) const;
    typedef T argument_type, result_type;
  };
}
```

##概要
算術演算を提供する関数オブジェクト群。これらは一切のメンバ変数を持たず、状態を保持しない。


###メンバ関数

| | |
|----------------------------------------|--------------------------------|
| `plus<T>::operator()` | `x + y` と等価 |
| `minus<T>::operator()` | `x - y` と等価 |
| `multiplies<T>::operator()` | `x * y` と等価 |
| `divides<T>::operator()` | `x / y` と等価 |
| `modulus<T>::operator()` | `x % y` と等価  |
| `negate<T>::operator()` | `-x` と等価  |

###メンバ型

| | |
|-------------------------------------------------|-------------------------|
| `first_argument_type, argument_type` | `T`と等価 |
| `second_argument_type` | `T`と等価 |
| `result_type` | `T`と等価 |

###例
```cpp
#include <iostream>
#include <functional>

int main()
{
  std::cout << std::plus<int>()(3, 5) << std::endl;
}
```

###出力
```
8
```

