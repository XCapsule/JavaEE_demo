# JavaEE_demo
JavaEE入门DEMO
## 图示
![img](https://github.com/XCapsule/JavaEE_demo/blob/master/mvc.png)
## 代码示例
**DAO层(Dao)**
```java
    public List<Hero> list() {
        List<Hero> heros = new ArrayList<Hero>();
        ......
        ResultSet rs = s.executeQuery(sql);
  
        while (rs.next()) {
             Hero hero = new Hero();
             int id = rs.getInt(1);
             String name = rs.getString(2);
             hero.id = id;
             hero.name = name;
             
             heros.add(hero);
        }
        ......
        return heros;    
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
