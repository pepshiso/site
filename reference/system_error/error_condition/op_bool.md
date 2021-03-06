#explicit operator bool(C++11)
```cpp
explicit operator bool() const noexcept;
```

##概要
`error_condition`オブジェクトがエラー状態であるかを判定する。`error_condition`クラスのデフォルトエラー値である`0`が正常と見なされる。`true`の場合はエラーであることを意味し、`false`の場合は正常を意味する。


##戻り値
[`value()`](./value.md)` != 0`


##例外
投げない


##例
```cpp
#include <iostream>
#include <system_error>
#include <string>

void print(const std::error_condition& ec)
{
  if (ec) {
    std::cout << "error! : " << ec.message() << std::endl;
  }
  else {
    std::cout << "success" << std::endl;
  }
}

int main()
{
  std::error_condition err1;
  print(err1);

  std::error_condition err2(static_cast<int>(std::errc::invalid_argument),
                            std::generic_category());
  print(err2);
}
```
* if (ec)[color ff0000]

###出力
```
success
error! : Invalid argument
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.0
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) 10.0


##参照
