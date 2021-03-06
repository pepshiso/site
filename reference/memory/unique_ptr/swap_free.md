#swap(フリー関数版)(C++11)
```cpp
namespace std {
  template <class T, class D>
  void swap(unique_ptr<T, D>& a, unique_ptr<T, D>& b) noexcept;
}
```

##概要
2つの`unique_ptr`オブジェクトを入れ替える。


##効果
`a.`[`swap`](./swap.md)`(b);`


##戻り値
なし


##例
```cpp
#include <iostream>
#include <memory>

int main()
{
  std::unique_ptr<int> a(new int(3));
  std::unique_ptr<int> b(new int(1));

  // aとbを入れ替える
  std::swap(a, b);

  std::cout << *a << std::endl;
  std::cout << *b << std::endl;
}
```

###出力
```
1
3
```

##バージョン
###言語
- C++11

###処理系
- [GCC](/implementation#gcc.md): 4.4.7
- [Clang libc++, C++11 mode](/implementation#clang.md): 3.0
- [ICC](/implementation#icc.md): ?
- [Visual C++](/implementation#visual_cpp.md): ?
