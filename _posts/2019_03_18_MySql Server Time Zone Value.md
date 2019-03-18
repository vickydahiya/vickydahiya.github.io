---
layout: post
title:  "MySql Server Time Zone Value"
---

With the day light time saving started this week, explore a new issue with the current mysql versions 5.7.22
After the server restart, running the spring boot application has started throwing the exception '
java.sql.SQLException: The server time zone value 'PDT' is unrecognized or represents more than one time zone. You must configure either the server or JDBC driver (via the serverTimezone configuration property) to use a more specifc time zone value if you want to utilize time zone support.
'

Complete stack trace is here

java.sql.SQLException: The server time zone value 'PDT' is unrecognized or represents more than one time zone. You must configure either the server or JDBC driver (via the serverTimezone configuration property) to use a more specifc time zone value if you want to utilize time zone support.
	at com.mysql.cj.jdbc.exceptions.SQLError.createSQLException(SQLError.java:129)
	at com.mysql.cj.jdbc.exceptions.SQLError.createSQLException(SQLError.java:97)
	at com.mysql.cj.jdbc.exceptions.SQLError.createSQLException(SQLError.java:89)
	at com.mysql.cj.jdbc.exceptions.SQLError.createSQLException(SQLError.java:63)
	at com.mysql.cj.jdbc.exceptions.SQLError.createSQLException(SQLError.java:73)
	at com.mysql.cj.jdbc.exceptions.SQLExceptionsMapping.translateException(SQLExceptionsMapping.java:76)
	at com.mysql.cj.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:835)
	at com.mysql.cj.jdbc.ConnectionImpl.<init>(ConnectionImpl.java:455)
	at com.mysql.cj.jdbc.ConnectionImpl.getInstance(ConnectionImpl.java:240)
	at com.mysql.cj.jdbc.NonRegisteringDriver.connect(NonRegisteringDriver.java:199)
	at com.zaxxer.hikari.util.DriverDataSource.getConnection(DriverDataSource.java:136)
	at com.zaxxer.hikari.pool.PoolBase.newConnection(PoolBase.java:369)
	at com.zaxxer.hikari.pool.PoolBase.newPoolEntry(PoolBase.java:198)
	at com.zaxxer.hikari.pool.HikariPool.createPoolEntry(HikariPool.java:467)
	at com.zaxxer.hikari.pool.HikariPool.checkFailFast(HikariPool.java:541)
	at com.zaxxer.hikari.pool.HikariPool.<init>(HikariPool.java:115)
	at com.zaxxer.hikari.HikariDataSource.getConnection(HikariDataSource.java:112)
	at com.zaxxer.hikari.HikariDataSource$$FastClassBySpringCGLIB$$eeb1ae86.invoke(<generated>)
	at org.springframework.cglib.proxy.MethodProxy.invoke(MethodProxy.java:218)
	at org.springframework.aop.framework.CglibAopProxy$CglibMethodInvocation.invokeJoinpoint(CglibAopProxy.java:749)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:163)
	at org.springframework.aop.support.DelegatingIntroductionInterceptor.doProceed(DelegatingIntroductionInterceptor.java:136)
	at org.springframework.aop.support.DelegatingIntroductionInterceptor.invoke(DelegatingIntroductionInterceptor.java:124)
	at org.springframework.aop.framework.ReflectiveMethodInvocation.proceed(ReflectiveMethodInvocation.java:186)
	at org.springframework.aop.framework.CglibAopProxy$DynamicAdvisedInterceptor.intercept(CglibAopProxy.java:688)
	at com.zaxxer.hikari.HikariDataSource$$EnhancerBySpringCGLIB$$af8bf53e.getConnection(<generated>)
	at org.springframework.jdbc.datasource.DataSourceUtils.fetchConnection(DataSourceUtils.java:157)
	at org.springframework.jdbc.datasource.DataSourceUtils.doGetConnection(DataSourceUtils.java:115)
	at org.springframework.jdbc.datasource.DataSourceUtils.getConnection(DataSourceUtils.java:78)
	at org.springframework.jdbc.support.JdbcUtils.extractDatabaseMetaData(JdbcUtils.java:319)
	at org.springframework.jdbc.support.JdbcUtils.extractDatabaseMetaData(JdbcUtils.java:356)
	at org.springframework.boot.autoconfigure.orm.jpa.DatabaseLookup.getDatabase(DatabaseLookup.java:73)
	at org.springframework.boot.autoconfigure.orm.jpa.JpaProperties.determineDatabase(JpaProperties.java:142)
	at org.springframework.boot.autoconfigure.orm.jpa.JpaBaseConfiguration.jpaVendorAdapter(JpaBaseConfiguration.java:113)
	at org.springframework.boot.autoconfigure.orm.jpa.HibernateJpaConfiguration$$EnhancerBySpringCGLIB$$889154a7.CGLIB$jpaVendorAdapter$4(<generated>)
	at org.springframework.boot.autoconfigure.orm.jpa.HibernateJpaConfiguration$$EnhancerBySpringCGLIB$$889154a7$$FastClassBySpringCGLIB$$2e0d7e9c.invoke(<generated>)
	at org.springframework.cglib.proxy.MethodProxy.invokeSuper(MethodProxy.java:244)
	at org.springframework.context.annotation.ConfigurationClassEnhancer$BeanMethodInterceptor.intercept(ConfigurationClassEnhancer.java:363)
	at org.springframework.boot.autoconfigure.orm.jpa.HibernateJpaConfiguration$$EnhancerBySpringCGLIB$$889154a7.jpaVendorAdapter(<generated>)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.springframework.beans.factory.support.SimpleInstantiationStrategy.instantiate(SimpleInstantiationStrategy.java:154)
	at org.springframework.beans.factory.support.ConstructorResolver.instantiate(ConstructorResolver.java:622)
	at org.springframework.beans.factory.support.ConstructorResolver.instantiateUsingFactoryMethod(ConstructorResolver.java:456)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.instantiateUsingFactoryMethod(AbstractAutowireCapableBeanFactory.java:1305)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1144)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:555)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:515)
	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:320)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:318)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:199)
	at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:277)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1247)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1167)
	at org.springframework.beans.factory.support.ConstructorResolver.resolveAutowiredArgument(ConstructorResolver.java:857)
	at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:760)
	at org.springframework.beans.factory.support.ConstructorResolver.instantiateUsingFactoryMethod(ConstructorResolver.java:509)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.instantiateUsingFactoryMethod(AbstractAutowireCapableBeanFactory.java:1305)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1144)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:555)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:515)
	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:320)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:318)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:199)
	at org.springframework.beans.factory.config.DependencyDescriptor.resolveCandidate(DependencyDescriptor.java:277)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.doResolveDependency(DefaultListableBeanFactory.java:1247)
	at org.springframework.beans.factory.support.DefaultListableBeanFactory.resolveDependency(DefaultListableBeanFactory.java:1167)
	at org.springframework.beans.factory.support.ConstructorResolver.resolveAutowiredArgument(ConstructorResolver.java:857)
	at org.springframework.beans.factory.support.ConstructorResolver.createArgumentArray(ConstructorResolver.java:760)
	at org.springframework.beans.factory.support.ConstructorResolver.instantiateUsingFactoryMethod(ConstructorResolver.java:509)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.instantiateUsingFactoryMethod(AbstractAutowireCapableBeanFactory.java:1305)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBeanInstance(AbstractAutowireCapableBeanFactory.java:1144)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.doCreateBean(AbstractAutowireCapableBeanFactory.java:555)
	at org.springframework.beans.factory.support.AbstractAutowireCapableBeanFactory.createBean(AbstractAutowireCapableBeanFactory.java:515)
	at org.springframework.beans.factory.support.AbstractBeanFactory.lambda$doGetBean$0(AbstractBeanFactory.java:320)
	at org.springframework.beans.factory.support.DefaultSingletonBeanRegistry.getSingleton(DefaultSingletonBeanRegistry.java:222)
	at org.springframework.beans.factory.support.AbstractBeanFactory.doGetBean(AbstractBeanFactory.java:318)
	at org.springframework.beans.factory.support.AbstractBeanFactory.getBean(AbstractBeanFactory.java:199)
	at org.springframework.context.support.AbstractApplicationContext.getBean(AbstractApplicationContext.java:1105)
	at org.springframework.context.support.AbstractApplicationContext.finishBeanFactoryInitialization(AbstractApplicationContext.java:867)
	at org.springframework.context.support.AbstractApplicationContext.refresh(AbstractApplicationContext.java:549)
	at org.springframework.boot.web.servlet.context.ServletWebServerApplicationContext.refresh(ServletWebServerApplicationContext.java:142)
	at org.springframework.boot.SpringApplication.refresh(SpringApplication.java:775)
	at org.springframework.boot.SpringApplication.refreshContext(SpringApplication.java:397)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:316)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1260)
	at org.springframework.boot.SpringApplication.run(SpringApplication.java:1248)
	at com.sclabs.useraccount.UserAccountApplication.main(UserAccountApplication.java:11)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:62)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:498)
	at org.springframework.boot.devtools.restart.RestartLauncher.run(RestartLauncher.java:49)
Caused by: com.mysql.cj.exceptions.InvalidConnectionAttributeException: The server time zone value 'PDT' is unrecognized or represents more than one time zone. You must configure either the server or JDBC driver (via the serverTimezone configuration property) to use a more specifc time zone value if you want to utilize time zone support.
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:62)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:423)
	at com.mysql.cj.exceptions.ExceptionFactory.createException(ExceptionFactory.java:61)
	at com.mysql.cj.exceptions.ExceptionFactory.createException(ExceptionFactory.java:85)
	at com.mysql.cj.util.TimeUtil.getCanonicalTimezone(TimeUtil.java:132)
	at com.mysql.cj.protocol.a.NativeProtocol.configureTimezone(NativeProtocol.java:2241)
	at com.mysql.cj.protocol.a.NativeProtocol.initServerSession(NativeProtocol.java:2265)
	at com.mysql.cj.jdbc.ConnectionImpl.initializePropsFromServer(ConnectionImpl.java:1319)
	at com.mysql.cj.jdbc.ConnectionImpl.connectOneTryOnly(ConnectionImpl.java:966)
	at com.mysql.cj.jdbc.ConnectionImpl.createNewIO(ConnectionImpl.java:825)
	... 90 common frames omitted


After some research, here is the way to fix the problem:

First step: Make the required changes to your 'application.properties' file (or the file where ever you have defined your datasource url

From
spring.datasource.url=jdbc:mysql://localhost:3306/<dbname>

To 
spring.datasource.url=jdbc:mysql://localhost:3306/<dbname>?useUnicode=true&useJDBCCompliantTimezoneShift=true&useLegacyDatetimeCode=false&serverTimezone=PST8PDT

Replace <dbname> with your DatabaseName
Replease pecific time (PST8PDT) with any of timezone as per your area. Here is the list for US
EST5EDT
CST6CDT
MST7MDT
PST8PDT

Make this change and try to run the server, if you still face the issue, here is the next change needs to be made.

Go to your mysql /etc/my.cnf file and set the following variable
default-time-zone = 'SYSTEM';

[How to find my.cnf on mac/UNIX
Run the following command

$locate my.cnf

If Locate DB will not be available on your mac, you will get the following warning

WARNING: The locate database (/var/db/locate.database) does not exist.
To create the database, run the following command:

  sudo launchctl load -w /System/Library/LaunchDaemons/com.apple.locate.plist

Please be aware that the database can take some time to generate; once
the database has been created, this message will no longer appear.

Run the sudo command as suggested by the warning, give it some time to create the DB for lookup and run the locate command again and it will give you the path like this

/usr/local/Cellar/mysql/5.7.22/.bottle/etc/my.cnf

Reach to the directory and open the my.cnf in vi editor(Or any editor of your choice)

Here are the command

$ vi my.cnf

Once you are on file, type i to enter the insert mode. And set the variable as mentioned earlier

default-time-zone = 'SYSTEM';

The command ZZ (notice that it is in uppercase) will allow you to quit vi and save the edits made to a file.

Once you are back, restart your DB server for the change to be reflected. If you are running the prod server and not possible to restart the DB, you can try following query on you running DB (I have read it somewhere, but didn't test as I have made the other change prior to finding this)

SET GLOBAL time_zone = '-5:00';orSET GLOBAL time_zone = 'SYSTEM';commit; 

Run the command below to verify the new configuration:
SELECT @@session.time_zone;

]
