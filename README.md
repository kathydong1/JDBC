1.DriverManager类：用语跟踪可用的JDBC驱动程序并产生数据库连接。

2.Connection接口：用于取得数据库信息、生成数据库语句，并管理数据库事务。

3.Statement接口：用于在基层连接上运行SQL语句，并且生成一个结果集。Statement有两个子接口：PreparedStatement和CallableStatement。
         PreparedStatement提供了可以与查询信息一起预编译的一种语句类型。
         CallableStatement从PreparedStatement继承而来，它用来封装数据库中存储过程的执行。

4.ResultSet接口：用于访问SQL查询返回的数据。当读取结果时，可以使用它的next()方法依次定位每一行数据，然后用相应的get方法读取数据。
加载驱动Class.forName(driverClass)
//加载MySql驱动
   Class.forName("com.mysql.jdbc.Driver")
//加载Oracle驱动
   Class.forName("oracle.jdbc.driver.OracleDriver")
获得数据库连接：
   Connection conn=DriverManager.getConnection("jdbc:mysql://127.0.0.1:3306/imooc", "root", "root");
写入SQL语句,prepareStatement中用？表示变量，设置值时用setInt()   获取值用getInt()...
   String sql="SELECT salary From mytable Where name=? "
创建连接statement
   Statement st=conn.createStatement();
   执行select语句，查询语句，返回结果集
   Resultset rs= st.execuseQuery(sql)
   执行增删改操作，返回修改了多少条数据,方法执行SQL的INSERT，UPDATE或DELETE语句
   Int rs=st.execuseUperdate(sql)
   执行表操作，返回布尔值
   Boolean rs=st.execute(sql)
创建连接池
   PrepareStatement ps=conn.prepareStatement(sql);
   for(int i=1000,i<2000,i++){
         //setInt中的1表示查询语句的第一个字段，代表name
         ps.setInt(1,‘text’+i)
   }
  ps.executeQuery()
关闭数据库连接
  conn.close()
