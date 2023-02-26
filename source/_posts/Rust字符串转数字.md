---
title: Rust字符串转数字
tags:
  - Rust
categories:
  - 学习笔记
cover: https://picsum.photos/1080/1080?random=19465
feature: false
date: 2022-08-31 17:42:37
---
# Rust字符串转数字
## 代码
```Rust
fn main() {
	// 方式一
    let parsed: i32 = "5".parse().unwrap();
	// 方式二
    let turbo_parsed = "10".parse::<i32>().unwrap();

    let sum = parsed + turbo_parsed;

    println!("Sum: {:?}", sum)

}
```

> 我们经常需要把字符串转成数字。完成这项工作的标准手段是用 [`parse`](https://rustwiki.org/zh-CN/std/primitive.str.html#method.parse) 函数。我们得 提供要转换到的类型，这可以通过不使用类型推断，或者用 “涡轮鱼” 语法（turbo fish，`<>`）实现。
只要对目标类型实现了 [`FromStr`](https://rustwiki.org/zh-CN/std/str/trait.FromStr.html) trait，就可以用 `parse` 把字符串转换成目标类型。 标准库中已经给无数种类型实现了 `FromStr`。如果要转换到用户定义类型，只要手动实现 `FromStr` 就行。

## 方式一：在变量名后面提供转换到的类型
> 例如下面代码中的**i32**

```Rust
	let parsed: i32 = "5".parse().unwrap();
```

## 方式二：使用“涡轮鱼”语法（turbo fish，`<>`）实现。
> 例如以下代码在parse函数后面提供`<i32>`

```Rust
	let turbo_parsed = "10".parse::<i32>().unwrap();
```
