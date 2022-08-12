# Exception(Error) Handling for RESTful Services:
 - Spring Boot provides a good default implementation for exception handling for RESTful Services. 
## Implementing Exception Handling - 404 Resource Not Found :
 - We specify the Response Status for a specific exception along with the definition of the Exception of ‘@ResponseStatus’ annotation in UserNotFoundException.java class.
  ```
  @ResponseStatus(code = HttpStatus.NOT_FOUND)
  public class UserNotFoundException extends RuntimeException {

    private static final long serialVersionUID = 1L;

    public UserNotFoundException(String message) {
        super(message);

    }

  }
  ```

  ## Customizing Error Response Structure:
      *  Default error response provided by Spring Boot contains all the details that are typically needed. we can define a specific error response structure. \
       Let’s define a simple error response bean. \
       
```
public class ErrorDetails {
private Date timestamp;
private String message;
private String details;

public ErrorDetails(Date timestamp, String message, String details) {
super();
this.timestamp = timestamp;
this.message = message;
this.details = details;
}

public Date getTimestamp() {
return timestamp;
}

public String getMessage() {
return message;
}

public String getDetails() {
return details;
}
}
```

   * To use ErrorDetails to return the error response, let’s create a GlobalExceptionHandler class annotated with @ControllerAdvice annotation. 
  