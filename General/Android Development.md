- **React**
	- JavaScript Component framework
	- npm (node package management)
- **Spring**
	- Java MVC framework
	- Maven, Gradle
	- middle man to MVC and ORM frameworks
- **Spring Boot**
	- Spring with heavy auto-configuration features
	- Injection Dependency Framework
		- manages life-cycle of **Java beans** (components)
	- includes **Apache Tomcat** by default
	- Dependency versions automatically added to parent project
	- no `web.xml` file
		- routing, filtering, & session configuration handled by annotations and implicit classes
	- **Actuator** monitors application health and API endpoint performance metrics
- **Hibernate**
	- Java ORM framework
	- Implements the **Java Persistence API (JPA)** specification

# Model-View-Controller (MVC) Architecture
- `model`
- `view`
- `controller`
	- `editor` - specialized `controller` associated with a particular `view` for modifying
- Examples:
	- Ruby on Rails
	- Django
	- Spring

# Object-relational mapping (ORM)
- Technique for converting between heap and relational database entries
- Examples:
	- Hibernate