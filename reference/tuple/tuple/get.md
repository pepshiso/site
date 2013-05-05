#get
```cpp
namespace std {
  template <size_t I, class... Types>
  typename tuple_element<I, tuple<Types...> >::type& get(tuple<Types...>& t) noexcept;

  template <size_t I, class... types>
  typename tuple_element<I, tuple<Types...> >::type&& get(tuple<Types...>&& t) noexcept;

  template <size_t I, class... Types>
  typename tuple_element<I, tuple<Types...> >::type const& get(const tuple<Types...>& t) noexcept;
}
```
* tuple_element[link /reference/tuple/tuple_element.md]
* tuple[link /reference/tuple/tuple.md]

##概要

<b>tupleオブジェクトから指定した位置の要素を取得する。</b>


##要件

テンプレートパラメータ`I`が`tuple`の要素数よりも小さいこと。
この要件を満たさない場合はコンパイルエラーとなる。


##戻り値

`tuple`オブジェクトの`I`番目の要素への参照


##例外

投げない


##例

```cpp
#include <iostream>
#include <tuple>
#include <string>

int main()
{
  std::tuple<int, char, std::string> t(1, 'a', "hello");

  int& i = std::get<0>(t);
  char& c = std::get<1>(t);
  std::string& s = std::get<2>(t);

  std::cout << i << std::endl;
  std::cout << c << std::endl;
  std::cout << s << std::endl;
}
```
* get[color ff0000]
* get[color ff0000]
* get[color ff0000]

###出力

```cpp
1
a
hello
```

##バージョン


###言語


- C++11



###処理系

- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 4.6.1
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) ??<h4>備考</h4>
(処理系やライブラリのバグや不完全な実装などをここに書く。なければ備考欄を削除)



##実装例

```cpp
```

##参照
```