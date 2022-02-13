# Mybatis学习笔记

## 1、简介

### 1.1、什么是mybatis

- ### mybatis是一款优秀的持久层框架

- #### 它支持定制化sql、存储过程以及高级映射

- #### mybatis避免了几乎所有的JDBC代码和手动设置参数以及获取结果集。

## 2、CRUD

### 2.1、namespace

namespace中的包名要和Dao/mapper的包名一致。

### 2.2、select

选择，查询语句；

- id：就是对应的namespace中的方法名；

- resultType：sql语句执行的返回值

- parameterType:参数类型

  1、编写接口

  ```Java
  //获取所有用户
      List<User> getUserList();
  ```

  2、编写对应的mapper中的sql语句

  ```java
  <select id="getUserList" resultType="cn.itcast.pojo.User">
          select  *  from  t_user ;
  </select>
  ```

  3、测试

  ```java
  @Test
      public void test01(){
          SqlSession sqlSession = MybatisUtils.getSqlSession();
          UserDao userMapper = sqlSession.getMapper(UserDao.class);
          User user = userMapper.getUserById(6);
          System.out.println(user);
          sqlSession.close();
      }
  ```

## 3、Insert

```sql
<insert id="addUser" parameterType="cn.itcast.pojo.User">
        insert into t_user
        (id,password,username,name,sex,age,address,qq,email)
        values
        (#{id},#{password},#{username},#{name},#{sex},#{age},#{address},#{qq},#{email})
</insert>
```

## 4、update

```sql
<update id="updateUser" parameterType="cn.itcast.pojo.User">
        update t_user t set
        name = #{name},
        password = #{password},
        username = #{username},
        sex = #{sex},
        age = #{age},
        address = #{address},
        qq = #{qq},
        email = #{email}
        where id = #{id}
    </update>
```

## 5、delete

```sql
<delete id="deleteUser" parameterType="int">
        delete from t_user where id = #{id}
</delete>
```

## 6、万能的map

假如，我们的实体类，或者数据库中的表，字段或者参数过多，我们应当考虑使用map

## 7、配置解析

### 7.1 核心配置文件

#### 		mybatis-config.xml

#### 		mybatis的配置文件包含了会深深影响Mybatis行为的设置和信息

- configuration（配置）

  - properties（属性）

  - settings（设置）

  - typeAliases（类型别名）

  - typeHandlers（类型处理器）

  - objectFactory（对象工厂）

  - plugins（插件）

  - environments（环境配置）

    - environment（环境变量）
      - transactionManager（事务管理器）
      - dataSource（数据源）

  - databaseIdProvider（数据库厂商标识）

  - mappers（映射器）

    

### 7.2、环境配置（environments）

Mybatis可以配置成适应多种环境

不过要记住：尽管可以配置多个环境，但每个sqlsessionfactory实例只能选择一种环境

mybatis默认的事务管理器就是JDBC，连接池：pooled

### 7.3、属性（properties）

我们可以通过properties属性来实现引用配置文件

这些属性都是可外部配置且动态替换的，既可以在典型的java属性文件中配置，亦可通过properties元素的子元素来传递

```xml
<property name="driver" value="com.mysql.jdbc.Driver"/>
<property name="url" value="jdbc:mysql://localhost:3306/basic?useSSL=true&amp;useUnicode=true&amp;characterEncoding=UTF-8"/>
<property name="username" value="root"/>
<property name="password" value="123456"/>
```

### 7.4、别名

-   类型别名是为java类型设置一个短的名字

- 存在的意义仅在于用来减少类完全限定名的冗余

  ```
  <typeAliases>
          <typeAlias type="cn.itcast.pojo.User" alias="User"/>
  </typeAliases>
  ```


## 8、映射器（mappers）

mapperregistry:注册绑定我们的mapper文件。

方式一

```
<mappers>
        <mapper resource="cn/itcast/dao/mapper/UserMapper.xml"/>
</mappers>
```

方式二

```
<mappers>
        <mapper class="cn.itcast.dao.UserDao"/>
</mappers>
```

注意点：

- 接口和它的mapper配置文件必须同名
- 接口和它的mapper配置文件必须在同一个包下

方式三

```
<mappers>
        <package name="cn.itcast.dao"/>
</mappers>
```

注意点：

- 接口和它的mapper配置文件必须同名
- 接口和它的mapper配置文件必须在同一个包下

## 9、日志

log4j使用步骤

1. 导包
2. 编写配置文件
3. 使用

## 10、分页

mybatis分页插件，pagehelper

分页插件学习地址：https://pagehelper.github.io/