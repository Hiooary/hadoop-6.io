# 使用 JAVA 操作 HDFS ——2 </br>
  ——使用 hdfs 自身提供的 api 全方位掌握HDFS，使用类 FileSystem </br>
  
  1.在 HDFS 下创建文件夹，代码如图：
  ![图片](https://github.com/Hiooary/hadoop_6.io/blob/master/images/code1.PNG)
  
   运行报错，<b>Permission denied: user=jxy, access=WRITE, inode="":root:supergroup:rwxr-xr- </b>，百度了一下，是因为权限不够，不能在hdfs中写，所以解决的话可以给 /user/root 赋权限，或者修改 hdfs-site.xml 配置文件
   查看：<b>hadoop fs -ls /</b>
   修改权限：<b>hadoop fs -chmod 777 /user（或者 /user/root ）</b>
   验证：<b>hadoop fs -ls /</b>
   ![图片](https://github.com/Hiooary/hadoop_6.io/blob/master/images/chmod.PNG)
   
   修改文件，加入如下代码：
   /<property>
   /<name>dfs.permissions /</name>
   /<value>false/</value>
   /</property>
   ![图片](https://github.com/Hiooary/hadoop_6.io/blob/master/images/permissions.PNG)
  
