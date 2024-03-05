# Design Prinsples

## SOLID Prinsples

### Single Responsibility Principle(SRP)

单一职责原则：一个类应该只负责一项职责，如果一个类承担多个职责，要视情况拆分

### Open-Closed Principle(OCP)

开放封闭原则：软件实体（类、模块、函数等）应该对扩展开放，对修改封闭，即通过扩展来实现变化，而不是通过修改已有的代码来实现

### Liskov Substitution Principle(LSP)

里氏替换原则：子类必须能够替换掉它们的基类，并且应用在原有的基类运行良好，可以理解为子类可以扩展父类的行为，但是不能改变父类的行为

父类方法的行为被改变有以下几种类型：

1. **功能性行为的改变**:如果子类重写的方法改变了父类方法的基本功能，那么就可以说改变了父类方法的行为

    _例子_ 父类有一个方法是用来添加元素到集合中，而子类重写这个方法时，改为删除集合中的元素

2. **非功能性行为的改变**:如果子类重写的方法改变了父类方法的非功能性行为，比如性能、安全性、可用性等，那么也可以说改变了父类方法的行为

    _例子_ 父类方法在一定的时间复杂度下完成任务，而子类重写的方法大大增加了时间复杂度，那么就改变了父类方法的行为

3. **前置条件和后置条件的改变**:如果子类重写的方法改变了父类方法的前置条件或后置条件，那么也可以说改变了父类方法的行为

    _例子_ 父类方法要求输入的参数不能为null，而子类重写的方法却允许输入参数为null
    _例子_ 父类方法定义为返回一个非空的集合，而子类重写的方法却要求返回的集合必须包含至少一个特定的元素

4. **异常行为的改变**:如果子类重写的方法改变了父类方法可能抛出的异常，那么也可以说改变了父类方法的行为

    _例子_ 父类方法定义为可能抛出一个检查异常，而子类重写的方法却定义为可能抛出一个运行时异常，那么就改变了父类方法的行为

### Interface Segregation Principle(ISP)

接口隔离原则：不应该强迫客户端依赖于它们不使用的接口，即接口应该足够小，不应该包含客户端不需要的方法，或者说类间的依赖关系应该建立在最小的接口上  
这个原则的主要目的是降低类之间的耦合度，使得系统更易于维护和扩展  
在面向对象的设计中，类的依赖关系是通过接口来建立的。如果一个接口包含了太多的方法，那么实现这个接口的类就必须实现所有的方法，即使其中有些方法并不需要。这就导致了类与接口之间的耦合度过高，使得系统难以维护和扩展

### Dependency Inversion Principle(DIP)

依赖倒置原则：高层模块不应该依赖于低层模块，二者都应该依赖于抽象；抽象不应该依赖于具体实现细节，具体实现细节应该依赖于抽象，换句话说，要针对接口编程，不要针对实现编程

## GOF Principle

### Creative design patterns

创建型设计模式  
创建型设计模式主要解决的问题是对象的创建与对象之间的解耦，以及灵活地管理和处理对象的创建过程。这些模式在对象创建方面提供了更加灵活、可扩展和可维护的解决方案，有助于降低系统的耦合度，增强了系统的灵活性和可维护性  

#### 单例模式模式

#### Factory Pattern

工厂模式

```java
// 定义汽车接口
interface Car {
    void drive();
}

// 具体的轿车类
class SedanCar implements Car {
    @Override
    public void drive() {
        System.out.println("Driving Sedan car");
    }
}

// 具体的卡车类
class Truck implements Car {
    @Override
    public void drive() {
        System.out.println("Driving Truck");
    }
}

// 汽车工厂接口
interface CarFactory {
    Car createCar();
}

// 具体的轿车工厂
class SedanCarFactory implements CarFactory {
    @Override
    public Car createCar() {
        return new SedanCar();
    }
}

// 具体的卡车工厂
class TruckFactory implements CarFactory {
    @Override
    public Car createCar() {
        return new Truck();
    }
}

// 客户端代码
public class FactoryPatternExample {
    public static void main(String[] args) {
        // 创建轿车工厂
        CarFactory sedanCarFactory = new SedanCarFactory();
        // 生产轿车
        Car sedanCar = sedanCarFactory.createCar();
        // 驾驶轿车
        sedanCar.drive(); // 输出：Driving Sedan car
        
        // 创建卡车工厂
        CarFactory truckFactory = new TruckFactory();
        // 生产卡车
        Car truck = truckFactory.createCar();
        // 驾驶卡车
        truck.drive(); // 输出：Driving Truck
    }
}
```

#### Abstract Factory Pattern

抽象工厂模式

#### 建造者模式

#### 原型模式

### 结构型设计模式

#### 适配器模式

#### 桥接模式

#### 装饰模式

#### 组合模式

#### 外观模式

#### 享元模式

#### 代理模式

### Behavioral design patterns

#### 责任链模式

#### 命令模式

#### 解释器模式

#### 迭代器模式

#### 中介者模式

#### 备忘录模式

#### 观察者模式

#### 状态模式

#### 策略模式

#### Template Method

**模板方法设计模式**  
它在一个方法中定义了一个算法的骨架，并允许子类为一个或多个步骤提供实现。这让子类可以在不改变算法结构的情况下，重新定义算法的某些步骤  

模板方法模式通常包含以下两个部分：

1. 抽象类：这个类定义了一个模板方法，这个方法包含了一个算法的骨架。这个模板方法可以定义一些默认的行为，也可以定义一些抽象的行为，这些抽象的行为由子类来实现。
2. 具体类：这个类继承自抽象类，并实现了抽象类中定义的抽象行为。这样，具体类就可以在不改变算法结构的情况下，重新定义算法的某些步骤。

```java
abstract class Beverage {
    // 模板方法定义了饮料的制作过程
    public final void prepareBeverage() {
        boilWater();
        brew();
        pourInCup();
        addCondiments();
    }
    
    // 抽象方法，由子类实现具体的冲泡过程
    abstract void brew();
    
    // 抽象方法，由子类实现具体的加调味品过程
    abstract void addCondiments();
    
    // 具体方法，用于烧水
    void boilWater() {
        System.out.println("Boiling water");
    }
    
    // 具体方法，倒入杯中
    void pourInCup() {
        System.out.println("Pouring into cup");
    }
}

class Coffee extends Beverage {
    // 实现冲泡咖啡的具体步骤
    void brew() {
        System.out.println("Brewing coffee");
    }
    
    // 实现加入糖和牛奶的具体步骤
    void addCondiments() {
        System.out.println("Adding sugar and milk");
    }
}

class Tea extends Beverage {
    // 实现冲泡茶的具体步骤
    void brew() {
        System.out.println("Steeping the tea");
    }
    
    // 实现加入柠檬的具体步骤
    void addCondiments() {
        System.out.println("Adding lemon");
    }
}

public class TemplateMethodExample {
    public static void main(String[] args) {
        Beverage coffee = new Coffee();
        coffee.prepareBeverage(); // 输出：Boiling water, Brewing coffee, Pouring into cup, Adding sugar and milk
        
        System.out.println();
        
        Beverage tea = new Tea();
        tea.prepareBeverage(); // 输出：Boiling water, Steeping the tea, Pouring into cup, Adding lemon
    }
}
```

#### 访问者模式
