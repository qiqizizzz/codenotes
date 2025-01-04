# 0、网站

[spring.io](https://spring.io/)



# 一、Maven

## 1.Maven基础

Maven 中的坐标是资源的唯一标识，通过该坐标可以唯一定位资源位置

使用坐标来定义项目或引入项目中需要的依赖。

Maven 坐标主要组成

- `groupld`:定义当前Maven项目隶属组织名称(通常是域名反写，例如:com.itheima)
- `artifactld`:定义当前Maven项目名称(通常是模块名称，例如 order-service、goods-service
- `version`:定义当前项目版本号

## 2.依赖配置

依赖:指当前项目运行所需要的jar包，一个项目中可以引入多个依赖，

配置:

1.在 pom.xml中编写`<dependencies>`标签

2.在`<dependencies>`标签中 使用`<dependency>`引入坐标

3.定义坐标的 `groupld`，`artifactld`，`version`

4.点击刷新按钮，引入最新加入的坐标

```xml
<dependencies>
<dependency>
<groupld>ch.gos.logback</groupld>
<artifactld>logback-classic</artifactld>
<version>1.2.3</version>
</dependency>
</dependencies>
```

**注意事项**

如果引入的依赖，在本地仓库不存在，将会连接远程仓库/中央仓库，然后下载依赖。

如果不知道依赖的坐标信息，可以到[mvnrepository.com](https://mvnrepository.com/)中搜索。

### 依赖传递

依赖具有传递性

- 直接依赖:在当前项目中通过依赖配置建立的依赖关系
- 间接依赖:被依赖的资源如果依赖其他资源，当前项目间接依赖其他资源

排除依赖

排除依赖指主动断开依赖的资源，被排除的资源无需指定版本

```xml
<dependency>
	<groupld>com.itheima</groupld>
	<artifactld>maven-projectB</artifactld>
	<version>1.0-SNAPSHOT</version>
    <!--这里是排除依赖 -->
	<exclusions>
		<exclusion>
			<groupld>junit</groupld>
			<artifactld>junit</artifactld>
		</exclusion>
	</exclusions>
    <!--这里是排除依赖 -->
</dependency>
```

起步依赖:
spring-boot-starter-web:包含了web应用开发所需要的常见依赖，
spring-boot-starter-test:包含了单元测试所需要的常见依赖。
官方提供的starter: https://docs.spring.io/spring-boot/docs/2.7.4/reference/htmlsingle/#using.build-systems.starters

### 依赖范围

依赖的jar包，默认情况下，可以在任何地方使用。可以通过`<scope>..</scope>`设置其作用范围

作用范围:

- 主程序范围有效。(main文件夹范围内)
- 测试程序范围有效。(test文件夹范围内)
- 是否参与打包运行。(package指令范围内)

```xml
<!--实例 -->
<dependency>
	<groupld>junit</groupld>
	<artifactld>iunit</artifactld>
	<version>4.10</version>
	<scope>test</scope>
</dependency>
```

| scope值       | 主程序 | 测试程序 | 打包(运行) | 范例          |
| ------------- | ------ | -------- | ---------- | ------------- |
| compile(默认) | Y      | Y        | Y          | `log4j`       |
| test          | -      | Y        | -          | `junit`       |
| provided      | Y      | Y        | -          | `servlet-api` |
| runtime       | -      | Y        | Y          | `jdbc驱动`    |

## 3.生命周期

生命周期阶段

- clean:移除上一次构建生成的文件
- compile:编译项目源代码
- test:使用合适的单元测试框架运行测试(`junit`)
- package:将编译后的文件打包，如:jar、war等
- install:安装项目到本地仓库

**注意**：在同一套生命周期中，当运行后面的阶段时，前面的阶段都会运行

# 二、HTTP协议

概念:`Hyper Text Transfer Protocol`，超文本传输协议，规定了浏览器和服务器之间数据传输的规则。

特点:

1.基于TCP协议：面向连接，安全

2.基于请求-响应模型的：一次请求对应一次响应

3.HTTP协议是无状态的协议:对于事务处理没有记忆能力。每次请求-响应都是独立的。

- 缺点:多次请求间不能共享数据。
- 优点:速度快

# 三、请求响应

请求响应:

- 请求(`HttpServletRequest`):获取请求数据
- 响应(`HttpServletResponse`):设置响应数据
- BS架构:Browser/Server，浏览器/服务器架构模式。客户端只需要浏览器，应用程序的逻辑和数据都存储在服务端。
- CS架构:Client/Server，客户端/服务器架构模式。

> 工具：postman

## 1.简单参数

**1.原始方式**
在原始的web程序中，获取请求参数，需要通过`HttpServetRequest` 对象手动获取。

```java
package com.qiqizizzz.demo2.Control;

import jakarta.servlet.http.HttpServletRequest;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class hello {
    @RequestMapping("/hello")
    public String Hello(HttpServletRequest request) {
        //获取请求参数
        String name = request.getParameter("name");
        String ageStr = request.getParameter("age");
        //返回结果
        int age=Integer.parseInt(ageStr);
        System.out.println("name="+name+",age="+age);
        return "OK!";
    }
}

/*在postman中输入http://localhost:8080/hello?name=Tom&age=10以得到参数*/
```

**2.SpringBoot方式**

```java
package com.qiqizizzz.demo2.Control;

import jakarta.servlet.http.HttpServletRequest;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class hello {
    @RequestMapping("/hello")
    public String Hello(String name,int age) {
        //返回结果
        System.out.println("name="+name+",age="+age);
        return "OK!";
    }
}
/*在postman中输入http://localhost:8080/hello?name=Tom&age=10以得到参数*/
```

简单参数:如果方法形参名称与请求参数名称不匹配，可以使用 @RequestParam 完成映射。

```java
@RequestMapping("/hello")
    public String hello(@RequestParam(name="name")String username,Integer age){
        System.out.println(username + ":" + age);
        return "OK";
    }
```

**注意事项**
`@RequestParam`中的required属性默认为true，代表该请求参数必须传递，如果不传递将报错。如果该参数是可选的，可以将required属性设置为false。

```java
@RequestMapping("/hello")
    public String simpleParam(@RequestParam(name="name",required = false)String username,Integer age){
        System.out.println(username + ":" + age);
        return "OK";
    }
```

## 2.实体参数

复杂实体对象:请求参数名与形参对象属性名相同，按照对象层次结构关系即可接收嵌套POJO属性参数。

```java
package com.qiqizizzz.demo2.Control;

import com.qiqizizzz.demo2.pojo.user;
import jakarta.servlet.http.HttpServletRequest;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class RequestControll {
    //实体参数
    @RequestMapping("/simplepojo")
    public String simplepojo(user users){
        System.out.println(users);
        return "OK";
    }
}
```

```java
package com.qiqizizzz.demo2.pojo;

public class user {
    private String name;
    private int age;

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    @Override
    public String toString() {
        return "user{" +
                "name='" + name + '\'' +
                ", age=" + age +
                '}';
    }
}
```

## 3.数组集合参数

数组参数:请求参数名与形参数组名称相同且请求参数为多个，定义数组类型形参即可接收参数

```java
@RequestMapping("/arrayparam")
    public String arrayparam(String[] hobby){
            System.out.println(Arrays.toString(hobby));
        return "OK";
    }
/*在postman中输入http://localhost:8080/arrayparam?hobby=game&hobby=java&hobby=sing*/
```

集合参数:请求参数名与形参集合名称相同且请求参数为多个，`@RequestParam` 绑定参数关系

```java
@RequestMapping("/listparam")
    public String listparam(@RequestParam List<String> hobby){
        System.out.println(hobby);
        return "OK";
    }
/*在postman中输入http://localhost:8080/listparam?hobby=game&hobby=java&hobby=sing*/
```

## 4.日期参数

日期参数:使用 `@DateTimeFormat`注解完成日期参数格式转换

```java
@RequestMapping("/dateparam")
    public String dateparam(@DateTimeFormat(pattern = "yyyy-MM-dd HH:mm:ss")LocalDateTime updateTime){
        System.out.println(updateTime);
        return "OK";
    }
/*在postman中输入http://localhost:8080/dateparam?updateTime=2024-12-17 10:00:05*/
```

## 5.Json参数

JSON参数:JSON数据**键名**与形参对象**属性名**相同，定义POJO类型形参即可接收参数，需要使用 `@RequestBody` 标识

```java
@RequestMapping("/jsonParam")
    public String jsonParam(@RequestBody user users){
        System.out.println(users);
        return "OK";
    }
/*在postman中输入http://localhost:8080/jsonParam*/
```

```json
{
    "name":"Tom",
    "age":10,
    "address":{
        "province":"beijing",
        "city":"beijing"
    }
}
```

## 6.路径参数

路径参数:通过请求URL直接传递参数，使用1..)来标识该路径参数，需要使用 `@PathVariable` 获取路径参数

```java
//一个路径参数的获取
@RequestMapping("/path/{id}")
    public String pathParam(@PathVariable Integer id)
    {
        System.out.println(id);
        return "OK";
    }
/*在postman中输入http://localhost:8080/path/2*/
```

```java
//多个路径参数的获取
@RequestMapping("/path/{id}/{name}")
    public String pathParam2(@PathVariable Integer id,@PathVariable String name)
    {
        System.out.println(id+":"+name);
        return "OK";
    }
/*在postman中输入http://localhost:8080/path/2/Tom*/
```

## 7.@ResponseBody

`@ResponseBody`

- 类型:方法注解、类注解
- 位置:Controller方法上/类上
- 作用:将方法返回值直接响应，如果返回值类型是 实体对象/集合，将会转换为JSON格式响应
- 说明:`@RestController=@Controller+@ResponseBody`;

统一响应结果:

Result(Code、msg、data)

## 8.分层解耦

分层解耦概念：

内聚:软件中各个功能模块内部的功能联系。

耦合:衡量软件中各个层/模块之间的依赖、关联的程度。

软件设计原则:高内聚低耦合。

### 8.1 三层架构

controller:控制层，接收前端发送的请求，对请求进行处理，并响应数据。

service:业务逻辑层，处理具体的业务逻辑。

dao:数据访问层(Data Access Object)(持久层)，负责数据访问操作，包括数据的增、删、改、查。



### 8.2 IOC&DI&bean

控制反转: Inversion Of Control，简称IOC。对象的创建控制权由程序自身转移到外部(容器)，这种思想称为控制反转。

依赖注入:Dependency Injection，简称DI。容器为应用程序提供运行时，所依赖的资源，称之为依赖注入。

Bean对象:IOC容器中创建、管理的对象，称之为bean。

**bean的声明**

要把某个对象交给IOC容器管理，需要在对应的类上加上如下注解之一:

| 注解        | 说明                 | 位置                                          |
| ----------- | -------------------- | --------------------------------------------- |
| @Component  | 声明bean的基础注解   | 不属于以下三类时，用此注解                    |
| @Controller | @Component的衍生注解 | 标注在控制器类上                              |
| @Service    | @Component的衍生注解 | 标注在业务类上                                |
| @Repository | @Component的衍生注解 | 标注在数据访问类上(由于与mybatis整合，用的少) |

**注意事项**

- 声明bean的时候，可以通过value属性指定bean的名字，如果没有指定，默认为类名首字母小写。
- 使用以上四个注解都可以声明bean，但是在springboot集成web开发中，声明控制器bean只能用`@Controller`.
- Bean组件扫描
  - 前面声明bean的四大注解，要想生效，还需要被组件扫描注解`@ComponentScan`扫描。
  - `@Componentscan`注解虽然没有显式配置，但是实际上已经包含在了启动类声明注解 `@SpringBootApplication`中，默认扫描的范围是启动类所在包及其子包。

### 8.3 `@Autowired` 相关

`@Autowired` 是 Spring Framework 中的一个注解，用于自动注入依赖关系。它可以用来自动将 Spring 容器中的 bean 注入到类的字段、构造函数或方法中，从而简化了依赖注入（DI）的过程。

> 它是 Spring 用于自动注入依赖的注解。它能够自动将 Spring 容器中的 bean 注入到类的字段、构造函数或方法中，从而减少了手动管理依赖的代码量。你可以通过该注解让 Spring 自动完成依赖注入的工作，从而提高开发效率。

####  1. 原理

> **自动注入的原理：**

- **Spring IoC 容器**：当你启动一个 Spring Boot 应用时，Spring 会启动其 Inversion of Control（IoC）容器，负责管理所有的 bean。
- **扫描组件**：Spring 会扫描带有 `@Component`、`@Service`、`@Repository` 或 `@Controller` 注解的类，这些类会被注册为 bean。
- **依赖注入**：`@Autowired` 注解会告诉 Spring 容器去查找并注入匹配类型的 bean。例如，如果你有一个 `MyRepository` 类型的 bean，Spring 会自动注入该类型的实例。

> **自动注入的工作流程：**

当 Spring 启动时，它会扫描所有类并创建 bean 实例。如果一个类标记了 `@Autowired`，Spring 会：

1. 查找 Spring 容器中是否有与字段类型、构造函数参数或方法参数匹配的 bean。
2. 如果找到匹配的 bean，它会将该 bean 注入到目标类的相应字段、构造函数或方法中。
3. 如果没有找到匹配的 bean，Spring 会抛出异常，除非该依赖项是可选的。

> **传统的手动实例化方式**

如果没有使用 Spring 或依赖注入，`MyService` 类会像这样手动实例化 `MyRepository`：

```java
public class MyService {
    private MyRepository myRepository;

    public MyService() {
        // 手动创建 MyRepository 的实例
        this.myRepository = new MyRepository();  // 直接实例化
    }

    public void processData() {
        myRepository.save("Some data");
    }
}
/*在这个例子中，MyService 自己负责创建 MyRepository 的实例，也就是说，MyService 需要知道如何实例化 MyRepository（通过 new MyRepository()）。这种做法使得 MyService 和 MyRepository 之间产生了强耦合，MyService 需要知道 MyRepository 的具体实现细节。*/
```

#### 2. **自动注入字段**

最常见的用法是直接在类的字段上使用 `@Autowired` 注解，Spring 会自动将适当的 bean 注入到该字段中。

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class MyService {

    @Autowired
    private MyRepository myRepository;  // 自动注入 MyRepository 类的实例

    public void doSomething() {
        // 使用 myRepository 执行一些操作
    }
}
```

#### 3. **自动注入构造函数**

`@Autowired` 也可以应用于构造函数，这是一种推荐的做法，特别是当需要确保所有依赖都在对象创建时被注入时。这也是一种更加显式的依赖注入方式。

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class MyService {

    private final MyRepository myRepository;

    @Autowired
    public MyService(MyRepository myRepository) {
        this.myRepository = myRepository;  // 通过构造函数注入
    }

    public void doSomething() {
        // 使用 myRepository 执行一些操作
    }
}
```

#### 4. **自动注入方法**

`@Autowired` 还可以用于方法，通常是 setter 方法，用于在对象创建后进行依赖注入。

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

@Service
public class MyService {

    private MyRepository myRepository;

    @Autowired
    public void setMyRepository(MyRepository myRepository) {
        this.myRepository = myRepository;  // 通过 setter 方法注入
    }

    public void doSomething() {
        // 使用 myRepository 执行一些操作
    }
}
```



#### 5. 多个Bean注入

`@Autowired`注解，默认是按照类型进行，如果存在多个相同类型的bean，将会报出错误。

通过以下几种方案来解决:

`@Primary`

```java
@Primary
@Service
public class EmpServiceAimplements Empservice {
```

`@Qualifier`

```java
@RestController
public class EmpController {
@Autowired
@Qudfifier("empServiceA")
private EmpService empService;
```

`@Resource`

```java
@RestController
public class Empcontroller {
@Resource(name="empServiceB")
private EmpService empService;
```

#### 6. **`@Autowired` 与构造器注入**

构造函数注入是一种更推荐的方式，因为它能确保所有依赖在类实例化时就已经被注入，并且使得依赖关系更加明确且不可更改。

```java
@Service
public class MyService {
    private final MyRepository myRepository;

    @Autowired
    public MyService(MyRepository myRepository) {
        this.myRepository = myRepository;
    }
}
```

## 9.session生命周期

在Web应用中，**session的生命周期**通常是从客户端访问应用开始，直到会话结束。具体来说，session的生命周期可以受到多个因素的影响，常见的生命周期如下：

1. **创建：** session会在用户第一次访问某个Servlet时自动创建。当客户端（比如浏览器）发起请求时，服务器会为该请求创建一个session，并生成一个唯一的session ID，通常保存在浏览器的cookie中（或者通过URL传递）。

2. **有效期：** 一旦session被创建，它会保持有效，直到发生以下一种情况：

   - 用户关闭浏览器（浏览器关闭时，所有关联的session都会被销毁）。这取决于session是否设置了浏览器关闭时自动销毁。
   - session超时：服务器会在一定时间内检查用户是否有活动。如果超过设定的超时时间（如30分钟没有任何请求），服务器会自动销毁该session。

3. **跳转：** 当你从主界面跳转到一个子界面时，**session依然存在**。在整个过程中，session不会被销毁，除非超时或显式地调用`session.invalidate()`来销毁session。所以，即使页面跳转，session仍然保持活动状态，只要在有效期内。

4. **超时设置：** 在Spring Boot等框架中，你可以通过配置文件来设置session的最大超时时间（以分钟为单位）。例如，在`application.properties`或`application.yml`中配置：

   ```properties
   server.servlet.session.timeout=30m
   ```

   上面的配置表示session在30分钟没有活动时将会过期。

5. **销毁：** 当用户退出登录，或者显式调用了`session.invalidate()`时，session会被销毁，且所有与该session相关的数据都会被清除。

# 四、MyBatis

MyBatis 是一款优秀的持久层框架，它支持自定义 SQL、存储过程以及高级映射。

MyBatis 免除了几乎所有的 JDBC 代码以及设置参数和获取结果集的工作。

MyBatis 可以通过简单的 XML 或注解来配置和映射原始类型、接口和 Java POJO（Plain Old Java Objects，普通老式 Java 对象）为数据库中的记录。

官网:[mybatis.org](https://mybatis.org/mybatis-3/zh_CN/index.html)

## 1.JDBC相关

JDBC:(Java DataBase Connectivity)，就是使用Java语言操作关系型数据库的一套API。

> 本质

- sun公司官方定义的一套操作所有关系型数据库的规范，即接口。
- 各个数据库厂商去实现这套接口，提供数据库驱动iar包。
- 我们可以使用这套接口(JDBC)编程，真正执行的代码是驱动Jar包中的实现类

```xml
<dependency>
	<groupId>mysql</groupId>
	<artifactId>mysql-connector-java</artifactId>
	<scope>runtime</scope>
</dependency>
```

## 2.数据库连接池

数据库连接池是个容器，负责分配、管理数据库连接(Connection)

它允许应用程序重复使用一个现有的数据库连接，而不是再重新建立一个释放空闲时间超过最大空闲时间的连接，来避免因为没有释放连接而引起的数据库连接遗漏。

> 优势

- 资源重用
- 提升系统响应速度
- 避免数据库连接遗漏

相关产品：

- Druid(德鲁伊)

  Druid连接池是阿里巴巴开源的数据库连接池项目

  功能强大，性能优秀，是lava语言最好的数据库连接池之一

**切换Druid数据库连接池**

官方地址:https://github.com/alibaba/druid/tree/master/druid-spring-boot-starter

```xml
<dependency>
<groupld>com.alibaba</groupld>
<artifactld>druid-spring-boot-starter</artifactld>
<version>1.2.8</version>
</dependency>
<!--pom.xml-->
```

```properties
spring.datasource.driver-class-name=com.mysql.cj.jdbc.Drivel
spring.datasource.url=jdbc:mysql://localhost:3306/mybatis
spring.datasource.username=root
spring.datasource.password=1234
# application.properties
```

## 3.lombok

Lombok是一个实用的Java类库，能通过注解的形式自动生成构造器、getter/setter、equals、hashcode、tostring等方法，并可以自动化生成日志变量，简化java开发、提高效率。

| 注解                    | 作用                                                         |
| ----------------------- | ------------------------------------------------------------ |
| @Getter/@Setter         | 为所有的属性提供get/set方法                                  |
| @ToString               | 会给类自动生成易阅读的 toString 方法                         |
| @EqualsAndHashCode      | 根据类所拥有的非静态字段自动重写 equals 方法和 hashcode 方法 |
| **@Data**               | 提供了更综合的生成代码功能(`@Getter+@Setter+@ToString+@EqualsAndHashcode`) |
| **@NoArgsConstructor**  | 为实体类生成无参的构造器方法                                 |
| **@AllArqsConstructor** | 为实体类生成除了static修饰的字段之外带有各参数的构造器方法   |

使用时需要引入依赖

```xml
</dependency>
	<groupld>org.projectlombok</groupld>
	<artifactld>lombok</artifactld>
</dependency>
```

## 4.`@Mapper`、`@Select`

**`@Mapper`注解**

`@Mapper` 是 MyBatis 中的一个注解，用来标记一个接口是一个 MyBatis 映射器（Mapper）。在 MyBatis 中，Mapper 接口用于定义数据库查询方法，而不需要手动编写 SQL 查询的实现。通过这个注解，MyBatis 会自动将该接口注册为一个 Mapper，并将接口方法和相应的 SQL 映射起来。

**作用：**

- `@Mapper` 注解让 MyBatis 知道 `UserMapper` 是一个 Mapper 接口，MyBatis 会自动为其创建代理对象，从而使得你可以通过接口方法调用数据库查询操作。
- 在 Spring Boot 中，你通常还需要使用 `@MapperScan` 注解（或者在 `application.properties` 中配置扫描路径）来让 Spring 自动扫描所有的 Mapper 接口。

**`@Select` 注解**

`@Select` 是 MyBatis 提供的注解，用来标识一个 SQL 查询操作。它会将标注的方法与指定的 SQL 查询语句关联起来，从而使得调用该方法时，MyBatis 会执行相应的 SQL 查询。

```java
@Mapper
public interface UserMapper {
    @Select("SELECT * FROM employee where employee_name=#{employee_name} and password=#{password}")
    User getEmployeeByNameAndPassword(String employee_name, String password);
}
/*你不需要手动“重写”接口方法，因为 MyBatis 会通过 动态代理 自动实现这些方法。你只需在接口中声明方法和对应的 SQL 查询，MyBatis 会为你生成实现类并执行 SQL 查询，处理结果并返回数据。通过这种方式，MyBatis 简化了数据库操作，减少了手动编写 SQL 执行代码的工作量。*/
```

**在这个例子中：**

- `@Select` 注解的 SQL 查询语句是 `SELECT * FROM employee WHERE employee_name=#{employee_name} AND password=#{password}`。
- `#{employee_name}` 和 `#{password}` 是 SQL 中的占位符，表示从方法参数中获取这两个值，并将它们注入到 SQL 语句中。这些占位符会被 MyBatis 自动替换为传入的参数值。

例如，如果你调用 `getEmployeeByNameAndPassword("JohnDoe", "123456")`，MyBatis 会将 SQL 查询变成：

```sql
SELECT * FROM employee WHERE employee_name='JohnDoe' AND password='123456'
```
