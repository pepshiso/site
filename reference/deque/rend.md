#rend
```cpp
reverse_iterator rend() noexcept;
const_reverse_iterator rend() const noexcept;
```

##概要

<b>先頭要素の前を指す逆イテレータを取得する。</b>


##戻り値

非`const`な文脈では`reverse_iterator`型で先頭要素の前を指す逆イテレータを返し、
`const`な文脈では`const_reverse_iterator`型で 先頭要素の前を指す逆イテレータを返す。



##例外

投げない


##計算量

定数時間


##例

```cpp
#include <iostream>
#include <deque>

int main()
{
  std::deque<int> d = {1, 2, 3};
  const std::deque<int>& cd = d;

  decltype(d)::reverse_iterator i = d.rbegin();
  decltype(d)::reverse_iterator last = d.rend();

  decltype(d)::const_reverse_iterator ci = cd.rbegin();
  decltype(d)::const_reverse_iterator clast = cd.rend();

  for (; i != last; ++i) {
    std::cout << *i << std::endl;
  }

  for (; ci != clast; ++ci) {
    std::cout << *ci << std::endl;
  }
}
```
* rend[color ff0000]
* rend[color ff0000]

###出力

```cpp
3
2
1
3
2
1
```

##参照


| | |
|--------------------------------------------------------------------------------------------------|--------------------------------------------------------------------------------|
| [`rbegin`](/reference/deque/rbegin.md) | 末尾要素を指す逆イテレータを取得する |
| [`crbegin`](/reference/deque/cbegin.md) | 末尾要素を指す読み取り専用逆イテレータを取得する |
| [`crend`](/reference/deque/crend.md) | 先頭要素の前を指す読み取り専用逆イテレータを取得する |
| [`begin`](/reference/deque/begin.md) | 先頭要素を指すイテレータの取得する |
| [`end`](/reference/deque/end.md) | 末尾要素の次を指すイテレータを取得する |

