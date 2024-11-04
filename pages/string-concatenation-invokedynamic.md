# String Concatenation 

1. Using concatenation operator `+`
<!-- -->
```java
String welcomeMessage(String user) {
  return "Hello " + 
          user + 
          "! Welcome to OpenValue Vienna Meetup!";
}
```

<br>
<br>

2. Using `StringBuilder`
<!-- -->
```java
String welcomeMessage(String user) {
  return new StringBuilder()
          .append("Hello ")
          .append(user)
          .append("! Welcome to OpenValue Vienna Meetup!")
          .toString();
}
```

::right::

<br>
<br>
<br>
<br>
 <div v-click>
```yaml
0 aload_1
1 invokedynamic #53 <makeConcatWithConstants, BootstrapMethods #0>
6 areturn
```
</div>

<br>

<div v-click>

```yaml
 0 new #56 <java/lang/StringBuilder>
 3 dup
 4 invokespecial #58 <java/lang/StringBuilder.<init> : ()V>
 7 ldc #59 <Hello >
 9 invokevirtual #61 <java/lang/StringBuilder.append : (Ljava/lang/String;)Ljava/lang/StringBuilder;>
12 aload_1
13 invokevirtual #61 <java/lang/StringBuilder.append : (Ljava/lang/String;)Ljava/lang/StringBuilder;>
16 ldc #65 <! Welcome to OpenValue Vienna Meetup!>
18 invokevirtual #61 <java/lang/StringBuilder.append : (Ljava/lang/String;)Ljava/lang/StringBuilder;>
21 invokevirtual #67 <java/lang/StringBuilder.toString : ()Ljava/lang/String;>
24 areturn
```

</div>


<!--  -->
