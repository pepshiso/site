#hardware_concurrency
```cpp
static unsigned int hardware_concurrency() noexcept;
```

##概要

処理系によりサポートされるスレッド並行数を取得する。

##戻り値

サポートされるスレッド並行数。その処理系において値を取得できない場合は0を返す。



##例外

送出しない。


##備考

戻り値はヒントとしてのみ利用すべきである。（値0が取得される場合がある。）


##例

```cpp
#include <iostream>#include <thread>int main(){  std::cout << "concurrency=" << std::thread::hardware_concurrency() << std::endl;  return 0;}
```

###出力

```cpp
concurrency=4
```

##バージョン


###言語


- C++11



###処理系

- [Clang](/implementation#clang.md):
- [GCC](/implementation#gcc.md):
- [GCC, C++0x mode](/implementation#gcc.md): 4.6.3, 4.7.0
- [ICC](/implementation#icc.md):
- [Visual C++](/implementation#visual_cpp.md):<h4>備考</h4>
(処理系やライブラリのバグや不完全な実装などをここに書く。なければ備考欄を削除)



##実装例

```cpp
```

##参照
```