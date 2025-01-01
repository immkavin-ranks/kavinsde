Date: 01-01-2025 
Platform: Windows

**Requirements**:
- Java 11 or above
- Tomcat server 10.x from https://tomcat.apache.org/

**Setup** 

Ignore this step if you have already set path variables for java. 
```
set PATH=C:\jdk1234;%PATH% 
set JAVA_HOME=C:\jdk1234
```


**Unzip** tomcat server and put it in C:\apache-tomcat-123456

```
set CATALINA_HOME=C:\apache-tomcat-123456
```

**Start** tomcat `%CATALINA_HOME%\bin\startup.bat`

**Visit**: http://localhost:8080/

![](attachments/Pasted%20image%2020250101150329.png)

To **Shutdown** the server `%CATALINA_HOME%\bin\shutdown`

**Sample Code**
```java
// Import required java libraries
import java.io.*;
import jakarta.servlet.*;
import jakarta.servlet.http.*;

// Extend HttpServlet class
public class HelloWorld extends HttpServlet {
 
   private String message;

   public void init() throws ServletException {
      // Do required initialization
      message = "Hello World";
   }

public void doGet(HttpServletRequest request, HttpServletResponse response)
      throws ServletException, IOException {
      
      // Set response content type
      response.setContentType("text/html");

      // Actual logic goes here.
      PrintWriter out = response.getWriter();
      out.println("<h1>" + message + "</h1>");
   }

   public void destroy() {
      // do nothing.
   }
}

```

**Compile** with servlet API:

`javac -cp "C:\apache-tomcat-123456\lib\servlet-api.jar" HelloWorld.java`

Copy the class file, then 👇

**Servlet** **Deployment**

Go to:  `C:\apache-tomcat-123456/webapps/ROOT/WEB-INF/classes` and *paste* the class file.

If `classes` not present already, create and paste the `.class` file there.

**Edit**: web.xml in `C:\apache-tomcat-123456/webapps/ROOT/WEB-INF/`

```xml
<servlet>
   <servlet-name>HelloWorld</servlet-name>
   <servlet-class>HelloWorld</servlet-class>
</servlet>

<servlet-mapping>
   <servlet-name>HelloWorld</servlet-name>
   <url-pattern>/helloworld</url-pattern>
</servlet-mapping>
```

Paste these entries inside the `<web-app>...</web-app>`in web.xml

**Structure**:

In  `C:\apache-tomcat-123456`

```
webapps/ROOT/
    ├── WEB-INF/
        ├── classes/
        │      └── HelloWorld . class
        └── web.xml
```

**Start** the tomcat server

**Point** your browser to http://localhost:8080/helloworld

![](attachments/Pasted%20image%2020250101151517.png)

There is your servlet. 🤩

You can explore more examples, that is already available in your server,
Point to http://localhost:8080/examples/servlets/

**Resources**:
1. https://www.tutorialspoint.com/servlets/servlets-first-example.htm
2. https://tomcat.apache.org/tomcat-10.1-doc/appdev/installation.html
3. https://tomcat.apache.org/tomcat-10.1-doc/appdev/sample/
4. https://www.tutorialspoint.com/servlets/servlets-environment-setup.htm

**Author**: [Kavin Manoharan](https://www.linkedin.com/in/kavinsde)  @  [Visit GitHub](https://github.com/immkavin-ranks/)