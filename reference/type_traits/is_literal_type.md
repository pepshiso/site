#is_literal_type(C++11)
```cpp
namespace std {
  template <class T>
  struct is_literal_type;
}
```

##概要
型`T`がリテラル型か調べる。


##要件
型`T`は完全型であるか、`const`/`volatile`修飾された(あるいはされていない)`void`か、要素数不明の配列型でなければならない。


##効果
`is_literal_type`は、型`T`がリテラル型であるならば[`true_type`](./integral_constant-true_type-false_type.md)から派生し、そうでなければ[`false_type`](./integral_constant-true_type-false_type.md)から派生する。

リテラル型とは、以下のいずれかの条件を満たす型である：

- [スカラ型](./is_scalar.md)
- リテラル型への参照
- リテラル型の配列
- 以下の全ての特性を持つクラス型
	- [トリビアルなデストラクタを持つ](./is_trivially_destructible.md)
	- 全てのコンストラクタが、定数式で初期化できること
	- 集成体であること、もしくは一つ以上の`constexpr`コンストラクタ、もしくはコピー／ムーブコンストラクタ以外のコンストラクタテンプレートを持っていること
	- 全てのデータメンバおよび基本クラスがリテラル型であること
- `void` (C++14から)

リテラル型は、`constexpr`関数のパラメータおよび戻り値の型に対する制約として使用されている。


##例
```cpp
#include <type_traits>

struct X {
  int value;

  constexpr X(int value)
    : value(value) {}
};

static_assert(std::is_literal_type<int>::value, "int is literal type");
static_assert(std::is_literal_type<X>::value, "X is literal type");

int main() {}
```

###出力
```
```

##バージョン
###言語
- C++11

###処理系
- [Clang](/implementation#clang.md): 3.1
- [GCC, C++0x mode](/implementation#gcc.md): 4.6.4
- [Visual C++](/implementation#visual_cpp.md): ??

###備考
Clang 3.0では、上記サンプルにおける`X`型が、リテラル型と見なされない。この問題は、Clang 3.1で修正されている。


