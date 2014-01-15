#basic_istream<>::sentry
```cpp
namespace std {
  template<class CharT, class Traits = char_traits<CharT>>
  class basic_istream<CharT, Traits>::sentry {
  public:
    explicit sentry(basic_istream<CharT, Traits>& is, bool noskipws = false);
    ~sentry();
    explicit operator bool() const;

    sentry(const sentry&) = delete;
    sentry& operator=(const setnry&) = delete;
  };
}
```
* basic_istream[link ../basic_istream.md]

##概要
`basic_istream<>::sentry`は、入力処理共通の前処理・後処理を実行するためのクラスである。
前処理・後処理がそれぞれコンストラクタ・デストラクタ内部で実行される。

書式化入力関数・非書式化入力関数は、内部で必ず`sentry`オブジェクトを構築・破棄する。

`explicit operator bool`関数は、コンストラクタでの処理が成功していれば`true`、さもなくば`false`を返す。

なお、C++標準規格では、規格で要求している処理のほかに、追加の処理を行っても良いとされている。

##参照

- [`basic_istream`](../basic_istream.md)