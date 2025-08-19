# Languages
## Bun
- based on WebKit JavaScriptCore
- WebKit FTL JIT
	- optimized by LLVM in fourth tier
- Written in Zig
- Drop in replacement for Node.js

# Concepts
[Key Terms](https://trpc.io/docs/concepts)
## Productivity Strategies
### Scrum
### Agile

## Design Patterns
- MVC
- Singleton
- Dependency Injection
- [more](https://www.geeksforgeeks.org/design-patterns-for-mobile-development/)

## Dynamic Web Content
- PHP
- ASP.NET
- Jakarta (Java) Servlet
	- Jakarta Servlet API -- Java classes responsive to client-server protocols
	- Jakarta Server Pages (JSP)
		- Abstracted Jakarta Servlet
> [!example]-
> - Can act as View component of a server-side MVC
> 	- JavaBeans as Model
> 	- Jakarta Servlets as Controller
> ![[JSP_Model_2.svg|]]

---
# Software Stacks
## LAMP
- Linux
- Apache web server
- MySQL
- Perl/PHP/Python
> [!info]-
> ![[LAMP_software_bundle.svg]]

## XAMPP
- Apache web server
- MariaDB
- PHP
- Perl

---
# Tools
## Containerization
### Web Container
Component of web server responsible for URL mapping, access , and lifecycle management of servlets.
Handles requests to Jakarta Servlets and Server Pages
- Winstone / jetty
- Apache Tomcat
- WildFly
## Automation
### CI/CD
- Jenkins
- GitLab CI
- GitHub Actions

## Testing
### General
- JUnit -- Java
- Cypress -- Javascript
- Robot Framework -- Generic
### Test Management
- TestRail
- Zephyr Squad
- XRAY
### Web Automation
- TestCafe
- Cypress
- Selenium
- WebDriver
- Playwright
- Detox
### Mobile
- Appium
- Espresso
- XCUITest
### API
- Rest Assured
- Karate DSL
- SoapUI
- [x] Postman

---
# HTML
![[HTML_element_content_categories.svg]]

---
# Frameworks
- Python
	- Pyramid, CherryPy
	- Django, Flask
		- offer robust enterprise scalability
	- multithreading
	- Unicode support
	- C/Rust bindings
	- JSON serialization
- Ruby
	- Ruby on Rails
		- enables rapid prototyping
	- YAML serialization
## PHP
- PHP
	- Laravel, Symfony

## AJAX
- AJAX (XML)
	- xmlns attribute of html tag


Microservices
Python, Django, AsyncIO
AWS, Docker, Kubernetes
PostgreSQL, Redis
NATS, Kafka

Since 2018 I've been trusted to code performant Python frameworks and applications for University research laboratories, starting with an atomic physics lab at UC Berkeley. To be clear, these were not data science projects; tabletop atom laser experiments demand strict performance specifications on software used to control instruments and mediate control loops. Packages I developed have been used execute experimental sequences that, for example, eventually lead to publishing an article in Nature Physics.

Apart from my laboratory work, I had also formally studied computer science at UC Berkeley and in recent years have worked professionally as a software developer. Working on a variety of systems, including robot application software, ROS code, cloud services, distributed event servers, UI dynamization, etc., has required, naturally, the use of various tools to meet objectives. For example, the robots are implemented in lxc bound Docker containers, communicates with cloud apps like Node Red, MongoDB, and Elastic, all while their development testing/rollout cycles are managed with Gitlab and Ansible. At my current employment, the projects can differ customer-to-customer. I've used different databases (MSSQL, PostgreSQL, Oracle), messaging protocols, and aspects of the application development.

