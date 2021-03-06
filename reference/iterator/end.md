#end(C++11)
```cpp
namespace std {
  template <class C>
  auto end(C& c) -> decltype(c.end());       // (1)

  template <class C>
  auto end(const C& c) -> decltype(c.end()); // (2)

  template <class T, size_t N>
  T* end(T (&array)[N]);                     // (3) C++11

  template <class T, size_t N>
  constexpr T* end(T (&array)[N]) noexcept;  // (3) C++14
}
```

##概要
範囲から、最後尾要素の次を指すイテレータを取得する。


##戻り値
- (1) : `return c.end();`
- (2) : `return c.end();`
- (3) : `return array + N;`


##備考
この関数は、範囲`for`文の実装に使用される。


##例
```cpp
#include <iostream>
#include <vector>
#include <iterator>
#include <algorithm> // for_each

void print(int x)
{
  std::cout << x << " ";
}

int main()
{
  // コンテナ
  {
    std::vector<int> v = {1, 2, 3};

    decltype(v)::iterator first = std::begin(v);
    decltype(v)::iterator last = std::end(v);

    std::for_each(first, last, print);
  }
  std::cout << std::endl;

  // 組み込み配列
  {
    int ar[] = {4, 5, 6};

    int* first = std::begin(ar);
    int* last = std::end(ar);

    std::for_each(first, last, print);
  }
}
```
* end[color ff0000]

###出力
```
1 2 3 
4 5 6 
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): ??
- [GCC](/implementation#gcc.md): 
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.0
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) ??


##参照
- [LWG2280 - begin/end for arrays should be constexpr and noexcept](http://www.open-std.org/jtc1/sc22/wg21/docs/lwg-active.html#2280)

