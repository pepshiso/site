#peek
```cpp
int_type peek();
```

##概要
（非書式化入力関数）ストリームバッファから次に入力される文字を先読みする。

すなわち、この関数は次に入力される文字を返すが、読み取り位置は変化しない。
この後の入力関数（書式化入力関数・非書式化入力関数いずれでも）で、改めて入力が行われる。

##戻り値

- `good() == true`なら、`rdbuf()->sgetc()`。
- `good() == false`なら、`Traits::eof()`。

##例
```cpp
#include <iostream>
#include <locale>

bool try_read_int(std::istream& is, unsigned & x) {
  is >> std::ws;
  if (std::isdigit(is.peek(), is.getloc())) {
    return is >> x
      ? true
      : false;
  } else {
    return false;
  }
}

int main() {
  std::cout << "0以上の整数を入力してください: " << std::flush;
  unsigned x;
  if (try_read_int(std::cin, x)) {
    std::cout << "入力された値: " << x << std::endl;
  } else {
    std::cout << "数値を入力してください。" << std::endl;
  }
}
```

##出力
```
（200を入力）
0以上の整数を入力してください: 200
入力された値: 200
```

##実装例
```cpp
int_type peek() {
  try {
    sentry s(*this, true);
    if (s) {
      return rdbuf()->sgetc();
    }
  } catch (...) {
    例外を投げずにbadbitを設定する;
    if ((exceptions() & badbit) != 0) {
      throw;
    }
  }
  return Traits::eof();
}
```

##バージョン
###言語
- C++98

##参照

- [`basic_istream::get`](./get.md)
- `basic_streambuf::sgetc`
