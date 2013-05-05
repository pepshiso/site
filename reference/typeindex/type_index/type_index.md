#コンストラクタ
```cpp
type_index(const type_info& rhs) noexcept;
```

##type_indexの構築

- `type_index(const type_info& rhs) noexcept`type_infoからの構築


##例外

投げない


##例

```cpp
#include <cassert>
#include <typeindex>

int main()
{
  std::type_index ti = typeid(int);
  assert(ti == typeid(int));
}
```

###出力

```cpp
```

##バージョン
```
###言語


- C++11



###処理系

- [GCC, C++0x mode](/implementation#gcc.md): 4.6.1
