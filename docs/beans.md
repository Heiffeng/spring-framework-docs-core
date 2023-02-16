# 1. The IoC Container
## 1.4. Dependencies
A typical enterprise application does not consist of a single object (or bean in the Spring parlance). Even the simplest application has a few objects that work together to present what the end-user sees as a coherent application. This next section explains how you go from defining a number of bean definitions that stand alone to a fully realized application where objects collaborate to achieve a goal.

一个典型的企业应用程序并不是由单一的对象（或Spring术语中的bean）组成的。即使是最简单的应用也有一些对象，它们一起工作，呈现出最终用户所看到的连贯的应用。下一节将解释你如何从定义一些单独的Bean定义到一个完全实现的应用，在这个应用中，各对象相互协作以实现一个目标。

### 1.4.1. Dependency Injection

Dependency injection (DI) is a process whereby objects define their dependencies (that is, the other objects with which they work) only through constructor arguments, arguments to a factory method, or properties that are set on the object instance after it is constructed or returned from a factory method. The container then injects those dependencies when it creates the bean. This process is fundamentally the inverse (hence the name, Inversion of Control) of the bean itself controlling the instantiation or location of its dependencies on its own by using direct construction of classes or the Service Locator pattern.

依赖注入是一个对象用来定义他们依赖关系的过程（即与他们一起工作的其他对象），通过构造参数，工厂方法参数，或者构造方法和工厂方法之外的属性setter方法。容器在创建bean时注入这些依赖关系。从根本上说，这个过程就是bean自己控制实例和定位依赖反转到使用类的构造或服务定位模式（因此被称为控制反转）。

Code is cleaner with the DI principle, and decoupling is more effective when objects are provided with their dependencies. The object does not look up its dependencies and does not know the location or class of the dependencies. As a result, your classes become easier to test, particularly when the dependencies are on interfaces or abstract base classes, which allow for stub or mock implementations to be used in unit tests.

采用DI原则，代码会更干净，当对象被提供其依赖关系时，解耦会更有效。对象不会查找其依赖关系，也不知道依赖关系的位置或类别。因此，你的类变得更容易测试，特别是当依赖关系是在接口或抽象基类上时，这允许在单元测试中使用存根或模拟实现。

DI exists in two major variants: Constructor-based dependency injection and Setter-based dependency injection.

DI 主要存在两种形式：构造器注入和Setter方法注入。

#### Constructor-based Dependency Injection

Constructor-based DI is accomplished by the container invoking a constructor with a number of arguments, each representing a dependency. Calling a static factory method with specific arguments to construct the bean is nearly equivalent, and this discussion treats arguments to a constructor and to a static factory method similarly. The following example shows a class that can only be dependency-injected with constructor injection: