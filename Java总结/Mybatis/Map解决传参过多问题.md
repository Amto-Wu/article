

万能的Map

为什么要使用 Map

对于数据库中的一张表，当业务量很大时，一张表中就可能会有许多字段。而当要修改数据时，例如：只需要修改用户名，却要将创建一个对象，并传递到配置文件中，这样无疑增大了代码量。但假如使用 Map ，只需要设置指定的键值，就可以在配置文件中取得·相应的值

在 UsersMapper.xml 中配置如下

```xml
<select id="getUserByMap" parameterType="map" resultType="com.wuliq.pojo.Users">
	select * from mybatis.users where id=#{userid}
</select>
```

并在相应的接口中定义如下方法

```java
/*使用Map获取指定信息*/
Users getUserByMap(Map map);
```

相应测试代码

```java
@Test
public void getUserByMap(){
	SqlSession sqlSession= MybatisUtils.getSqlSession();
	UsersMapper usersMapper=sqlSession.getMapper(UsersMapper.class);
        
	/*创建 HashMap */
	HashMap<String ,Object> hashMap=new HashMap<>();
	hashMap.put("userid",1);
        
	Users users=usersMapper.getUserByMap(hashMap);
	System.out.println(users);
	sqlSession.close();
    }
```



Map使用场景

- Map传递参数，直接在 SQL 中取出 key 即可
- 对象传递参数，直接在 SQL 中取对象的属性即可
- 只有一个基本数据类型参数的情况下，可以直接在 SQL 中取到