# 使用 JAVA 操作 HDFS(2)</br>
  ——使用 hdfs 自身提供的 api 全方位掌握HDFS，使用类 FileSystem </br>
  
  1.在 HDFS 下创建文件夹，代码如图：</br>
  ![图片](https://github.com/Hiooary/hadoop_6.io/blob/master/images/code1.PNG)</br>
  
   运行报错，<b>Permission denied: user=jxy, access=WRITE, inode="":root:supergroup:rwxr-xr- </b>，百度了一下，是因为权限不够，不能在hdfs中写，所以解决的话可以给 /user/root 赋权限，或者修改 hdfs-site.xml 配置文件，<b>然后重启系统</b>，不然可能无法作用</br>
   查看：<b>hadoop fs -ls /</b></br>
   修改权限：<b>hadoop fs -chmod 777 /user（或者 /user/root ）</b></br>
   验证：<b>hadoop fs -ls /</b></br>
   ![图片](https://github.com/Hiooary/hadoop_6.io/blob/master/images/chmod.PNG)</br>
   
   修改文件，加入如下代码：</br>
   \<property></br>
   \<name>dfs.permissions \</name></br>
   \<value>false\</value></br>
   \</property></br>
   ![图片](https://github.com/Hiooary/hadoop_6.io/blob/master/images/permissions.PNG)</br>
   
   再次运行，出现问题如下图，<b>File /java could only be replicated to 0 nodes, instead of 1 </b>，猜测是节点挂了，重新启动节点后，可以运行</br>
   ![图片](https://github.com/Hiooary/hadoop_6.io/blob/master/images/node.PNG)</br>
   
   运行结果如图：</br>
   ![图片](https://github.com/Hiooary/hadoop_6.io/blob/master/images/test.PNG)</br>
   
 2.在 HDFS 下上传文件，代码如图：</br>
    ![图片](https://github.com/Hiooary/hadoop_6.io/blob/master/images/code2.PNG)</br>
    
   在 D 盘下建一个 log.txt 文件用于上传，运行代码，可以在 hadoop 中看到代码已经上传：</br>
     ![图片](https://github.com/Hiooary/hadoop_6.io/blob/master/images/java.PNG)</br>
 3. 在 HDFS 下下载文件，代码如图：</br>
    ![图片](https://github.com/Hiooary/hadoop_6.io/blob/master/images/code3.PNG)</br>
    
    运行，可以看到 log.txt 的内容：</br>
     ![图片](https://github.com/Hiooary/hadoop_6.io/blob/master/images/log.PNG)</br>
 4. 在 HDFS 下下载文件，代码如图：</br>
    ![图片](https://github.com/Hiooary/hadoop_6.io/blob/master/images/code4.PNG)</br>
    
    运行，可以看到 log.txt 的内容：</br>
     ![图片](https://github.com/Hiooary/hadoop_6.io/blob/master/images/delete.PNG)</br>
    
     
   
  
