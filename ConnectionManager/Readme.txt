Opening a lot of database connections is not good practice. I'm working in a version of my project called ConnectionManager that has the code for updating a database table. And I'll go to the tables package and open AdminManager.java. 
The way this application is currently architected every time I call my DBUtil class's getConnection method, I'm opening a new connection,
and then I am closing that connection when that method is finished. And if you count up all the times that get connection method is used, you'll see that the opening and closing connections execute many, many times.

In JDBC this is bad practice, and that's because connections are expensive. They take time, memory, and resources, and so you should minimize the opening and closing of connections by reusing connections. As i did in my project.
When you work in a Java Enterprise Edition Server environment such as JBoss, the server typically will provide connection pooling. It's a multi-user environment, and so it's vital that multiple users reuse those connections. If you're building your own Java application,
though, either as a console application like this one or a desktop application, I needed to write my own logic.
