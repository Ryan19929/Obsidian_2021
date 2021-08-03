# Logstash导出Mysql数据到ES的问题
-	针对高版本的MySql jar包，jdbc_driver_class参数需要从"com.mysql.jdbc.Driver"改成"com.mysql.cj.jdbc.Driver"
-	遇到地区时间问题，需要在查询语句中添加时区。相应字段如，jdbc_connection_string => "jdbc:mysql://10.4.177.69:3306/mysql?serverTimezone=UTC"
-	output中的document_id是不允许重复的
-	Logstash不必和ES在同一个服务器上，只要可以相互访问即可
test