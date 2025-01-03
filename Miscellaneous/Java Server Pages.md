Wamp server for MySQL + Tomcat server

**Configure WampServer's Apache to work with Tomcat:**

C:\wamp64\bin\apache\apache2.4.62.1\conf\extra\http-ajp.conf

create the file and paste this

```
LoadModule proxy_module modules/mod_proxy.so
LoadModule proxy_ajp_module modules/mod_proxy_ajp.so

<IfModule proxy_ajp_module>
    ProxyPass /jsp ajp://localhost:8009/jsp
    ProxyPassReverse /jsp ajp://localhost:8009/jsp
</IfModule>
```

C:\wamp64\bin\apache\apache2.4.62.1\conf\httpd.conf add this line below

`Include conf/extra/httpd-ajp.conf`

C:\apache-tomcat-10.1.34\conf\server.xml and uncomment this section

<!-- Define an AJP 1.3 Connector on port 8009 -->
   
    <Connector protocol="AJP/1.3"
               address="::1"
               port="8009"
               redirectPort="8443"
               maxParameterCount="1000"
		
               />


and add `secretRequired="false"` inside Connector

Project: C:\apache-tomcat-10.1.34\webapps\testjsp

![](attachments/Pasted%20image%2020250103085059.png)

![](attachments/Pasted%20image%2020250103085109.png)

Download MySQL connector https://dev.mysql.com/downloads/connector/j/

Place the jar file in following locations:

C:\apache-tomcat-10.1.34\lib
C:\apache-tomcat-10.1.34\webapps\testjsp\WEB-INF\lib

Create a test.jsp file in your project folder: see the image above

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<html>
<body>
<h2>JSP Test Page</h2>
<%= new java.util.Date() %>
</body>
</html>
```


Start wampserver

Start tomcat

try Running: http://localhost:8080/testjsp/test.jsp


Now to DB example

Add this context configuration to your `C:\apache-tomcat-10.1.34\conf\context.xml` inside the `<Context>` tag:

```xml
<Resource name="jdbc/MySQLDB"
          auth="Container"
          type="javax.sql.DataSource"
          maxTotal="100"
          maxIdle="30"
          maxWaitMillis="10000"
          username="root"
          password=""
          driverClassName="com.mysql.cj.jdbc.Driver"
          url="jdbc:mysql://localhost:3306/nmc?autoReconnect=true"/>
```

Create a new file `C:\apache-tomcat-10.1.34\webapps\testjsp\WEB-INF\web.xml` if it doesn't exist:

```xml
<?xml version="1.0" encoding="UTF-8"?>
<web-app xmlns="http://xmlns.jcp.org/xml/ns/javaee"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://xmlns.jcp.org/xml/ns/javaee 
         http://xmlns.jcp.org/xml/ns/javaee/web-app_4_0.xsd"
         version="4.0">
    
    <resource-ref>
        <description>MySQL Connection Pool</description>
        <res-ref-name>jdbc/MySQLDB</res-ref-name>
        <res-type>javax.sql.DataSource</res-type>
        <res-auth>Container</res-auth>
    </resource-ref>
    
</web-app>
```


display_users.jsp

```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8" pageEncoding="UTF-8"%>
<%@ page import="java.sql.*" %>
<!DOCTYPE html>
<html>
<head>
    <title>Users Data</title>
    <style>
        table {
            border-collapse: collapse;
            width: 80%;
            margin: 20px auto;
        }
        th, td {
            border: 1px solid #ddd;
            padding: 8px;
            text-align: left;
        }
        th {
            background-color: #f2f2f2;
        }
        tr:nth-child(even) {
            background-color: #f9f9f9;
        }
        .error {
            color: red;
            padding: 10px;
            margin: 10px;
        }
    </style>
</head>
<body>
    <h2>Users List</h2>
    <%!
        // Method to safely close ResultSet
        public void closeResultSet(ResultSet rs) {
            try {
                if (rs != null && !rs.isClosed()) {
                    rs.close();
                }
            } catch (SQLException e) {
                // Log the error but don't throw it
                e.printStackTrace();
            }
        }

        // Method to safely close Statement
        public void closeStatement(Statement stmt) {
            try {
                if (stmt != null && !stmt.isClosed()) {
                    stmt.close();
                }
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }

        // Method to safely close Connection
        public void closeConnection(Connection conn) {
            try {
                if (conn != null && !conn.isClosed()) {
                    conn.close();
                }
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    %>
    <%
    Connection conn = null;
    PreparedStatement pstmt = null;
    ResultSet rs = null;
    
    try {
        // Register driver with proper error handling
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
        } catch (ClassNotFoundException e) {
            throw new ServletException("MySQL Driver not found.", e);
        }
        
        // Create the connection with additional parameters to prevent abandoned connections
        String url = "jdbc:mysql://localhost:3306/nmc?autoReconnect=true&useUnicode=true" +
                    "&characterEncoding=UTF-8&allowPublicKeyRetrieval=true&useSSL=false" +
                    "&connectionCollation=utf8mb4_unicode_ci";
        String dbUsername = "root";
        String dbPassword = "";
        
        conn = DriverManager.getConnection(url, dbUsername, dbPassword);
        
        if(conn != null) {
            out.println("<p style='color: green'>Connected to database successfully!</p>");
            
            // Use PreparedStatement instead of Statement for better security
            String sql = "SELECT email, username FROM users";
            pstmt = conn.prepareStatement(sql);
            rs = pstmt.executeQuery();
            
            out.println("<table>");
            out.println("<tr>");
            out.println("<th>Email</th>");
            out.println("<th>Username</th>");
            out.println("</tr>");
            
            while (rs != null && rs.next()) {
                out.println("<tr>");
                String email = rs.getString("email");
                String username = rs.getString("username");
                out.println("<td>" + (email != null ? email : "") + "</td>");
                out.println("<td>" + (username != null ? username : "") + "</td>");
                out.println("</tr>");
            }
            
            out.println("</table>");
        }
        
    } catch(Exception e) {
        out.println("<div class='error'>");
        out.println("Error: " + e.getMessage());
        out.println("</div>");
        e.printStackTrace();
    } finally {
        // Close resources in reverse order of creation
        closeResultSet(rs);
        closeStatement(pstmt);
        closeConnection(conn);
    }
    %>
    
    <%-- Explicitly request garbage collection to clean up any remaining resources --%>
    <% System.gc(); %>
</body>
</html>
```

After making these changes:

1. Stop Tomcat completely
2. Wait a few seconds
3. Start Tomcat again
4. Access your page at: `http://localhost:8080/testjsp/display_users.jsp`


Screenshots

![](attachments/Pasted%20image%2020250103090015.png)
![](attachments/Pasted%20image%2020250103090031.png)
![](attachments/Pasted%20image%2020250103090040.png)
![](attachments/Pasted%20image%2020250103090104.png)
![](attachments/Pasted%20image%2020250103090316.png)
![](attachments/Pasted%20image%2020250103090329.png)

Source code: https://github.com/immkavin-ranks/testjsp