**--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------**
real world production code, using if-else condition becomes costly as one extra else could crash the application. Knowing proper replacements separates junior devs from seniors.

if (paymentType.equals("creditcard")) {
 processCreditCard(payment);
} else if (paymentType.equals("upi")) {
 processUpi(payment);
} else if (paymentType.equals("crypto")) {
 processCrypto(payment);
}

If you’re still writing giant chains of if-else statements in your core logic, you’re holding your code hostage.
They're simple, but they don't scale.

Once logic gets complex, your code becomes hard to test, extend, and read.

So what do senior Java devs do? They often replace them with the Strategy Pattern.

The Strategy Pattern is like having different ways to get to the airport. Instead of one giant function with if-else for "take bus," "take taxi," or "take train," you create a separate "strategy" for each. Your main code simply picks the right strategy for the situation and says, "Go."

Instead of endless else if blocks, you: 
-> Define a strategy interface (PaymentStrategy). 
-> Create concrete classes for each case (CreditCardPayment, UpiPayment).
-> Use a Map to pick the right strategy at runtime.
strategyMap.get(type).processPayment(payment);
Boom. Now you can add new logic without touching the old code. Clean, scalable, and maintainable.

![1761495072312](https://github.com/user-attachments/assets/b8dba54c-2dbd-4f41-aeb7-db2d0fda5840)
**-----------------------------------------------------------------------------------------------------------------------------------------------------------------**
JAVA NEW FEATURES
![1761326164787](https://github.com/user-attachments/assets/9f97263f-2b3a-4e70-93f9-4d1d40aa806d)

**-----------------------------------------------------------------------------------------------------------------------------------------------------------------**
In a Spring Boot ProductController, you must handle two distinct scenarios: returning a simple 404 Not Found status when a product is missing, and returning a 201 Created status with a dynamic Location header upon successful creation. What are the Spring mechanisms you would use to implement each of these requirements, and why?

Two main ways to control the HTTP response to send back to client: @ResponseStatus and ResponseEntity

→ @ResponseStatus: Simple Static Label
>Stick it on an exception or a controller method, always returns the same HTTP status code. >"Fire-and-forget" approach. Quick and clean for situations where the response is always the same.
 >Best for: Simple error handling. For eg, a ResourceNotFoundException can be annotated with @ResponseStatus(HttpStatus.NOT_FOUND), will always return a 404 status.
 >Limitation: Can't add custom headers or a dynamic response body

→ ResponseEntity: Custom Toolkit 🛠️
>Gives full, programmatic control to construct the entire HTTP response at runtime
>Can set the status code, add custom headers, and craft the response body exactly how we need it, often based on some logic.
>Best for: Complex responses, ideal when we need to add a Location header after creating a resource (201 Created) or return a detailed JSON object for a specific error.
>Flexibility: It's the go-to choice when your response needs to adapt.

By combining them, using @RestControllerAdvice to handle exceptions globally, we can use @ResponseStatus for common errors and ResponseEntity for more specific, dynamic ones, giving us both efficiency and flexibility
![1761325976752](https://github.com/user-attachments/assets/9b197e14-0806-47f8-8299-c6cbab8d2df1)

**-----------------------------------------------------------------------------------------------------------------------------------------------------------------**
