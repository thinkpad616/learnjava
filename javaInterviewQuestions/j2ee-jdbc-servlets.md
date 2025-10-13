# J2EE: JDBC and Servlets (Study Guide + Examples)

## Contents
- JDBC Drivers and Architecture
- Connections, Statements
- PreparedStatement vs Statement vs CallableStatement
- Connection Pooling (HikariCP)
- Transactions and Isolation Levels
- Row Mappers and DAO Pattern
- Servlets: lifecycle, doGet/doPost
- Filters and Listeners
- JSP and JSTL overview
- MVC pattern

---

## JDBC Basics
```java
try (Connection con = DriverManager.getConnection(url, user, pass);
     PreparedStatement ps = con.prepareStatement("select id,name from emp where id=?")) {
    ps.setInt(1, 10);
    try (ResultSet rs = ps.executeQuery()) {
        while (rs.next()) { System.out.println(rs.getString("name")); }
    }
}
```

## Connection Pooling
Use HikariCP; tune pool size and timeouts.

## Transactions
Set auto-commit false; commit/rollback explicitly. Choose correct isolation level.

## Servlets
```java
public class HelloServlet extends HttpServlet {
    @Override protected void doGet(HttpServletRequest req, HttpServletResponse resp) throws IOException {
        resp.getWriter().println("Hello");
    }
}
```
