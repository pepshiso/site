#make_error_code (C++11)
```cpp
namespace std {
  error_code make_error_code(io_errc e) noexcept;
}
```
* error_code[link /reference/system_error/error_code.md]
* io_errc[link ./io_errc.md]

##概要
`io_errc`から`error_code`を生成する


##戻り値
[`error_code`](/reference/system_error/error_code.md)`(static_cast<int>(e), `[`iostream_category`](./iostream_category.md)`())`


##例外
投げない


##例
```cpp
#include <iostream> // 自動的に<ios>もインクルードされる
#include <string>

int main()
{
  std::error_code ec = std::make_error_code(std::io_errc::stream);

  std::cout << "category : " << ec.category().name() << std::endl;
  std::cout << "value : " << ec.value() << std::endl;
  std::cout << "message : " << ec.message() << std::endl;
}
```
* make_error_code[color ff0000]

###出力例
```
category : iostream
value : 1
message : iostream stream error
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md):
- [GCC, C++0x mode](/implementation#gcc.md): ??
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md): 10.0, 11.0


##参照


