# 練習問題1.1
* [gccのマニュアル](https://gcc.gnu.org/onlinedocs/gcc-7.2.0/gcc/Overall-Options.html#Overall-Options)
  * c、hはC++、Cの区別なし
  * cc、cp、cxx、cpp、CPP、c++、C: C++のソースコード
  * hh、H、hp、hxx、hpp、HPP、h++、tcc: C++のヘッダファイル
  * ii: プリプロセスしないC++のソースコード
* clangは発見できず
* cpp、hppを何となく自分は使っていたが規定のものがあった

# 練習問題1.2
* [exit code](http://tldp.org/LDP/abs/html/exitcodes.html)
* [上記の日本語版](https://qiita.com/Linda_pp/items/1104d2d9a263b60e104b)
* [cppreference](http://en.cppreference.com/w/cpp/utility/program/EXIT_status): EXIT_SUCCESSとかならヘッダファイルで定義されている

```cpp
int main(void)
{
    return -1;
}
```
```cpp
> usr@xps13:~$ g++ hoge.cpp
> usr@xps13:~$ ./a.out
> usr@xps13:~$ echo $?
255
```

# 練習問題1.3
```cpp
#include <iostream>

int main(void)
{
    std::cout << "Hello, World" << std::endl;
    return 0;
}
```

# 練習問題1.4
```cpp
#include <iostream>

int main(void)
{
    std::cout << "Enter two numbers" << std::endl;
    int v1, v2;
    std::cin >> v1 >> v2;
    std::cout << "The product of " << v1 << " and " << v2 << " is "
              << v1 * v2 << std::endl;
    return 0;
}
```

# 練習問題1.5
```cpp
#include <iostream>
int main(void)
{
    using namespace std;
    cout << "The sum of ";
    cout << v1;
    cout << " and ";
    cout << v2;
    cout << " is ";
    cout << v1 + v2;
    cout << endl;

    return 0;
}
```

# 練習問題1.6
正しくない。``;``を取り除く必要あり。

# 練習問題1.7
```cpp
/*/**/*/
int main(){}
```
```
hoge.cpp:1:8: エラー: expected unqualified-id before ‘/’ token
 /*/**/*/
        ^
hoge.cpp:1:8: エラー: expected constructor, destructor, or type conversion before ‘/’ token
```

# 練習問題1.8
``std::cout << /* "*/" */;`` → missing terminating '"' character → ``std::cout << /* "*/" */";``

# 練習問題1.9
```cpp
#include <iostream>
int main(void)
{
    int sum = 0, i = 50;
    while (i <= 100)
    {
        sum += i;
    }
    std::cout << sum << std::endl;
    return 0;
}
```

# 練習問題1.10
```cpp
#include <iostream>
int main()
{
    int i = 10;
    while (i >= 0)
    {
        std::cout << i << " ";
        --i;
    }
    std::cout << std::endl;
    return 0;
}
```

# 練習問題1.11
```cpp
#include <iostream>

int main(void)
{
    int v1, v2;
    std::cin >> v1 >> v2;
    if (v1 > v2)
    {
        std::swap(v1, v2);
    }

    while (v1 < v2)
    {
        std::cout << v1 << " ";
        ++v1;
    }
    return 0;
}
```

# 練習問題1.12
-100から100までの整数の和になる

# 練習問題1.13
```cpp
#include <iostream>
int main(void)
{
    int sum = 0, i = 50;
    for (int i = 50; i <= 100; ++i)
    {
        sum += i;
    }
    std::cout << sum << std::endl;
    return 0;
}
```
```cpp
#include <iostream>
int main()
{
    int i = 10;
    for (int i = 10; i >= 0; --i)
    {
        std::cout << i << " ";
    }
    std::cout << std::endl;
    return 0;
}
```
# 練習問題1.14
forの方が変数のスコープが小さく、ループ中の不変条件などが分かりやすい。whileは外のスコープの変数に副作用を加えながら実行するときは良さそう。

# 練習問題1.15
# 練習問題1.16
```cpp
#include <iostream>
int main(void)
{
    int i, sum;
    while (std::cin >> i)
    {
        sum += i;
    }
    std::cout << sum << std::endl;
    return 0;
}
```
``Ctrl-D``でEOFが入力される。

# 練習問題1.17
```sh
> wget http://www.informit.com/content/images/9780321714114/downloads/GCC_4_7_0.zip
> unzip GCC_4_7_0.zip
```
occurs.ccをコンパイルして実行してみる。

# 練習問題1.18
同上

# 練習問題1.19
```cpp
#include <iostream>

int main(void)
{
    int v1, v2;
    std::cin >> v1 >> v2;
    while (v1 < v2)
    {
        std::cout << v1 << " ";
        ++v1;
    }
    return 0;
}
```

# 練習問題1.20
```cpp
#include <iostream>
#include "Sales_item.h"

int main(void)
{
    Sales_item item;
    while (std::cin >> item)
    {
        std::cout << item << std::endl;
    }
    return 0;
}
```

# 練習問題1.21
```cpp
#include <iosteam>
#include "Sales_item.h"

int main(void)
{
    Sales_item item1, item2;
    std::cin >> item1 >> item2;
    if (item1.isbn() == item2.isbn())
    {
        std::cout << item1 + item2 << std::endl;
        return 0;
    }
    else
    {
        std::cerr << "Data must refer to same ISBN" << std::endl;
        return -1;
    }
}
```

# 練習問題1.22
```cpp
#incldue <iostream>
#include "Sales_time.h"

int main(void)
{
    Sales_item sum, input;
    if (std::cin >> sum)
    {
        while(std::cin >> input)
        {
            if (input.isbn() == sum.isbn())
            {
                sum += input;
            }
            else
            {
                std::cout << sum << std::endl;
                sum = input;
            }
        }
        std::cout << sum << std::endl;
    }
    else
    {
        std::cerr << "No valid data" << std::endl;
        return -1;
    }

}
```

# 練習問題1.23
```cpp
#include <iostream>
#include "Sales_item.h"

int main(void)
{
    Sales_item current, input;
    if (std::cin >> current)
    {
        int cnt = 1;
        while (std::cin >> input)
        {
            if (input.isbn() == current.isbn())
            {
                ++cnt;
            }
            else
            {
                std::cout << current.isbn() << " appeared " << cnt << " times" << std::endl;;
                current = input;
                cnt = 1;
            }
            std::cout << current.isbn() << " appeared " << cnt << " times" << std::endl;
        }
    }

    return 0;
}
```

# 練習問題1.24
```sh
./a.out < data/book_sales
```

# 練習問題1.25
