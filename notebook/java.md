## java

**Q： 如何判断两个字符串是否相等**

A：



**Q： 如何判断两个float型数据是否相等**

A：



**Q：JDBC操作数据库的步骤 ？** 

A：

1. 注册数据库驱动。 

利用`Class.forName()`方法装载某一个数据库的驱动程序。

语法：`Class.forName("JDBC 驱动程序类")`

使用MySQL的驱动程序:`Class.forName("com.mysql.jdbc.Driver")`

使用JDBC－ODBC桥驱动程序:`Class.forName("sun.jdbc.odbc.JdbcOdbcDriver")`

使用ORACLE的驱动程序:`Class.forName("oracle.jdbc.driver.OracleDriver")`

2. 连接的数据库的地址

不同的数据库连接地址不同，这点需要特别注意：

```java
String ODBCURL = "jdbc:odbc:dbName";

String MySQLURL = "jdbc:mysql://host:port/dbName";

String SQLServerURL = "jdbc:microsoft:sqlserver://host:1433;DatabaseName=dbName";

String oracleURL = "jdbc:oracle:thin:@host:port:dbName";
```

3. 建立数据库连接。 

   ```java
   Connection conn = DriverManager.getConnection(url,Login,password);
   ```

4. 创建一个Statement。 

利用Connection接口的createStatement()方法创建语句对象。

语句对象SQL语句发送到对应的数据库，并获得执行结果

```java
 Statement stmt = conn.createStatement();
```

5. 执行SQL语句。 

   ```java
   String sql = "select * from book";
   
   ResultSet rs = stmt.executeQuery(sql);
   ```

6. 处理结果集。 

   ```java
   while(rs.next())
   
   {
       name = rs.getString(1);   
       score = rs.getFloat(2);
       System.out.println(name+","+score);
    }
   ```

7. 关闭数据库连接。 

    rs.close()
