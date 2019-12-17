---
title: Getting start Mybatis with Spring xml setting
categories:
- java
- mybatis
tags: mybatis
layout: post
---

#### Add dependency


```xml

<!-- MyBatis -->
<dependency>
	<groupId>org.mybatis</groupId>
	<artifactId>mybatis</artifactId>
	<version>3.5.2</version>
</dependency>

<dependency>
	<groupId>org.mybatis</groupId>
	<artifactId>mybatis-spring</artifactId>
	<version>2.0.3</version>
</dependency>

```

#### Building SqlSessionFactory from XML

add SqlSessionFactory bean in applicationContext.xml

```xml

<bean id="dataSource" class="org.apache.commons.dbcp2.BasicDataSource">
	<property name="driverClassName" value="${jdbc.driver}" />
	<property name="url" value="${jdbc.url}" />
	<property name="username" value="${jdbc.username}" />
	<property name="password" value="${jdbc.password}" />
</bean>

<bean id="sqlSessionFactory" class="org.mybatis.spring.SqlSessionFactoryBean">
	<property name="dataSource" ref="dataSource"></property>
	<property name="configLocation" value="classpath:mybatis-config.xml"></property>

</bean>

<bean id="sqlSession" name="sqlSession" class="org.mybatis.spring.SqlSessionTemplate" destroy-method="clearCache">
	<constructor-arg name="sqlSessionFactory" ref="sqlSessionFactory" />
</bean>

<!--   Use  sqlSession -->
<bean id="userDAO" class="me.*.UserDAO">
	<constructor-arg name="sqlSession" ref="sqlSession"></constructor-arg>
</bean>

```

#### Add mybatis-config.xml

create mybatis-config file in resources folder


```xml

<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE configuration
  PUBLIC "-//mybatis.org//DTD Config 3.0//EN"
  "http://mybatis.org/dtd/mybatis-3-config.dtd">
<configuration>
	<typeAliases>
		<typeAlias type="me.*.UserVO" alias="user"></typeAlias>
	</typeAliases>
	<mappers>
		<mapper resource="mappings/example.xml" />
	</mappers>
</configuration>

```

#### Add mappings

create a mappings folder in classpath(resources)


```xml

<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE mapper PUBLIC "-//mybatis.org//DTD Mapper 3.0//EN"
  "http://mybatis.org/dtd/mybatis-3-mapper.dtd">

<mapper namespace="UserDAO">

 	<select id="getUserInfo" parameterType="user" resultType="user">
		SELECT
		id,
		user_id
		FROM users
		WHERE id = #{id}
	</select>

</mapper>

```

#### Java Source

```java

public class UserDAO implements IUserDAO {
	private SqlSession sqlSession;

	public UserDAO(SqlSessionTemplate sqlSession) {
		this.sqlSession = sqlSession;
	}

	public UserVO getUserInfo(UserVO vo) {
		return sqlSession.selectOne("UserDAO.getUserInfo", vo);
	}
}

```