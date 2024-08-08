# Ownership所有权

## Rust内存管理方式

*   所有权系统
*   特点：

    *   Rust 使用所有权系统进行内存管理，编译器在编译时通过静态分析来确保内内存安全
    *   每个值都有一个所有者，在任何时候只能有一个有效的所有者
    *   通过借用(引用)机制来共享数据，同时保证数据竞争和悬垂指针的安全
*   优点：

    *   在编译时保证内存安全，没有运行时开销
    *   避免了数据竞争和悬垂指针
*   缺点：

    *   需要程序员理解和遵循所有权和借用规则，学习曲线较陡

## 所有权规则

Rust 是一种系统编程语言，其设计目的是确保内存安全并防止数据竞争，而不依赖垃圾回收器。这种内存安全性主要通过所有权系统来实现。

1.  **所有权基本规则**

    1.  每一个值都有一个所有者(owner)
    2.  在任一时刻，值只能有一个所有者
    3.  当所有者离开作用域(scope)，值会被丢弃(drop)

## 练习

    //第一种
    fn take_ownership(s: String) -> String {
        s
    }
    let s1 = String::from("Hello");
    let s2 = take_ownership(s1.clone());

    println!("{s1}");
    println!("{s2}");


    //第二种
    fn take_ownership(s: &String) -> String {
        s.to_string()
    }
    let s1 = String::from("Hello");
    let s2 = take_ownership(&s1);

    println!("{s1}");
    println!("{s2}");

