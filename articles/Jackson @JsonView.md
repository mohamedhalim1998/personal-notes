#spring #jackson #web #java 

solve the problem of reusing the same DTO to provide different views of the same model data to different clients/users

## Sample

### define view
```java
public class View {//Enclosing type to define User views  
 public static interface UserView {      //External View for User   
      public static interface External {  
      }      //Intenal View for User, will inherit all filds in External  
      public static interface Internal extends External {  
      }  
  }  
}
```

### use @JsonView on the DTO

```java
public class UserDto {
   @JsonView(value = { View.UserView.External.class })
   private Integer id;
   @JsonView(value = { View.UserView.External.class })
   private String firstName;
   @JsonView(value = { View.UserView.External.class })
   private String lastName;
   @JsonView(value = { View.UserView.Internal.class })
   private String ssn; 
   @JsonView(value = { View.UserView.Internal.class })
   private Instance dob;
   @JsonView(value = { View.UserView.Internal.class })
   private String mobileNo;
}
```

### use the view in Serializing / Deserializing 

```java
// for serialize 
objectMapper.writerWithView(View.UserView.Internal.class)
// for deserialize
objectMapper.readerWithView(View.UserView.Internal.class)
```

### Auto config with spring boot

```java 
@RestController
public class UserController {
   @GetMapping("/int/users")
   // Serialize response with Intenal View   
   @JsonView(value = View.UserView.Internal.class) 
   public List<User> getAllInternal() {
       return userService.getAllUsers();
   }
   @GetMapping("/ext/users")
   @ResponseStatus(code = HttpStatus.OK)
   // Serialize response with External View
   @JsonView(value = View.UserView.External.class)
   public List<User> getAllExternal() { 
        return userService.getAllUsers();
   }
}
```

--------------------------

#### references
- https://medium.com/@iamitpatil1993/jackson-jsonview-and-its-meaningful-use-with-spring-boot-rest-5fb2ad58dcfe
- sample: https://github.com/mohamedhalim1998/code-samples/tree/main/json-view