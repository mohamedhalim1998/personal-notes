# Context

- It is the context of the current state of the application.
- It can be used to get information regarding the activity and application.
- It can be used to get access to resources, databases, and shared preferences, and etc.

### **Aplication Context**

This context is tied to the lifecycle of an application.

used where you need a context whose lifecycle is separate from the current context

Example Use: singleton object If you pass the activity context here, it will lead to the memory leak as it will keep the reference to the activity and activity will not be garbage collected.

### Activity Context

This context is tied to the lifecycle of an activity

Example Use: If you have to create an object whose lifecycle is attached to an activity

