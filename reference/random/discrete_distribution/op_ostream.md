#operator<<(C++11)
```cpp
namespace std {
  template <class CharT, class Traits, class IntType>
  basic_ostream<CharT, Traits>& operator<<(
    basic_ostream<CharT, Traits>& os
    const discrete_distribution<IntType>& x);
}
```
* basic_ostream[link /reference/iostream/basic_ostream.md]

##概要
ストリームへの出力を行う。


##効果
`os`に対して、分布オブジェクト`x`の現在状態を出力する。


##事後条件
`os`のフォーマットフラグが、この関数を呼び出す前の状態に戻ること。


##戻り値
`os`


##例
```cpp
#include <iostream>
#include <random>

int main()
{
  std::discrete_distribution<> dist = {0.1, 0.2, 0.3};
  std::cout << dist << std::endl;
}
```

###出力例
```
3 1.66666666666666657e-01 3.33333333333333315e-01 4.99999999999999889e-01
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.2
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) ??


##参照

