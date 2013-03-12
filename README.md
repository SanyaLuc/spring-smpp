spring-smpp
===========

Spring wrapper on top of smslib and JSMPP libraries.

Work in progress, see (minimal.xml)[src/test/resources/minimal.xml]

```
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans" 
       xmlns:util="http://www.springframework.org/schema/util" 
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="
       http://www.springframework.org/schema/beans
  	   http://www.springframework.org/schema/beans/spring-beans-3.0.xsd
		   http://www.springframework.org/schema/util
		   http://www.springframework.org/schema/util/spring-util-3.0.xsd">

  <bean class="com.sentaca.spring.smpp.SMPPService">
    <property name="gatewaysConfiguration">
      <set>
        <bean class="com.sentaca.spring.smpp.SMSCGatewayConfiguration">
          <constructor-arg>
            <bean class="com.sentaca.spring.smpp.BindConfiguration">
              <property name="systemId" value="smppclient1" />
              <property name="password" value="password" />
              <property name="host" value="xxx.sentaca.com" />
              <property name="port" value="2775" />
              <property name="sourceTON" value="0" />
              <property name="sourceNPI" value="1" />
              <property name="destinationTON" value="1" />
              <property name="destinationNPI" value="1" />
              <property name="systemType" value="test" />
              <property name="serviceType" value="test" />
            </bean>
          </constructor-arg>
          <constructor-arg>
            <bean class="com.sentaca.spring.smpp.mo.MessageReceiver">
              <constructor-arg>
                <!-- inject your handler here -->
                <bean class="com.sentaca.spring.smpp.MyDeliverSmMessageProcessor"/>
              </constructor-arg>
            </bean>
          </constructor-arg>
        </bean>
      </set>
    </property>
  </bean>


</beans>
```
