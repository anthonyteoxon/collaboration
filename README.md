# Collaboration

Requirements:
Use Tomcat 7 as per requirements of opentides
Use Java 7

#Create Server:
1. Go to toolbar Window > Show View > Other > Server
2. When the server view was shown: right-click(New) > Server > Then Server Options Dialog will appear(Select Apache Tomcat v7.0 ) > Then locate your tomcat directory on your computer > Next > Add the project to your server > Finsih

3. Additional Config:
change database connection in your server
Context.xml: Add this before closing of context tag. </Context>
	<Resource auth="Container" driverClassName="com.mysql.jdbc.Driver"
		maxActive="100" maxIdle="30000" maxWait="10000" name="jdbc/opentides3"
		password="" type="javax.sql.DataSource"
		url="jdbc:mysql://localhost:3306/opentides3?autoReconnect=true" 
		username="root"/>
		
		#For Database connection - this config is in localhost.properties
		database.driver=com.mysql.jdbc.Driver
		database.url=jdbc:mysql://localhost/opentides3
		database.username=root
		database.password=
		database.jndi=java:comp/env/jdbc/opentides3

#Important:	
server.xml, change "opentides" for any url that you want. And, change the value of "reloadable" to false, default value is true.

		<Context docBase="tatiana" path="/opentides" reloadable="true" source="org.eclipse.jst.jee.server:tatiana"/></Host>
		
		Note: If context reloading still occurs uncomment the excluded libraries in log4j dependency located in your pom.xml

#PermGen
1. click your server(server settings will appear)
2. 
3. add this to VM Arguments -Xmx1024m -XX:MaxPermSize=512m
		
Additional Possible Errors that you might encounter:
If table in your database were not generated upon server start up, just drop the database and restart your server.


Most of the fixes were already committed, so just in case that you still experience some error just follow the instructions above.


