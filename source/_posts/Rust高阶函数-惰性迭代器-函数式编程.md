---
title: Rust高阶函数&惰性迭代器&函数式编程
tags:
  - Rust
categories:
  - 学习笔记
cover: https://picsum.photos/1080/1080?random=13273
feature: false
date: 2022-09-13 21:51:46
---
# 高阶函数以及惰性计算介绍:
:::tip 高阶函数以及惰性计算介绍

**Rust 提供了高阶函数**（Higher Order Function, HOF），指那些输入一个或多个函数，并且/或者产生一个更有用的函数的函数。HOF 和惰性迭代器（lazy iterator）给 Rust 带来了函数式（functional）编程的风格。

**惰性计算**又称为惰性求值（Lazy Evaluation），是一个计算机编程中的概念，它的目的是要最小化计算机要做的工作，尽可能延迟表达式求值。延迟求值特别用于函数式编程语言中。**在使用延迟求值的时候，表达式不在它被绑定到变量之后就立即求值，而是在该值被取用的时候求值。**惰性计算的最重要的好处是它可以构造一个无限的数据类型。

惰性计算还可以在大规模数据处理中平滑处理时间，提高内存使用率。当处理大规模数据时，一次性进行处理往往是不方便的。

:::

# 代码：
```Rust
fn is_odd(n: u32) -> bool {

	n % 2 == 1

}

  

fn main() {

	println!("求所有平方后小于100的奇数的和！！！");
	
	let upper = 100;

  

	// 函数式的写法
	
	let sum_of_squared_odd_numbers: u32 =
	
	(0..).map(|n| {println!("map:{:?}",n);n*n}) // 所有自然数取平方
	
		.take_while(|&n|{println!("take_while:{:?}",n);n < upper}) // 取小于上限的
		
		.filter(|&n| {println!("filter:{:?}",n);is_odd(n)}) // 取奇数
		
		.fold(0, |sum, i| {println!("fold:{:?}",i);sum + i}); // 最后加起来
	
	println!("平方后小于100的奇数的和为： {}", sum_of_squared_odd_numbers);

}
```

# 运行：
```bash
求所有平方后小于100的奇数的和！！！
map:0
take_while:0
filter:0
map:1
take_while:1
filter:1
fold:1
map:2
take_while:4
filter:4
map:3
take_while:9
filter:9
fold:9
map:4
take_while:16
filter:16
map:5
take_while:25
filter:25
fold:25
map:6
take_while:36
filter:36
map:7
take_while:49
filter:49
fold:49
map:8
take_while:64
filter:64
map:9
take_while:81
filter:81
fold:81
map:10
take_while:100
平方后小于100的奇数的和为： 165
```

# 惰性迭代器演示：
**在使用惰性迭代器的时候，表达式不在它被绑定到变量之后就立即求值，而是在该值被取用的时候求值。**
>可以看到在debug的过程中代码多次往回跑，以此可见上面的观点

<video style="border-radius: 10px;
    width: 100%;" id="video" controls="" preload="none" poster="https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/videos/20220913221859.png">
      <source id="mp4" src="https://riven-cabin.oss-cn-guangzhou.aliyuncs.com/blog/videos/20220913220905.mp4" type="video/mp4">
</videos>
