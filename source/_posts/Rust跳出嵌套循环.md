---
title: Rust跳出嵌套循环
tags:
  - Rust
categories:
  - 学习笔记
cover: https://picsum.photos/1080/1080?random=13487985
feature: false
date: 2022-09-01 15:53:03
---
# Rust跳出嵌套循环
> 在处理嵌套循环的时候可以 break 或 continue 外层循环。在这类情形中，循环必须用一些 'label（标签）来注明，并且标签必须传递给 break/continue 语句。

## 示例代码
```Rust
fn main() {
    'outer: loop {
        println!("进入外循环");

        'inner: loop {
            println!("进入内循环");

            // 这只是中断内部的循环
            // break;

            // 这会中断外层循环
            break 'outer;
        }

        println!("这里是不可达代码");
    }

    println!("退出外层循环");
}

```