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