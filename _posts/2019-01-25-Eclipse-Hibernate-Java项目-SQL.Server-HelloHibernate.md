---
title: "HelloHibernate的建议过程"
excerpt: "使用Eclipse JavaEE和SQL Server 2000，通过Hibernate，写一个最基本的HelloHibernate的Java项目，"
categories:
- Coding
tags:
- Eclipse
- Hibernate
- Java
- SQL Server 2000
- Program
create_at: 2019-01-25
last_modified_at: 2019-01-26
toc: true
toc_label: "文章提纲"
toc_icon: "book-reader"
toc_sticky: true
---

## 安装与配置
* JDK的安装：建议使用JRE 1.8以上；
* SQL Server 2000的安装：建议SQL Server 2000 SP3以上；
  * 主要是简单好用，而且资源到处都找得到。
  * SQL Server的“安全性→身份验证”中必须包括SQL Server验证，必须提供sa用户，不需要密码，否则需要修改Hibernate的配置文件。
* Eclipse的安装：建议是javaee 2018-09以上的版本
  * 配置“Windows→Preferences→Java→Build Path→User Libraries→New”一个“Hibernate3”，再“Add External Jars”就可以把相关的包全部定义在这个变量下面。
  * SQL Server2000的JAR包安装：
    * 去[jTDS](http://jtds.sourceforge.net/)就可以下载到支持SQL Server的JAR包文件，比微软出的SQL Server 2K的JAR包还好（微软的包会报错）。
    * 配置“Windows→Preferences→Java→Build Path→User Libraries→New”一个“jTDS”，再“Add External Jars”就可以把相关的包全部定义在这个变量下面。
  * Hibernate Tools的安装：
    * 可以去JBoss的网站下载完整的安装包；
    * 建议在Eclipse JavaEE中安装，如果在Eclipse Java中安装需要下载许多新的插件，而网络环境不好就安装不成功。

## 开发小结
### 建立项目
* 在Eclipse中创建一个Java项目。
  * 说明：Hibernate不仅用在Web项目中，也可以在Java项目中使用，只是安装建议参考前面的说明；
* 在SQL Server的“企业管理器”中创建一个名字叫“Hibernate”的数据库。
* 在“Hibernate”数据库中创建一个“MESSAGE”的表。
  ```SQL
  CREATE TABLE [dbo].[MESSAGE] (
  	[MESSAGE] [char] (10) COLLATE Chinese_PRC_CI_AS NULL 
      ) ON [PRIMARY]
### 配置项目
* 选中项目，“右键→Properties→Java Build Path→Libraries→Add Library→User Library→Hibernate 3”即可把相关类包纳入到项目中。
* 选中项目，“右键→Properties→Java Build Path→Libraries→Add Library→User Library→jTDS”即可把相关类包纳入到项目中。
### 创建代码
* 创建一个新的类Message
    ```java
    package sample.entity;
    public class Message {
        private String message;
        public Message(String message) {
            this.message = message;}
        public String getMessage() {
            return message;}
        public void setMessage(String message) {
            this.message = message;}
    }
* 创建一个测试类
    ```java
    package sample.entity;
    public class PopulateMessages {

        public static void main(String[] args) {
            SessionFactory factory = new Configuration().configure().buildSessionFactory();
            Session session = factory.openSession();
            session.beginTransaction();

            Message message = new Message("Hibernated");
            session.save(message);
            session.getTransaction().commit();
            session.close();
        }
    }
* 创建一个Hibernate的配置文件：“New→Other→Hibernate Configuration File→hibernate.cfg.xml”
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>
    <!DOCTYPE hibernate-configuration PUBLIC 
        "-//Hibernate/Hibernate Configuration DTD 3.0//EN"
        "http://www.hibernate.org/dtd/hibernate-configuration-3.0.dtd">
    <hibernate-configuration>
    <session-factory name="Hibernate">
        <property name="hibernate.connection.driver_class">net.sourceforge.jtds.jdbc.Driver</property>
        <property name="hibernate.connection.url">jdbc:jtds:sqlserver://127.0.0.1:1433;DatabaseName=hibernate</property>
        <property name="hibernate.connection.username">sa</property>
        <property name="hibernate.dialect">org.hibernate.dialect.SQLServerDialect</property>
        <property name="hibernate.show_sql">true</property>
        <mapping resource="sample/entity/Message.hbm.xml"/>
    </session-factory>
    </hibernate-configuration>
* 创建一个Hibernate的映射文件：“New→Other→Hibernate XML Mapping File”，把多余的文件和目录移除，“Add Class→Message→Finish”就可以了。
    ```xml
    <?xml version="1.0"?>
    <!DOCTYPE hibernate-mapping PUBLIC 
        "-//Hibernate/Hibernate Mapping DTD 3.0//EN"
        "http://hibernate.sourceforge.net/hibernate-mapping-3.0.dtd">
    <!-- Generated 2019-1-23 19:49:53 by Hibernate Tools 3.5.0.Final -->
    <hibernate-mapping>
        <class name="sample.entity.Message" table="MESSAGE">
            <id name="message" type="java.lang.String">
                <column name="MESSAGE" />
                <generator class="assigned" />
            </id>
        </class>
    </hibernate-mapping>
## 执行项目
* 运行PopulateMessages就可以看到结果了。
