# spring-study
# spring

## 1.1

* spring是一个轻量级的、非入侵的框架！

* 控制反转（IOC）、面向切面编程（AOP）！

* 支持事物处理、对框架整合支持！

   **spring是一个轻量级的控制反转（IOC）和面向切面编程（AOP）的框架！** 

  

## 1.2组成

![image-20210429112807244](C:\Users\mi\AppData\Roaming\Typora\typora-user-images\image-20210429112807244.png)

## 1.3扩展

基于spring的开发

![image-20210429112920284](C:\Users\mi\AppData\Roaming\Typora\typora-user-images\image-20210429112920284.png)

* springboot
  * 一个快速开发的脚手架。
  * 可快速开发单个微服务。
* springcloud
  * 基于springboot实现的。

**弊端：发展太久，违背了原来的理念！配置繁琐**



# IOC理论推导

 	1. UserDao接口
 	2. UserDaolmpl 实现类
 	3. UserService业务接口
 	4. UserServicelmpl实现业务类

![image-20210429115432805](C:\Users\mi\AppData\Roaming\Typora\typora-user-images\image-20210429115432805.png)

* IOC(控制反转)将控制权交还给用户，不需要每次修改代码（不用管理对象的创建，由用户选择创建），增加程序灵活性

  **这种思想从根本解决问题，降低耦合，可以更加专注在业务的实现**

* 使用set注入降低程序主动性，将控制权交由用户决定**(IOC控制反转)**

  ```java
  //这里使用的是set注入使程序不具有主动性（意思就是我提供了几个方法你决定用哪个）--
  //--（之前的是我有几个方法我只能给你new一个需要用其他的需要重新修改代码new另一个）
  public void setUserDao(UserDao userDao){
      this.userDao=userDao;
  }
  ```

# IOC创建对象的方式

1. 使用无参构造创建对象，默认

   ```xml
    <!--  无参构造  -->
       <bean id="user" class="com.island.pojo.User">
           <!--   这里相当于注入一个name（给她赋值）     -->
           <property name="name" value="张三"/>
       </bean>
   ```

2. 也可以使用有参构造创建对象，（通过下标的方式进行赋值）

   2.1通过下标进行注入（还不会下标是怎么标的）

   ```xml
   <bean id="user" class="com.island.pojo.User">
       <constructor-arg index="0" value="张阿斯蒂芬三"/>
   </bean>
   ```

   2.2通过type类型进行注入 （如果两个参数都是同一类型如int或string就不行了）

   ```xml
   <bean id="user" class="com.island.pojo.User">
       <constructor-arg type="java.lang.String" value="莫得感情"/>
   </bean>
   ```

   2.3直接参数名注入

   ```xml
   <bean id="user" class="com.island.pojo.User">
       <constructor-arg name="name" value="参数名注入"/>
   </bean>
   ```
