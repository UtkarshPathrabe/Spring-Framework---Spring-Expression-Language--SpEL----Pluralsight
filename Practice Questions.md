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

Q06. In your application, there are two beans, User and Order, that have the same property name. You wrote the following code to set the Order bean’s name property with a value.  
```
1 SpelExpressionParser parser = new SpelExpressionParser();
2 User user = new User();
3 Order order = new Order();
4 StandardEvaluationContext userContext = new StandardEvaluationContext(user);
5 parser.parseExpression("id").setValue(userContext,"12345");
6 System.out.println(order.getId());
```  
When you run it, you get “null” as the output. How would you correct the code so that you get the output as “12345”?  
A. Add the following line:  
`StandardEvaluationContext orderContext = new StandardEvaluationContext(order);`  
Change line 5 as:  
`parser.parseExpression("order.id").setValue(userContext,"12345");`  
B. Add the following line:  
`StandardEvaluationContext orderContext = new StandardEvaluationContext(order);`  
Change line 5 as:  
`parser.parseExpression("id").setValue(user,"12345");`  
C. Add the following line:  
`StandardEvaluationContext orderContext = new StandardEvaluationContext(order);`  
And change line 5 to:  
`parser.parseExpression("id").setValue(orderContext,"12345");`  
D. Add the following line:  
`StandardEvaluationContext orderContext = new StandardEvaluationContext(order);`  
Change line 5 as:  
`parser.parseExpression("id").setValue("12345");`  
Answer:  
Add the following line:  
`StandardEvaluationContext orderContext = new StandardEvaluationContext(order);`  
And change line 5 to:  
`parser.parseExpression("id").setValue(orderContext,"12345");`  

Q07. What is correct about the @Value annotation?  
A. It is an annotation used for injecting values in to Spring beans.  
B. It is an annotation used specifically for writing SpEL expressions.  
C. It is anannotation used for wiring SpEL expressions in Spring.  
D. It is an annotation used for writing SpEL expressions in metadata.  
Answer: `It is an annotation used for injecting values in to Spring beans.`  

Q08. In plain Java code, what SpEL expression would you write to access the first name of a comma (,) separated list of names? Assume that you have a defined variable called "names".  
A. "#names.split(',')[0]"  
B. "#names.split(",")[0]"  
C. "names.split(',')[0]"  
D. "{names.split(",")[0]}"  
Answer: `"#names.split(',')[0]"`  

Q09. In plain Java code, what SpEL expression would you write to access the country property from the systemProperties predefined variable?  
A. "#{systemProperties['user.country']}"  
B. "{#systemProperties['user.country']}"  
C. "#systemProperties['user.country']"  
D. "#systemProperties[user.country]"  
Answer: `"#systemProperties['user.country']"`  

Q10. You are using setter method wiring to set the value to the country property of a User bean with the user’s Locale specific information. what is the correct syntax? Assume you have a setter method as follows:  
```
public void setCountry(String country) {
    this.country = country;
}
```  
A.  
```
@Value("#{systemProperties[user.country]}")
public void setCountry(String country) {
    this.country = country;
}
```  
B.  
```
@Value("#systemProperties['user.country']")
public void setCountry(String country) {
    this.country = country;
}
```  
C.  
```
@Value("#{systemProperties['user.country']}")
public void setCountry(String country) {
    this.country = country;
}
```  
D.  
```
@Value("#{systemProperty['user.country']}")
public void setCountry(String country) {
    this.country = country;
}
```  
Answer:  
```
@Value("#{systemProperties['user.country']}")
public void setCountry(String country) {
    this.country = country;
}
```  

Q11. In your application, you have City bean as follows:  
```
@Component("city")
public class City {
	private String name;
	private Boolean isCapital;
	public City(String name, Boolean isCapital) {
		this.name = name;
		this.isCapital = isCapital;
	}
}
```  
Elsewhere in your application, you have populated a list of City beans as follows:  
```
List<City> cities = new ArrayList<>();
cities.add(new City("Copenhagen",true));
cities.add(new City("Hadsund",false));
cities.add(new City("Arden",false));
```  
Now you need to wire some bean’s property with a list of non-capital cities. How would you write the SpEL expression using the @Value annotation for this?  
A.  
```
@Value("#{cities?[isCapital!= true]}")
private List<City> nonCapitalCities;
```  
B.  
```
@Value("#cities.?[isCapital!= true]")
private List<City> nonCapitalCities;
```  
C.  
```
@Value("#{cities?[!isCapital]}")
private List<City> nonCapitalCities;
```  
D.  
```
@Value("#{cities.?[isCapital!= true]}")
private List nonCapitalCities;
```  
Answer:  
```
@Value("#{cities.?[isCapital!= true]}")
private List nonCapitalCities;
```  