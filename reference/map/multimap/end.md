#end
```cpp
iterator end() noexcept;
const_iterator end() const noexcept;
```

##概要
`multimap` コンテナの最後の要素の次を参照するイテレータを返す。


##戻り値
コンテナの最後の要素の次を参照するイテレータ。 
`iterator` と `const_iterator` はいずれもメンバ型である。`multimap` クラステンプレートにおいて、これらは双方向イテレータである。


##計算量
定数時間


##例
```cpp
#include <iostream>
#include <map>

using namespace std;

int main() 
{
  multimap<int, char> c;
  c.insert( std::make_pair(3,'C'));
  c.insert( std::make_pair(3,'D'));
  c.insert( std::make_pair(7,'G'));
  c.insert( std::make_pair(8,'H'));
  c.insert( std::make_pair(4,'D'));
  c.insert( std::make_pair(5,'E'));
  c.insert( std::make_pair(1,'A'));
  c.insert( std::make_pair(2,'B'));
  c.insert( std::make_pair(6,'F'));

  for( auto i = c.begin(); i != c.end() ; ++i ) {
    cout << i->first << " " << i->second << "\n";
  }

  return 0;
}
```

###出力
```
1 A
2 B
3 C
3 D
4 D
5 E
6 F
7 G
8 H
```

##バージョン
###言語
- C++03

###処理系
- [Clang](/implementation#clang.md): 2.9, 3.0, 3.1, 3.2, 3.3
- [GCC](/implementation#gcc.md): ??
- [GCC, C++11 mode](/implementation#gcc.md): ??
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md): ??


##参照

| 名前 | 説明 |
|------------------------------------------------------------------------------------------------|--------------------------------------------------|
| [`multimap::begin`](/reference/map/multimap/begin.md) | 先頭を指すイテレータを取得する |
| [`multimap::cbegin`](/reference/map/multimap/cbegin.md) | 先頭を指すconstイテレータを取得する |
| [`multimap::cend`](/reference/map/multimap/cend.md) | 末尾を指すconstイテレータを取得する |
| [`multimap::rbegin`](/reference/map/multimap/rbegin.md) | 末尾を指す逆イテレータを取得する |
| [`multimap::rend`](/reference/map/multimap/rend.md) | 先頭を指す逆イテレータを取得する |
| [`multimap::crbegin`](/reference/map/multimap/rbegin.md) | 末尾を指す逆constイテレータを取得する |
| [`multimap::crend`](/reference/map/multimap/rend.md) | 先頭を指す逆constイテレータを取得する |
