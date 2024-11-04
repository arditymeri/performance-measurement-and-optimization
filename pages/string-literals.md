# Java Examples - String literals

1. One string literal

```java
String welcomeMessage = "Hello everyone! Welcome to the OpenValue Meetup!";
```

<br>

2. Concatenate string literals 
<!-- Concatenate string literals -->
```java
String welcomeMessage = "Hello" + " everyone" + "! Welcome to" + " the OpenValue Meetup" + "!";
```

<br>

3. Using `StringBuilder`
<!-- Using string builder-->
```java
String welcomeMessage = new StringBuilder()
        .append("Hello")
        .append(" everyone")
        .append("! Welcome to")
        .append(" the OpenValue Meetup")
        .append("!")
        .toString();

```

<!-- Find two java code examples and ask people what is more performant -->