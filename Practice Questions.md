Spring Framework: Spring Expression Language (SpEL)  
===================================================  

Q01. What is the syntax of the collection selection operator?  
A. =? (equal and question mark)  
B. ? (question mark)  
C. ?. (question mark and period)  
D. .? (period and question mark)  
Answer: `.? (period and question mark)`  

Q02. What SpEL expression should you write in the @Value annotation to set the following value to a property named message?  
*Welcome John Doe, you are currently in US and your time zone is America/New_York.*  
A. 
```
@Value("Welcome #{name}, you are currently in #{systemProperties['user.country']} and your time
zone is #{systemProperties['user.timezone']}")
private String message;
```  
B. 
```
@Value("Welcome #name, you are currently in #systemProperties['user.country'] and your time
zone is #systemProperties['user.timezone']")
private String message;
```  
C. 
```
@Value("Welcome #{name}, you are currently in #{systemProperties[user.country]} and your time
zone is #{systemProperties[user.timezone]}")
private String message;
```  
D. 
```
@Value("Welcome #{name}, you are currently in #{systemProperties['user.country']} and your time
zone is #{systemProperties['user.timeZone']}")
private String message;
```  
Answer: 
```
@Value("Welcome #{name}, you are currently in #{systemProperties['user.country']} and your time
zone is #{systemProperties['user.timezone']}")
private String message;
```  

Q03. You have written the following SpEL in your XML Spring configuration:  
```
<bean id="order" class="com.example.speldemoxml.data.Order">
    <property name="shippingLocations" value="#{shipping.locationsByCountry[user.country]}"/>
</bean>
```  
When you run the application, you get the following exception:  
```
org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'order' ...
nested exception is org.springframework.expression.spel.SpelEvaluationException: Property or field 'shipping' cannot be found on object ...
```  
What could be the reason for this?  
A. A public property named shipping is not defined in the order bean.  
B. A field named shipping is not defined before the order bean definition.  
C. A property named shipping is not defined in the order bean.  
D. A bean named shipping is not defined before the order bean definition.  
Answer: `A bean named shipping is not defined before the order bean definition.`  

Q04. What statement correctly defines SpEL?  
A. Enables to manipulate queries at runtime.  
B. Enables to write expressions that can derive objects.  
C. Enables to write expressions that can create new objects.  
D. Enables to query and manipulate an object/object graphs at run time.  
Answer: `Enables to query and manipulate an object/object graphs at run time.`  

Q05. What is the correct syntax for writing SpEL in the context of metadata?  
A. "#{expression}"  
B. "#expression"  
C. "{#expression}"  
D. "{expression}"  
Answer: `"#{expression}"`  