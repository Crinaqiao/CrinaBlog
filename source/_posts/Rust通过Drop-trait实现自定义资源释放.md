---
title: Rust通过Drop trait实现自定义资源释放
tags:
  - Rust
categories:
  - 学习笔记
cover: https://picsum.photos/1080/1080?random=138423
feature: false
date: 2022-10-26 17:06:33
---
# Rust通过Drop trait实现自定义资源释放
:::tip 介绍
Drop trait 只有一个方法：drop，
当对象离开作用域时会自动调用该 方法。
Drop trait 的主要作用是释放实现者的实例拥有的资源。

Box，Vec，String，File，以及 Process 是一些实现了 Drop trait 来释放 资源的类型。
Drop trait 也可以为任何自定义数据类型手动实现。
:::

## 代码示例
```Rust
struct Droppable{
    name:&'static str,
}

impl Drop for  Droppable{
    fn drop(&mut self) {
        println!("> 销毁 {}",self.name);
    }
}

fn main() {
    let _a=Droppable{name:"a"};

    // 代码块A
    {
        let _b=Droppable{name:"b"};

        // 代码块B
        {
            let _c=Droppable{name:"c"};
            let _d=Droppable{name:"d"};
            
            println!("离开代码块B");
        }
        println!("刚离开代码块B");
        println!("离开代码块A");
    }
    println!("刚离开代码块A");
    drop(_a);
    println!("main函数结束");
    // `_a` *不会*在这里再次销毁，因为它已经被（手动）销毁。
}
```

## 运行结果
```bash
离开代码块B
> 销毁 d
> 销毁 c
刚离开代码块B
离开代码块A
> 销毁 b
刚离开代码块A
> 销毁 a
main函数结束
```