#atomic_compare_exchange_weak_explicit(C++11)
```cpp
namespace std {
  template<class T>
  bool atomic_compare_exchange_weak_explicit(
         shared_ptr<T>* p, shared_ptr<T>* expected, shared_ptr<T> desired,
         memory_order success, memory_order failure);
}
```
* memory_order[link /reference/atomic/memory_order.md]

##概要
メモリオーダーを指定して、弱い比較で、アトミックに`shared_ptr`オブジェクトを入れ替える。


##要件
`p != nullptr`であること。

`failure`が[`memory_order_release`](./memory_order.md), [`memory_order_acq_rel`](./memory_order.md)ではないこと。

`failure`が`success`よりも強くないこと。


##効果
現在の値`p`と`expected`が等しければ、`*p`を`desired`で置き換え、そうでなければ`*p`を`*expected`で置き換える。

等しい場合は`success`メモリオーダー、そうでなければ`failure`メモリオーダーに従って、アトミックに値の置き換えが行われる。



##戻り値
`*p`と`*expected`が等しければ`true`、そうでなければ`false`を返す。


##例外
投げない


##備考
等値比較は、2つの`shared_ptr`オブジェクトが同じポインタを保持し、リソースを共有していれば`true`となる。


##例
```cpp
#include <iostream>
#include <memory>

int main()
{
  std::shared_ptr<int> p(new int(1));

  std::shared_ptr<int> ps = p;
  std::shared_ptr<int> q(new int(3));
  while (!std::atomic_compare_exchange_weak_explicit(
          &p, &ps, q,
          std::memory_order_acq_rel,
          std::memory_order_relaxed)) {}

  std::shared_ptr<int> result = std::atomic_load(&p);
  std::cout << *result << std::endl;
}
```
* atomic_compare_exchange_weak_explicit[color ff0000]


###出力
```
3
```


##バージョン
###言語
- C++11

###処理系
- [Clang, C++11 mode](/implementation#clang.md): 3.3
- [GCC, C++11 mode](/implementation#gcc.md): (4.8.2時点で未実装)
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) ??


##参照
- [`atomic_compare_exchange_weak() - shared_ptr`](./atomic_compare_exchange_weak.md)
- [`atomic_compare_exchange_weak_explicit() - <atomic>`](/reference/atomic/atomic_compare_exchange_weak_explicit.md)
- [`atomic_compare_exchange_strong_explicit() - <atomic>`](/reference/atomic/atomic_compare_exchange_strong_explicit.md)
- [N2674 Shared_ptr atomic access, revision 1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2674.htm)
- [C++0x Shared_ptr atomic access - Faith and Brave - C++で遊ぼう](http://faithandbrave.hateblo.jp/entry/20081015/1224066366)


