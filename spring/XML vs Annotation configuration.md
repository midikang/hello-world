XML vs Annotation configuration
===============================
application context
----
XML
contextConfigLocation

Annotation
contextClass and contextConfigLocation

context-param
--------

~~~~
<context-param>
    <param-name>contextConfigLocation</param-name>
    <param-value>classpath:spring/business-config.xml, classpath:spring/tools-config.xml</param-value>
</context-param>

~~~
<context-param>
  <param-name>contextClass</param-name>
  <param-value>org.springframework.web.context.support.AnnotationConfigWebApplicationContext</param-value>
</context-param>
<context-param>
  <param-name>contextConfigLocation</param-name>
  <param-value>org.springframework.samples.petclinic.config.RootApplicationContextConfig</param-value>
</context-param>


servlet-class
--------
org.springframework.web.servlet.DispatcherServlet

init-param
--------
"        <init-param>
            <param-name>contextConfigLocation</param-name>
            <param-value>classpath:spring/mvc-core-config.xml</param-value>
        </init-param>"

"  <init-param>
   <param-name>contextClass</param-name>
   <param-value>org.springframework.web.context.support.AnnotationConfigWebApplicationContext</param-value>
  </init-param>
  <init-param>
   <param-name>contextConfigLocation</param-name>
   <param-value>org.springframework.samples.petclinic.config.MvcCoreConfig</param-value>
  </init-param>"
