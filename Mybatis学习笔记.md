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