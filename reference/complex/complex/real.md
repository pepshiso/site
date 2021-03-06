#real
```cpp
constexpr T real() const;		// (1)
void real(T val);				// (2) C++11 から
```

##概要
複素数の実部を取得、あるいは、設定する。


##効果
- (1) -
- (2) 実部に `val` を設定する。


##戻り値
- (1) 実部
- (2) -


##備考
- 実部の取得は、同名の非メンバ関数 [`real`](../real.md) も存在する。
- 実部の設定は、C++11 から。


##例
```cpp
#include <iostream>
#include <complex>

int main()
{
  std::complex<double> c(1.0, 2.0);
  std::cout << c << ", real part = " << c.real() << std::endl;
  c.real(4.0);
  std::cout << c << ", real part = " << c.real() << std::endl;
}
```
* real[color ff0000]

###出力
```
(1,2), real part = 1
(4,2), real part = 4
```


##参照
|                    |                                  |
|--------------------|----------------------------------|
|[`imag`](imag.md)   | 虚部を取得、あるいは、設定する。 |
|[`real`](../real.md)| 実部を取得する。（非メンバ関数） |
|[`imag`](../imag.md)| 虚部を取得する。（非メンバ関数） |
