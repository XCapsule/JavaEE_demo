# JavaEE_demo
JavaEE入门DEMO
## 图示
![img](https://github.com/XCapsule/JavaEE_demo/blob/master/mvc.png)
## 代码示例
**DAO层(Dao)**
```java
    ResultSet rs = s.executeQuery(sql);
  
         if (rs.next()) {
             hero = new Hero();
             String name = rs.getString(2);
             float hp = rs.getFloat("hp");
             int damage = rs.getInt(4);
             hero.name = name;
             hero.hp = hp;
             hero.damage = damage;
             hero.id = id;
     }
```
**Model层(Bean)**
```java
    public class Hero {
    public int id;
    public String name;
    public float hp;
    public int damage;
    public int getId() {...}
    public void setId(int id) {...}
    public int getName() {...}
    public void setName(int id) {...}
    ...
```
**Servlet层(Servlet)**
```java
    // List Heroes
    public class HeroListServlet extends HttpServlet {

        protected void service(HttpServletRequest request, HttpServletResponse response)
                throws ServletException, IOException {
            List<Hero> heros = new HeroDAO().list();
            request.setAttribute("heros", heros);
            request.getRequestDispatcher("listHero.jsp").forward(request, response);

        }
    }
```
