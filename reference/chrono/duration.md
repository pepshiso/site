#duration(C++11)

```cpp
namespace std {
namespace chrono {
  template <class Rep, class Period = ratio<1>>
  class duration;
}}
```

##概要
`duration`は、2つの時間の経過時間を表現するための型である。
`duration`のテンプレートパラメータである`ratio`の値によって、時間のためのあらゆる単位(ナノ秒、ミリ秒、秒, etc...)を表現することができる。

標準では、以下の`typedef`が提供される：

| `typedef名`                                         | 説明       | 対応バージョン |
|-----------------------------------------------------|------------|----------------|
| [`nanoseconds`](/reference/chrono/nanoseconds.md)   | ナノ秒     | C++11          |
| [`microseconds`](/reference/chrono/microseconds.md) | マイクロ秒 | C++11          |
| [`milliseconds`](/reference/chrono/milliseconds.md) | ミリ秒     | C++11          |
| [`seconds`](/reference/chrono/seconds.md)           | 秒         | C++11          |
| [`minites`](/reference/chrono/minutes.md)           | 分         | C++11          |
| [`hour`](/reference/chrono/hours.md)                | 時         | C++11          |


##メンバ関数
###構築／コピー／破棄

| 名前                                      | 説明                  | 対応バージョン |
|-------------------------------------------|-----------------------|----------------|
| [`(constructor)`](./duration/duration.md) | コンストラクタ        | C++11          |
| `~duration() = default;`                  | デストラクタ          | C++11          |
| `operator=(const duration&) = default;`   | 代入演算子            | C++11          |

###観測

| 名前                           | 説明         | 対応バージョン |
|--------------------------------|--------------|----------------|
| [`count`](./duration/count.md) | 値を取得する | C++11          |


###算術演算

| 名前                                              | 説明                     | 対応バージョン |
|---------------------------------------------------|--------------------------|----------------|
| [`operator+`](./duration/op_unary_add.md)         | 正の`duration`を生成する | C++11          |
| [`operator-`](./duration/op_unary_substract.md)   | 負の`duration`を生成する | C++11          |
| [`operator++`](./duration/op_increment.md)        | 値をインクリメントする   | C++11          |
| [`operator--`](./duration/op_decrement.md)        | 値をデクリメントする     | C++11          |
| [`operator+=`](./duration/op_add_assign.md)       | `+`の複合代入            | C++11          |
| [`operator-=`](./duration/op_substract_assign.md) | `-`の複合代入            | C++11          |
| [`operator*=`](./duration/op_multiply_assign.md)  | `*`の複合代入            | C++11          |
| [`operator/=`](./duration/op_divide_assign.md)    | `/`の複合代入            | C++11          |
| [`operator%=`](./duration/op_modulo_assign.md)    | `%`の複合代入            | C++11          |


##静的メンバ関数
###特別な値

| 名前                         | 説明         | 対応バージョン |
|------------------------------|--------------|----------------|
| [`zero`](./duration/zero.md) | 初期値を取得 | C++11          |
| [`min`](./duration/min.md)   | 最小値を取得 | C++11          |
| [`max`](./duration/max.md)   | 最大値を取得 | C++11          |


##メンバ型

| 名前     | 説明             | 対応バージョン |
|----------|------------------|----------------|
| `rep`    | 値の数値型 `Rep` | C++11          |
| `period` | 単位型 `Period`  | C++11          |


##例
```cpp
#include <iostream>
#include <chrono>
#include <ctime>

using std::chrono::system_clock;
using std::chrono::seconds;

void print(const system_clock::time_point& p)
{
  std::time_t t = system_clock::to_time_t(p);
  char buf[26];  // 最低26バイトが必要
#ifdef _MSC_VER
  // Visual Studioではctime_s()が推奨されている。
  ctime_s(buf, 26, &t);
#else
  // ctime()のリエントラント版
  ctime_r(&t, buf);
#endif
  // 出力された文字列には改行が含まれていることに注意
  std::cout << buf;
}

int main()
{
  // 現在日時を取得
  system_clock::time_point now = system_clock::now();

  // 3秒後の日時を取得
  system_clock::time_point p = now + seconds(3);

  print(now);
  print(p);
}
```

###出力例
```
Tue Oct 16 16:25:08 2012
Tue Oct 16 16:25:11 2012
```

##バージョン
###言語
- C++11

###処理系
- [GCC, C++0x mode](/implementation#gcc.md): 4.7.0

##参照

