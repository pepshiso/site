#deallocate (C++11)
```cpp
void deallocate(pointer p, size_type n);
```

##概要
メモリを解放する。


##戻り値
[`allocator_traits`](/reference/memory/allocator_traits.md)`<OuterAlloc>::`[`deallocate`](/reference/memory/allocator_traits/deallocate.md)`(`[`outer_allocator()`](./outer_allocator.md)`, p, n)`


##例
```cpp
#include <iostream>
#include <vector>
#include <string>

#include <scoped_allocator>

template <class T>
using alloc_t = std::allocator<T>;

// コンテナの要素(Inner)
using string = std::basic_string<
  char,
  std::char_traits<char>,
  alloc_t<char>
>;

// コンテナ(Outer)
template <class T>
using vector = std::vector<
  T,
  std::scoped_allocator_adaptor<alloc_t<T>, alloc_t<typename T::value_type>>
>;

int main()
{
  vector<string>::allocator_type alloc {
    alloc_t<string>(), // vector自体のアロケータオブジェクト
    alloc_t<char>()    // vectorの全ての要素に使用するアロケータオブジェクト
  };

  // 外側のアロケータを使用し、stringが3要素入るメモリを確保
  const std::size_t n = 3;
  string* p = alloc.allocate(n);

  // メモリを解放
  alloc.deallocate(p, n);
}
```

###出力
```
```

##バージョン
###言語
- C++11

###処理系
- [Clang, C++11 mode](/implementation#clang.md): 3.0
- [GCC, C++11 mode](/implementation#gcc.md): 4.7.3
- [ICC](/implementation#icc.md): ??
- [Visual C++](/implementation#visual_cpp.md) ??
