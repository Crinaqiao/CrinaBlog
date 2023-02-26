---
title: Rust迭代器(Iterator)
tags:
  - Rust
categories:
  - 学习笔记
cover: https://picsum.photos/1080/1080?random=12103483
feature: false
date: 2022-10-26 19:29:01
---
# Rust迭代器
:::tip 介绍

Iterator trait 用来对集合（collection）类型（比如数组）实现迭代器。

这个 trait 只需定义一个返回 next（下一个）元素的方法，这可手动在 impl 代码块 中定义，或者自动定义（比如在数组或区间中）。

为方便起见，for 结构会使用 .into_iter() 方法将一些集合类型 转换为迭代器。

:::

## 常用方法
- `next()`  : 能返回 `next`（下一个）元素的方法。
- `take(n)` : 提取 `Iterator` 的前 `n` 项。
- `skip(n)` : 移除前 `n` 项，从而缩短了 `Iterator` 。
- `iter()` : 对数组/slice 产生一个 `Iterator`。

## 代码示例
```Rust
struct Fibonacci {
    curr: u32,
    next: u32,
}

// 为 `Fibonacci`（斐波那契）实现 `Iterator`。
// `Iterator` trait 只需定义一个能返回 `next`（下一个）元素的方法。
impl Iterator for Fibonacci {
    type Item = u32;
    
    // 我们在这里使用 `.curr` 和 `.next` 来定义数列（sequence）。
    // 返回类型为 `Option<T>`：
    //     * 当 `Iterator` 结束时，返回 `None`。
    //     * 其他情况，返回被 `Some` 包裹（wrap）的下一个值。
    fn next(&mut self) -> Option<u32> {
        let new_next = self.curr + self.next;

        self.curr = self.next;
        self.next = new_next;

        // 既然斐波那契数列不存在终点，那么 `Iterator` 将不可能
        // 返回 `None`，而总是返回 `Some`。
        Some(self.curr)
    }
}

// 返回一个斐波那契数列生成器
fn fibonacci() -> Fibonacci {
    Fibonacci { curr: 1, next: 1 }
}

fn main() {
    // `0..3` 是一个 `Iterator`，会产生：0、1 和 2。
    let mut sequence = 0..3;

    println!("Four consecutive `next` calls on 0..3");
    println!("> {:?}", sequence.next());
    println!("> {:?}", sequence.next());
    println!("> {:?}", sequence.next());
    println!("> {:?}", sequence.next());

    // `for` 遍历 `Iterator` 直到返回 `None`，
    // 并且每个 `Some` 值都被解包（unwrap），然后绑定给一个变量（这里是 `i`）。       
    println!("Iterate through 0..3 using `for`");
    for i in 0..3 {
        println!("> {}", i);
    }

    // `take(n)` 方法提取 `Iterator` 的前 `n` 项。
    println!("The first four terms of the Fibonacci sequence are: ");
    for i in fibonacci().take(4) {
        println!("> {}", i);
    }

    // `skip(n)` 方法移除前 `n` 项，从而缩短了 `Iterator` 。
    println!("The next four terms of the Fibonacci sequence are: ");
    for i in fibonacci().skip(4).take(4) {
        println!("> {}", i);
    }

    let array = [1u32, 3, 3, 7];

    // `iter` 方法对数组/slice 产生一个 `Iterator`。
    println!("Iterate the following array {:?}", &array);
    for i in array.iter() {
        println!("> {}", i);
    }
}

```

## 运行结果
```bash
Four consecutive `next` calls on 0..3
> Some(0)
> Some(1)
> Some(2)
> None
Iterate through 0..3 using `for`
> 0
> 1
> 2
The first four terms of the Fibonacci sequence are: 
> 1
> 2
> 3
> 5
The next four terms of the Fibonacci sequence are:
> 8
> 13
> 21
> 34
Iterate the following array [1, 3, 3, 7]
> 1
> 3
> 3
> 7
```