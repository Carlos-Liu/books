# HTML教程
 > http://www.runoob.com/html/html-tutorial.html

    <!DOCTYPE html>
    <html>
    <head> 
    <meta charset="utf-8"> 
    <title>文档标题</title>
    </head>

    <body>
    文档内容......
    </body>

    </html>

## 基础
- 对于中文网页需要使用```<meta charset="utf-8">```声明编码，否则会出现乱码。有些浏览器会设置 GBK 为默认编码，则你需要设置为```<meta charset="gbk">```
- HTML文档的后缀名, .html, .htm没有区别，都可以使用
- ```<!DOCTYPE>``` 声明
  > <!DOCTYPE>声明有助于浏览器中正确显示网页。  
  > 网络上有很多不同的文件，如果能够正确声明HTML的版本，浏览器就能正确显示网页内容。  
  > doctype 声明是不区分大小写的  
  > 查看完整网页声明类型[DOCTYPE 参考手册](http://www.runoob.com/tags/tag-doctype.html)
- HTML 链接是通过标签 ```<a>``` 来定义的.
  > ```<a href="http://www.runoob.com">这是一个链接</a>``` 
- 开始标签常被称为起始标签（opening tag），结束标签常称为闭合标签（closing tag）。
- ```<body>``` 元素定义了 HTML 文档的主体。

## 属性
- HTML 元素可以设置属性
- 属性可以在元素中添加附加信息
- 属性一般描述于开始标签
- 属性总是以名称/值对的形式出现，比如：```name="value"```。
- 属性和属性值对大小写不敏感。不过，万维网联盟在其 HTML 4 推荐标准中**推荐**小写的属性/属性值。而新版本的 (X)HTML **要求**使用小写属性。
- HTML 链接由 ```<a>``` 标签定义。链接的地址在 **href 属性**中指定：
  > ```<a href="http://www.runoob.com">这是一个链接</a>```
- 属性值应该始终被包括在引号内。双引号是最常用的，不过使用单引号也没有问题。
  > Remark: 在某些个别的情况下，比如属性值本身就含有双引号，那么您必须使用单引号，例如：```name='John "ShotGun" Nelson'```
- 查看完整的HTML属性列表: [HTML 标签参考手册](http://www.runoob.com/tags/html-reference.html), [HTML 标准属性参考手册](http://www.runoob.com/tags/ref-standardattributes.html)

## 标题 ```<h1>```
- 请确保将 HTML 标题 标签只用于标题。不要仅仅是为了生成粗体或大号的文本而使用标题。
- 搜索引擎使用标题为您的网页的结构和内容编制索引。
- 因为用户可以通过标题来快速浏览您的网页，所以用标题来呈现文档结构是很重要的。
- 浏览器会自动地在标题和段落的前后添加空行

## 格式化标签
|标签 | 描述 |
|:-|:-|
| ```<b>``` | 定义粗体文本 |
| ```<em>``` | 定义着重文字 |
| ```<i>``` | 定义斜体字 |
| ```<small>``` | 定义小号字 |
| ```<strong>``` | 定义加重语气 |
| ```<sub>``` | 定义下标字 |
| ```<sup>``` | 定义上标字 |
| ```<ins>``` | 定义插入字 |
| ```<del>``` | 定义删除字 |
| ```<abbr>``` | 定义缩写 |
| ```<address>``` | 定义地址 |
| ```<bdo>``` | 定义文字方向 |
| ```<blockquote>``` | 定义长的引用 |
| ```<q>``` | 定义短的引用语 |
| ```<cite>``` | 定义引用、引证 |
| ```<dfn>``` | 定义一个定义项目 |

## 链接
链接的 HTML 代码很简单。它类似这样：   
     ```<a href="url">链接文本</a>```  
href 属性描述了链接的目标。

## 图像
定义图像的语法是：

    ```<img src="url" alt="some_text">```
- src指明图像的URL地址
- alt 属性用来为图像定义一串预备的可替换的文本。在浏览器无法载入图像时，浏览器将显示这个替代性的文本而不是图像。为页面上的图像都加上替换文本属性是个好习惯，这样有助于更好的显示信息，并且对于那些使用纯文本浏览器的人来说是非常有用的。

**设置图像链接**   

```<p>无边框的图片链接:<a href="http://www.runoob.com/xxx"><img border="0" src="smiley.gif" alt="HTML 教程" width="32" height="32"></a></p>```

**创建图像映射**  
```<map>```定义图像地图，```<area>```定义图像地图中的可点击区域，[参考示例](http://www.runoob.com/try/try.php?filename=tryhtml_areamap)

### id 属性
id属性可用于创建在一个HTML文档**书签标记**。  
**提示**: 书签是不以任何特殊的方式显示，在HTML文档中是不显示的，所以对于读者来说是隐藏的。  

实例  
在HTML文档中插入ID:  
    ```<a id="tips">有用的提示部分</a>```
    
在HTML文档中创建一个链接到"有用的提示部分(id="tips"）"：  
    ```<a href="#tips">访问有用的提示部分</a>```  
或者，从另一个页面创建一个链接到"有用的提示部分(id="tips"）"：  
    ```<a href="http://www.runoob.com/html/html-links.html#tips">访问有用的提示部分</a>```

## HEAD
```<head>``` 元素包含了所有的头部标签元素。在 ```<head>```元素中你可以插入脚本（scripts）, 样式文件（CSS），及各种meta信息。  

可以添加在头部区域的元素标签为: ```<title>, <style>, <meta>, <link>, <script>, <noscript>, and <base>```.
- ```<title>``` 元素:
  - 定义了浏览器工具栏的标题
  - 当网页添加到收藏夹时，显示在收藏夹中的标题
  - 显示在搜索引擎结果页面的标题  
- ```<base>``` 标签描述了基本的链接地址/链接目标，该标签作为HTML文档中所有的链接标签的**默认链接**.
- ```<link>``` 标签定义了文档与外部资源之间的关系。通常用于链接到样式表 ```<link rel="stylesheet" type="text/css" href="mystyle.css">```.
- ```<style>``` 标签定义了HTML文档的样式文件引用地址. 在```<style>```元素中你也可以直接添加样式来渲染 HTML 文档.
- ```<meta>```标签提供了元数据.元数据也不显示在页面上，但会被浏览器解析。META 元素通常用于指定网页的描述，关键词，文件的最后修改时间，作者，和其他元数据。元数据可以使用于浏览器（如何显示内容或重新加载页面），搜索引擎（关键词），或其他Web服务。
   > 为搜索引擎定义关键词:  
   > ```<meta name="keywords" content="HTML, CSS, XML, XHTML, JavaScript">```  
   > 为网页定义描述内容:  
   > ```<meta name="description" content="免费 Web & 编程 教程">```  
   > 定义网页作者:  
   > ```<meta name="author" content="Runoob">```  
   > 每30秒钟刷新当前页面:  
   > ```<meta http-equiv="refresh" content="30">```  

## 注意
- 当显示页面时，浏览器会移除源代码中多余的空格和空行。**所有连续的空格或空行都会被算作一个空格**。需要注意的是，HTML 代码中的所有连续的空行（换行）也被显示为一个空格。 [demo](http://www.runoob.com/try/try.php?filename=tryhtml_poem)
- 请始终将正斜杠添加到子文件夹。假如这样书写链接：```href="http://www.runoob.com/html"```，就会向服务器**产生两次 HTTP 请求**。这是因为**服务器会添加正斜杠到这个地址，然后创建一个新的请求**，就像这样：```href="http://www.runoob.com/html/"```。

## 表格
- 表格由 ```<table>``` 标签来定义。
- 每个表格均有若干行（由 ```<tr>``` 标签定义）
- 每行被分割为若干单元格（由 ```<td>``` 标签定义）。字母 td 指表格数据（table data），即数据单元格的内容。数据单元格可以包含文本、图片、列表、段落、表单、水平线、表格等等。
- 表格的表头使用 ```<th>``` 标签进行定义。
 
 ```
   <table border="1">
       <tr>
           <td>row 1, cell 1</td>
           <td>row 1, cell 2</td>
       </tr>
       <tr>
           <td>row 2, cell 1</td>
           <td>row 2, cell 2</td>
       </tr>
   </table>
```
在浏览器显示如下  
   <table border="1">
       <tr>
           <td>row 1, cell 1</td>
           <td>row 1, cell 2</td>
       </tr>
       <tr>
           <td>row 2, cell 1</td>
           <td>row 2, cell 2</td>
       </tr>
   </table>

## 列表
- 无序列表使用ul标签，有序列表使用ol标签，每个列表项实用li标签

```
<ul>
  <li>Coffee</li>
  <li>Milk</li>
</ul>  
```
- 对于有序列表，可以指定type属性来定义不同类型的有序列表，例如```<ol type="A">```定义列表为大写字母编号，如下
```
A. Apples
B. Bananas
C. Oranges
```
- 对于无序列表，可以指定style属性来定义不同类型的列表编号，例如```<ul style="list-style-type:square">```定义bullets为方块样式
