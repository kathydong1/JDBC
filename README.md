加载驱动Class.forName(driverClass)
//加载MySql驱动
   Class.forName("com.mysql.jdbc.Driver")
//加载Oracle驱动
   Class.forName("oracle.jdbc.driver.OracleDriver")
获得数据库连接：
   Connection conn=DriverManager.getConnection("jdbc:mysql://127.0.0.1:3306/imooc", "root", "root");
写入SQL语句,prepareStatement中用？表示变量，设置时用set
   String sql="SELECT salary From mytable Where name=? "
创建连接statement
   Statement st=conn.createStatement();
创建连接池
   PrepareStatement ps=conn.prepareStatement(sql);
