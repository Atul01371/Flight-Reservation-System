# Flight-Reservation-System
FRS application is used to search, book flights online. Admin users can add/delete/update flight details. It is developed using Spring and Hibernate frameworks.

<h2>Project workflow : </h2>
web.xml -> FRS-servlet.xml, DispatcherServlet -> hibernate.cfg.xml, jdbc.properties, views folder.
Request comes from user -> DispatcherServlet -> HandlerMapping -> Controller -> class/method based on url --(Model)-> Service layer -> DAO layer -> all the way back to controller -> ViewResolver ->View -> Response to user.
<h2 >web.xml : </h2>
It is called deployment descriptor of web application. It includes all Servlet details mainly Dispatcher servlet which is called front controller of web application. In servlet-mapping all url's are mapped to FRS servlet.Upon initialization of DispatcherServlet, the framework will try to load the application context from a file named [servlet-name]-servlet.xml located in the application's WebContent/WEB-INFdirectory. In this project, our file will be FRS-servlet.xml.

<h2> FRS-servlet.xml : </h2> 
This file is used to create the beans defined in additon to InternalResourceViewResolver, ReloadableResourceBundleMessageSource, PropertyPlaceholderConfigurer, AnnotationSessionFactoryBean, HibernateTransactionManager. hibernate.cfg.xml is also configured in this file in the bean SessionFactory. PropertyPlaceholderConfigurer bean is used to define our property files such as jdbc.properties and message.properties.

<h2>hibernate.cfg.xml : </h2>
It contains configuration details of hibernate along with mapping class 'Flight'.

<h2>jdbc.properties : </h2>
This is properties file which contains jdbc related information such as 
 

<ul> 
<li >driverClassName : OracleDriver </li>
<li> dialect : OracleDialect </li>
<li> databaseurl : url to connect to database  </li>
<li> username : username of database </li>
<li> password : password of database </li>

</ul>

<h2> Model : </h2>
It encapsulates the application data and generally consists of POJO. @Entity marks java bean class as Model. In this project one model 'Flight' is there.

<h2>View:  </h2>
View is responsible for rendering the model data according to user request. Spring MVC supports many types of views for different presentation technologies. These include - JSPs, HTML, PDF, Excel worksheets, XML, Velocity templates, XSLT, JSON, Atom and RSS feeds, JasperReports, etc. But most commonly we use JSP.

<h2>Controller : </h2>
The DispatcherServlet delegates the request to the controllers to execute the functionality specific to it. The @Controller annotation indicates that a particular class serves the role of a controller. The @RequestMapping annotation is used to map a URL to either an entire class or a particular handler method. In this project only one controller 'FRSController' is there which is autowired with 'FlightService'. RequestMapping annotation helps controller which method to call/resolve based on path of request and method type GET/POST. @ModelAttribute is used as parameter to method to tell which model to use to bind View and Controller.

<h2> Service : </h2>
@Service annotation indicates class as service.

FlightService.java is an interface that contains set of methods.
FlightServiceImpl.java is a class that implements FlightService and access DAO layer by autowiring FlightDAO.
<h2> DAO :</h2>
FlightDAO.java is an interface that contains set of methods.
FlightDAOImpl.java is a class that implements FlightService and access database using Hibernate by autowiring SessionFactory. (still needs to add some more files)
