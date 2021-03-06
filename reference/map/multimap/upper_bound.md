#upper_bound
```cpp
iterator upper_bound(const key_type& x);
const_iterator upper_bound(const key_type& x) const;
```

##概要
`x` より大きいキーを持つコンテナ内の最初の要素を指すイテレータを返す（コンテナの比較オブジェクトを使う）。 
[`lower_bound()`](/reference/map/multimap/lower_bound.md) と異なり、このメンバ関数は `x` と等しいときは要素へのイテレータを返さず、それは大きい場合にのみ要素へのイテレータを返す。 
内部的に、`multimap` コンテナ内の全ての要素は常に比較オブジェクトで定義された基準に従って並ぶため、この関数が返す値に続く全ての要素は `x` より大きいことに注意。


##パラメータ
- `x`<br/>
比較されるキー値。 
`key_type` はメンバ型であり、`multimap` コンテナ内でテンプレートパラメータ `Key` の別名して定義される。


##戻り値
コンテナ内の `x` より大きい最初の要素へのイテレータ。 
`iterator` はメンバ型であり、双方向イテレータとして定義される。


##計算量
[`size()`](/reference/map/multimap/size.md) について対数時間。


##例
```cpp
#include <iostream>
#include <map>
using namespace std;

int main()
{
  multimap<int,char> c;

  c.insert(std::make_pair(10,'a'));
  c.insert(std::make_pair(20,'b'));
  c.insert(std::make_pair(30,'c'));

  auto ii = c.upper_bound(20);
  cout << ii->first << "," << ii->second << endl;

  return 0;
}
```

###出力
```
30,c
```

##参照

| | |
|-------------------------------------------------------------------------------------------------|-----------------------------------------------------------------------------------------|
| [`lower_bound`](/reference/map/multimap/lower_bound.md) | 与えられた値よりも小さくない最初の要素へのイテレータを返す |
| [`equal_range`](/reference/map/multimap/equal_range.md) | 指定したキーにマッチする要素範囲を返す |
| [`find`](/reference/map/multimap/find.md) | 指定したキーで要素を探す |
| [`count`](/reference/map/multimap/count.md) | 指定したキーにマッチする要素の数を返す |


