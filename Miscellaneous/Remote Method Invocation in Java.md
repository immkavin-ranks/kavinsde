> We create a Java RMI (Remote Method Invocation) application that displays database data from MySQL using WampServer.

GitHub Repository: [Java RMI MySQL Demo](https://github.com/immkavin-ranks/java-rmi-mysql)

**Requirements**
- WampServer running with MySQL
- Java JDK installed
- MySQL JDBC driver in your class path

**Create a database and table in MySQL**

```SQL
CREATE DATABASE school;
USE school;

CREATE TABLE students (
    id INT PRIMARY KEY AUTO_INCREMENT,
    name VARCHAR(100),
    email VARCHAR(100)
);

INSERT INTO students (name, email) VALUES
    ('John Doe', 'john@example.com'),
    ('Jane Smith', 'jane@example.com');
```

![](attachments/Screenshot%202025-01-18%20132510.png)

**Insert some data:**

![](attachments/Pasted%20image%2020250118134152.png)

**Project folder structure**

java-rmi-mysql-demo/
├── Student.java
├── DatabaseService.java
├── DatabaseServiceImpl.java
├── Server.java
├── Client.java
└── lib/
    └── mysql-connector-j-9.1.0.jar

**Student.java**
```java
import java.io.Serializable;

public class Student implements Serializable {
    private int id;
    private String name;
    private String email;
    
    public Student(int id, String name, String email) {
        this.id = id;
        this.name = name;
        this.email = email;
    }
    
    // Getters and setters
    public int getId() { return id; }
    public String getName() { return name; }
    public String getEmail() { return email; }
    
    @Override
    public String toString() {
        return "Student [id=" + id + ", name=" + name + ", email=" + email + "]";
    }
}
```

**DatabaseService.java**
```java
import java.rmi.Remote;
import java.rmi.RemoteException;
import java.util.List;

public interface DatabaseService extends Remote {
    List<Student> getAllStudents() throws RemoteException;
}
```

**DatabaseServiceImpl.java**
```java
import java.rmi.RemoteException;
import java.rmi.server.UnicastRemoteObject;
import java.sql.*;
import java.util.ArrayList;
import java.util.List;

public class DatabaseServiceImpl extends UnicastRemoteObject implements DatabaseService {
    private static final String DB_URL = "jdbc:mysql://localhost:3306/school";
    private static final String USER = "root";
    private static final String PASS = "";
    
    public DatabaseServiceImpl() throws RemoteException {
        super();
    }
    
    @Override
    public List<Student> getAllStudents() throws RemoteException {
        List<Student> students = new ArrayList<>();
        
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
            
            try (Connection conn = DriverManager.getConnection(DB_URL, USER, PASS);
                 Statement stmt = conn.createStatement();
                 ResultSet rs = stmt.executeQuery("SELECT * FROM students")) {
                
                while (rs.next()) {
                    students.add(new Student(
                        rs.getInt("id"),
                        rs.getString("name"),
                        rs.getString("email")
                    ));
                }
            }
        } catch (Exception e) {
            throw new RemoteException("Database error: " + e.getMessage());
        }
        
        return students;
    }
}
```

**Server.java**
```java
import java.rmi.registry.LocateRegistry;
import java.rmi.registry.Registry;

public class Server {
    public static void main(String[] args) {
        try {
            DatabaseService service = new DatabaseServiceImpl();
            Registry registry = LocateRegistry.createRegistry(1099);
            registry.rebind("DatabaseService", service);
            System.out.println("Server is running...");
        } catch (Exception e) {
            System.err.println("Server error: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Client.java**
```java
import java.rmi.registry.LocateRegistry;
import java.rmi.registry.Registry;
import java.util.List;

public class Client {
    public static void main(String[] args) {
        try {
            Registry registry = LocateRegistry.getRegistry("localhost", 1099);
            DatabaseService service = (DatabaseService) registry.lookup("DatabaseService");
            
            List<Student> students = service.getAllStudents();
            
            System.out.println("Students from database:");
            for (Student student : students) {
                System.out.println(student);
            }
        } catch (Exception e) {
            System.err.println("Client error: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Compile** all the java files: `javac *.java`

**Start the server:**
`java -cp ".;.\lib\mysql-connector-j-9.1.0.jar;" Server`

![](attachments/Screenshot%202025-01-18%20133146.png)

**Start client:** `java Client`

![](attachments/Pasted%20image%2020250118135044.png)

That's It. 🥳

**Necessary Resources:**

Download the MySQL JDBC driver if you haven't already:

- Go to [https://dev.mysql.com/downloads/connector/j/](https://dev.mysql.com/downloads/connector/j/)
- Download the "Platform Independent" version
- Extract the .jar file

Profile: [Kavin - GitHub](https://github.com/immkavin-ranks/)