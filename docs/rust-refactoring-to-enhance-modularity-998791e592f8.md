# Rust 重构增强模块化

> 原文：<https://medium.com/nerd-for-tech/rust-refactoring-to-enhance-modularity-998791e592f8?source=collection_archive---------6----------------------->

![](img/a1fbf0598a8285fa3415b30c6f86525c.png)

**简介**

生产可靠的系统软件具有挑战性。指针操作、可变堆数据和并发性通常用于实现高性能，但会导致难以发现和重现的细微错误。 [Rust](https://www.technologiesinindustry4.com/) 编程语言通过其类型系统静态地防止一些错误来解决这个问题，该类型系统将一个排他的能力与每个可变的内存位置相关联。在任何时候，任何独占的能力都被最多一个正在执行的函数持有:只有那个代码可以访问内存位置。这些独占能力通常被交换为共享能力，通过共享能力，许多引用可以读取一个位置，但是当需要别名时，没有一个引用可以修改它。Rust 的类型系统应用了这一原则，确保类型良好的 [Rust](https://www.technologiesinindustry4.com/) 程序不会出现数据竞争、悬空指针或别名引用带来的意外副作用。

**描述**

我们将解决与程序结构相关的四个问题，以改进我们的程序。首先，我们的关键函数现在执行两项任务:解析参数和读取文件。对于这样一个小函数，这不是一个严重的问题。但是，如果我们仍然在 main 中扩展程序，大多数函数处理的独立任务的数量将会增加。随着一个功能获得更多的职责，它变得更难推理，更难检查，更难改变而不破坏它的一部分。最好将功能分开，这样每个功能负责一项任务。这个问题也与第二个问题有关:虽然查询和文件名是我们程序的配置变量，但是像内容这样的变量是用来执行程序逻辑的。main 变得越长，我们要纳入范围的变量就越多；范围内的变量越多，就越难跟踪每个变量的目标。最好将配置变量分组到一个结构中，以使它们的目的清晰。
第三个问题是，我们曾经使用 expect 在读取文件失败时打印一条错误消息，但是错误消息只是打印了读取文件出错的地方。[读取文件失败的原因有很多:例如，文件可能丢失了，或者我们没有权限打开它。](https://www.technologiesinindustry4.com/)现在，不管发生什么事情，我们都会在阅读文件错误信息时打印出出错信息，但这不会给用户任何信息！
第四，我们反复使用 expect 来处理不同的错误，如果用户在没有指定足够参数的情况下运行我们的程序，他们将从 Rust 那里得到一个索引越界错误，这并不能清楚地解释这个问题。如果所有的错误处理代码都在一个地方，那么将来的维护人员在需要改变错误处理逻辑时，就只有一个地方可以查阅代码，这可能是最好的。将整个错误处理代码放在一个地方也将确保我们打印的消息对我们的最终用户有意义。

![](img/04b613366776e37ef5906b6525fdd330.png)

让我们通过重构我们的项目来解决这四个问题。

**二元项目的关注点分离**

将多项任务的责任分配给 most 功能的组织问题在几个二元项目中很常见。因此，Rust 社区已经开发了一个过程，当主程序开始变大时，作为分割二进制程序的独立关注点的建议。该方法具有后续步骤:

将程序分发到 main.rs 和 lib.rs 中，并将您的程序逻辑移动到 lib.rs 中
只要指令解析逻辑很少，它就可以保留在 main.rs 中。从 main.rs 中提取它，并将其移动到 lib.rs 中当指令解析逻辑开始变得复杂时，在此过程之后保留在 main 函数中的职责应限于以下内容:

*   用参数值调用指令解析逻辑
*   设置其他配置
*   在 lib.rs 中调用运行函数
*   如果 run 返回错误，则处理错误

这种方式是关于分离关注点:main.rs 处理程序的运行，lib.rs 处理手头任务的所有逻辑。这种结构使我们能够通过将程序移入 lib.rs 中的函数来测试我们程序的所有逻辑。仍然在 main.rs 中的唯一代码足够小，可以通过读取它来验证它的正确性。因为我们不能直接测试大多数函数，所以让我们按照这个过程重新编写我们的程序。

**提取参数解析器**

我们将解析参数的功能提取到一个函数中，main 将调用该函数来组织将指令解析逻辑移动到 src/lib.rs 中。清单 12–5 显示了 main 的新开始，它调用一个替换函数 parse_config，我们将在 src/main.rs 中定义该函数。

```
Filename: src/main.rs
fn main() {
let args: Vec = env::args().collect();let (query, filename) = parse_config(&args);// --snip--
}
fn parse_config(args: &[String]) -> (&str, &str) {
let query = &args[1];
let filename = &args[2];
(query, filename)
}
```

我们仍然将指令参数收集到一个向量中，但是我们没有将索引 1 处的参数值赋给变量 query，也没有将索引 2 处的参数值赋给 most 函数中的变量 filename，而是将整个向量传递给 parse_config 函数。我们仍然在 main 中创建查询和文件名变量，但是 main 不负责确定指令参数和变量如何对应。
对于我们的小程序来说，这种重新做的工作似乎有些多余，但是我们正在以小而渐进的方式进行重构。[在做了这样的修改之后，再次运行程序来验证参数解析仍然有效。经常看到自己的进步很好，一旦出现问题，有助于找出问题的原因。](https://www.technologiesinindustry4.com/)

**分组配置值**

我们可以采取另一个小步骤来进一步增强 parse_config 函数。在这一瞬间，我们返回一个元组，另一方面，我们立即再次将该元组拆分成单独的部分。这通常是一个象征，也许我们还没有适当的抽象。

显示还有改进空间的另一个指标是，配置是 parse_config 的一部分，这意味着我们返回的两个值是相关的，并且都是一个配置值的一部分。除了将这两个值组合成一个元组之外，我们目前没有在信息的结构中传达这个意思；我们可以将这两个值放入一个结构中，并为每个结构字段提供一个有意义的名称。这样做将使代码的未来维护者更容易了解各种值之间的关系以及它们的用途。

注意:当 posh 类型更合适时使用原始值是一种反模式，称为原始痴迷。

```
Filename: src/main.rs
fn main() {
let args: Vec = env::args().collect();
let config = parse_config(&args);
println!("Searching for {}", config.query);
println!("In file {}", config.filename);
let contents = fs::read_to_string(config.filename)
.expect("Something went wrong reading the file");
// --snip--
}
struct Config {
query: String,
filename: String,
}
fn parse_config(args: &[String]) -> Config {
let query = args[1].clone();
let filename = args[2].clone();
Config { query, filename }
}
```

我们添加了一个名为 Config 的结构，它被定义为拥有名为 query 和 filename 的字段。parse_config 的签名现在表明它返回一个配置值。我们现在将 Config 定义为在 parse_config 的主体中包含自己的字符串值，其中我们希望返回引用 args 中的字符串值的字符串片段。main 中的 args 变量是参数值的所有者，只是让 parse_config 函数借用它们，这表明如果 config 试图要求 args 中的值的所有权，我们就违反了 Rust 的借用规则。

我们可以用许多不同的方法来管理字符串数据，但是最简单的方法是对值调用 clone 方法，尽管这种方法有些低效。这可能会为 Config 实例创建一个完整的信息副本，这比存储字符串数据需要更长的时间和更多的内存。然而，克隆信息也使我们的代码非常简单，因为我们不需要管理引用的生命周期；在这种情况下，放弃触摸性能以实现简单性可能是一种值得的权衡。

![](img/1d7a4d69c38fded749711d12e819276d.png)

**使用克隆人的利弊**

[许多 Rust aceans 都倾向于避免使用克隆来修复所有权问题，因为它的运行时间成本很高。](https://www.technologiesinindustry4.com/)拥有一个效率稍低的工作程序比第一次就对代码进行过度优化要好。随着我们对 Rust 越来越有经验，从最有效的解决方案开始会更容易，除了现在，调用 clone 是完全可以接受的。

我们的代码现在更准确地表达了问题和文件名是相关的，它们的目的是配置程序如何工作。任何使用这些值的代码都知道如何在 config 实例中为自己的目的而命名的字段中找到它们。

**为配置创建构造函数**

到目前为止，我们已经从 main 中提取了解析指令参数的逻辑，并将其放在 parse_config 函数中。这样做有助于我们确定查询和文件名值与代码中应该传达的关系相关。然后，我们添加了一个 Config struct 来调用 query 和 filename 的相关目的，并准备好从 parse_config 函数返回值的名称作为 struct 字段名称。

现在 parse_config 函数的目的是创建一个配置实例，我们将把 parse_config 从一个 clear 函数改为一个名为 new 的函数，它与配置结构相关。进行这种修改将使代码更符合习惯。我们将通过调用 String::new 在标准库中创建类型的实例，比如 String。类似地，通过将 parse_config 更改为与 config 相关的替换函数，我们将准备好通过调用 Config::new 来创建 Config 的实例。

```
Filename: src/main.rs
fn main() {
let args: Vec = env::args().collect();
let config = Config::new(&args);
// --snip--
}
// --snip--
impl Config {
fn new(args: &[String]) -> Config {
let query = args[1].clone();
let filename = args[2].clone();Config { query, filename }
}
}
```

我们已经修改并更新了 main，将我们调用 parse_config 的地方改为调用 Config::new。我们已经将 parse_config 的名称转换为 new，并将其移动到一个 impl 块中，该块将新函数与 config 关联起来。请再次尝试编译此代码，以确保它能够正常工作。

更多详情请访问:[https://www . technologiesinindustry 4 . com/rust-refactoring-to-enhance-modularity/](https://www.technologiesinindustry4.com/rust-refactoring-to-enhance-modularity/)