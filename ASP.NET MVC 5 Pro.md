
- REST - 表现式状态传输 **Re**presentational **S**tate **T**ransfer
- TDD - 软件的实现是依据测试规范实现的
- ASP.NET WEB FORM 单片式设计，用户界面和后台处理逻辑被耦合在一起，不易进行单元测试
- MVC框架对每一个组件提供了三种选择
  - 使用组件现行的默认行为（可满足大多数应用程序）  
  - 派生默认实现的一个子类，以调整其行为
  - 用接口和抽象基类的一个**新的实现**来完全替换该组件 
- MVC关注分离，model中操作数据的逻辑仅包含在model中，显示数据的逻辑只包含在View中，而处理用户请求和用户输入的代码只包含在Controller中。

## Razor视图引擎
- .cshtml文件扩展名表示这是一个由Razor进行处理的C#视图。
- Razor引擎处理视图内容并生成发送给浏览器的HTML。
- 对于渲染的解释
-![](https://github.com/Carlos-Liu/Notes4Work/blob/master/%E5%AD%A6%E4%B9%A0%E6%80%BB%E7%BB%93/images/Pro%20asp.net%20mvc/Render%20explaination.png)

## Controller / View
MVC中，Controller的工作是构造一些数据，并将其传递给视图，而视图则负责把它渲染成HTML。

ASP.NET MVC中控制器是一些派生自```system.Web.Mvc.Controller```的类，是框架内置的控制器基类。Controller中的每一个public方法都成为一个Action，意即可以用某个URL通过Web来调用它，以执行一个动作。

Action返回ViewResult对象，是指示MVC去渲染视图，并返回了它所产生的HTML。

MVC约定：
- 控制器放到Controllers文件夹
- 视图放到Views文件夹，文件夹结构与关联的Controller名称相对应，e.g. ```Views\Controller_A\Action_1```

Visual Studio在调试web程序时会分配一个随机端口，并启动IIS Express（vs附带的精简版的全功能IIS应用程序服务器，用于开发期间递交ASP.NET的内容和服务）。

## Action

controller中的一个public方法称为一个action，这种方法通过ASP.NET的路由系统与一个可配置的URL相关联。当一个请求被发送给与一个action相关联的URL时，便会执行此action中的语句，以进行domain model上的一些操作，然后选择一个view显示给client。

*Todo：P44页图*

一种方法用于响应HTTP的**GET**请求：Get请求是某人单击一个链接时，浏览器正常发出的请求，当有人第一次访问/Home/Index时，这个action负责显示最初的页面。

一种方法用于响应HTTP的**POST**请求：这个action负责接收所递交的数据，并决定用它做什么。

这两种方法都由同样的URL进行调用，但MVC确保会根据所处理的是GET请求或者POST请求，来调用合适的方法。

## ViewBag
将数据从controller传递给view的一种方式是使用ViewBag对象，它是controller基类的一个成员。ViewBag是一种动态对象，可以给它赋任意属性，这些属性的值在随后渲染的view中是可用的。对于属性的名称没有特别要求，只要在controller和view中保持匹配即可。

- Controller
  
      public ViewResult TestAction()
      {
        int hour = DateTime.Now.Hour;
        ViewBag.CurrentHour = hour.ToString();
        return View();
      }

- View
  
      <div>"Current Hour is: " + @ViewBag.CurrentHour</div>


## 强类型视图
渲染一个特定的Model类型（指定了想使用的类型）

## 路由系统 Routing System
它决定如何将URL映射到controller以及对应的action上（App_Start/RouteConfig.cs），MVC**默认约定**为Home/Index。MVC的每一个Action都有它自己的URL，而MVC使用路由系统将这些URL转换为Action。

## Helper Method辅助器方法

MVC框架附带了一组内置的辅助器方法，如Html.ActionLink，可以方便的用来渲染HTML的链接、文本框输入、复选框、选择框以及其他种类的内容。

辅助器方法中的lambda表达式用来选择与input元素有关的**属性**，如下的TextFor辅助器方法会生成一个input元素的HTML,该元素的id和name标签属性设置为**Phone**，Phone是所选域类的属性名字(Property of the view model class)。

        @Html.TextFor(x => x.Phone)

也可以将ViewModel中的属性名指定为一个字符串，如```@Html.TextFor("Phone")```

@using(Html.BeginForm()) { ... } 这里的using的作用是帮助Html.BeginForm辅助器在超出范围时关闭HTML的form元素，即Html.BeginForm辅助器方法会创建form元素的两部分，如下

        <form action="/Controller_A/Action_1" method="post">
         . . .
        </form>

- 辅助器方法有一个可选的对象参数，可在其所创建的元素上指定标签属性，如@Html.TextBoxFor(x => x.Name, **new { @class="form-control" }** )

## 模型绑定 (Model Binding)
模型绑定是MVC特性。HTML辅助器方法的作用是：在创建发送给客户端的表单数据时，生成的是HTML的input元素，其中的id和name标签属性的值来自于模型类的**属性名**，HTML辅助器将model数据转换为HTML信息，即 **model -> HTML** 的方式进行数据转换。

与此相反，对于模型绑定，会根据HTML中input的元素名称和值来设置model实例中的对应属性值，然后该model实例被传递给处理POST的action，所以模型绑定是利用表单元素及其输入的数据来创建model对象，即采用 **HTML -> model** 的方式进行数据转换。


## ViewModel属性验证
MVC支持验证规则声明，即验证约束是使用标准的C#注解属性特性来表示的. MVC会自动侦测这些attribute，并在模型绑定过程中使用它们进行数据验证。同时也可以在controller中使用ModelState.IsValid来检查是否验证通过。

        [Required(ErrorMessage="Pleases enter your name.")]
        public string Name {get;set;}
        
## Domain Model V.s. View Model
- Domain model包含业务领域的**数据、以及处理这些数据的操作、转换和规则**
- View model只表现**view与controller之间传递的数据**
- MVC中的View model是一种简单的模型类，只用于从controller向view传递数据。而domain model是数据、操作以及规则的完整表示。

## Bootstrap
- Bootstrap的基本特性是通过运用于HTML元素的class起作用的，这些class与放在Content文件夹中的样式表文件所定义的CSS选择器相关联。

## DI/Ioc container
P49 - 50

## Misc
- 可以从solution explorer中拖拽javascript和css文件，放到cshtml代码中，visual studio能够对所选的文件自动创建script和link元素。
- Content文件夹中的脚本都有一个对应的带有 min 前缀的配对文件，如bootstrap.css和bootstrap.min.css，将应用程序部署到产品环境时，这是压缩javascript和css文件的通用做法，即min是去除所有空格符的版本。就javascript而言，它会用较短的标签替换函数及变量名，这种压缩的目的是为了减少对浏览器递送内容时所需的带宽量。

- MVP模式有两个实现
    - 被动式视图实现（Passive view）：view不包含逻辑，它是UI控件的容器，由presenter直接进行操纵。    
    - 监管控制器实现（Supervisor controller): view可能要负责一些具有表现逻辑的元素，如data binding，并给出对domain model数据源的引用。
    
- 对于一个程序员，如果没有好的设计方法学，而且根本不做测试，则需要让用户去发现程序的错误，这种程序员属于低级别程序员。
- TDD只能在有基础并且成熟的开发团队中使用，并且团队成员具有较高的技能水平和**纪律约束**。

- 开源浏览器自动化工具：
    - Selenium RC(http://seleniumhq.org)，需要java服务器
    - WatiN （http://watin.sourceforge.net)
