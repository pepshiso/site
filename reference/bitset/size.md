#size
```cpp
size_t size() const;                    // C++03
constexpr size_t size() const noexcept; // C++11
```

##概要
ビット数を取得する。


##戻り値
テンプレートパラメータ`N`を返す。


##例
```cpp
#include <iostream>
#include <bitset>

int main()
{
  std::bitset<4> bs("1011");

  std::cout << bs.size() << std::endl;
}
```

###出力
```
4
```


##参照

