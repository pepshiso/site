#p(C++11)
```cpp
double p() const;
```

##概要
確率`p`を取得する。


##戻り値
構築時に設定された、`true`を生成する確率`p`を返す。


##例
```cpp
#include <iostream>
#include <random>

int main()
{
  std::bernoulli_distribution dist(0.3);

  double p = dist.p();
  std::cout << p << std::endl;
}
```

###出力
```
0.3
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


