# 像专业人员一样用 Chompjs 和 JMESPath 提取 JSONs

> 原文：<https://medium.com/nerd-for-tech/extract-jsons-like-a-pro-with-chompjs-and-jmespath-74e97429cc8a?source=collection_archive---------20----------------------->

![](img/69ab2af7026f82322b20fa6c9b4ab656.png)

对于任何 web 数据提取开发人员来说，处理 javascript 对象都是一项重要的技能。在处理动态页面时，您可能只是刚刚开始涉足这个领域，但是您很快就会发现

# 使用 chompjs 库解析脚本文本

因此，让我们假设您已经从脚本标记中提取了这段文本

```
__DATA__ = {"data":{"type":"@products", "products":[{"id":12345678, "name":"Bacon", "brand": "Some Brand", "price":2.50, "instock": false},{"id":12345679, "name":"Ham", "price":3.50, "instock": true},{"id":12345680, "name":"Beef", "price":1.50, "instock": false}]}}; some_javascript(data) {results = do_stuff(data); return results}; new beep_boop_js_var = some_javascript(__DATA__)
```

这段文字有很多你不想要的元素，但它也有，看起来很像 python 字典，包含很多产品的数据。这是一个 javascript 对象。通常你会有一个 JSON 包来帮助你把它变成一个字典。但是当它不是一个干净的 JSON 时你会怎么做呢？在这种情况下，Zytan Mariusz Obajtek 制作了一个包来帮助我们: [chompjs](https://github.com/Nykakin/chompjs) 。

```
from chompjs import parse_js_object 
script = """__DATA__ = {"data":{"type":"@products", "products":[{"id":12345678, "name":"Bacon", "brand": "Some Brand", "price":2.50, "instock": false},{"id":12345679, "name":"Ham", "price":3.50, "instock": true},{"id":12345680, "name":"Beef", "price":1.50, "instock": false}]}}; 
some_javascript(data) {results = do_stuff(data); return results}; new beep_boop_js_var = some_javascript(__DATA__)""" data = parse_js_object(script)
```

在这种情况下，parse_js_object 函数在脚本中查找第一个 js 对象，提取它，然后将其转换为 python 字典。这只是 chompjs 的冰山一角，查看 Github 上的例子，看看其他更难的格式，用它可以很容易地解析。

# 使用 JMESPath 提取数据

那么，现在你有了字典，从字典中获取数据的最好方法是什么呢？使用嵌套字典，挑选您需要的字段可能会很麻烦，但是您可以通过使用另一个包来使它变得容易得多: [JMESPath](https://github.com/jmespath/jmespath.py) 。

例如，如果您想从字典中获取产品列表，您可以通过一个函数调用来实现:

```
jmespath.search('data.products', data)
```

它不止于此。让我们更进一步，假设您想要产品的名称？您可以:

```
jmespath.search('data.products[].name', data)
```

此处的更改表明我想浏览产品列表并拉出名称字段，这将留给我一个产品名称列表。现在，虽然这已经非常有用，我们可以更深入一点。

假设您只想要这些产品中的一种产品的名称，即“培根”。实际上，我们可以在方括号中输入一个查询来过滤我们的结果:

```
jmespath.search('data.products[?name==`Bacon`]', data)
```

和前面一样，我们也可以拉出一个特定的字段:

```
jmespath.search('data.products[?name==`Bacon`].price', data)
```

现在，让我们做一些更有趣的事情。比方说，我想找到超过一定价格的产品。嗯，我也可以在这些括号里做其他种类的条件句:

```
jmespath.search('data.products[?price>`2`], data)
```

您可能已经注意到，只有一件商品有品牌，所以如果我执行以下操作，它将只给出该商品的品牌名称。在这种情况下要小心，如果有不完整的结果，您将不知道这些数据实际上来自哪个字典:

```
jmespath.search('data.products[].brand', data)
```

最后，您可能已经注意到我们示例中的 instock 字段有一个布尔值，所以如果我们只想获得所有库存商品的名称，我们可以这样做:

```
jmespath.search('data.products[?instock].name', data)
```

# 结论

这两个包可能是我在提取 web 数据时使用的两个比较重要的包。许多站点通常会在源代码中使用标准的 JSON 或 js 脚本，chompjs 可以为您提取这些脚本。对于这些情况以及大多数 API 响应，您可能最终会得到嵌套的字典，JMESPath 使筛选变得轻而易举。

如果你想看这些措施的视频，请查看我在 Youtube 上的视频。

查看其他用于解析 HTML 和提取数据的有用开源包:

*最初发表于*[T5【https://www.zyte.com】](https://www.zyte.com/blog/extract-json-using-chompjs-and-jmespath/)*。*