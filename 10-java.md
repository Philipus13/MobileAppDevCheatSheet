### Abstract

contains both concrete and abstract methods

### Interface 

blueprint/contract of a class

### Composition (has-a relationship)

```java
Person {
   // Person has a job 
   Job job;
}
```

### Inheritance 
```java
class Animal {}
class Cat extends Animal {}
```

### Overloading (static polymorphism)

```java
class Printer {
   void display();
   void display(String message);
}
```

### Overriding (dynamic polymorphism)
```java
class Printer{
   void print();
}


DeskJetPrinter extends Printer{
   @Override
   void print();
}
```

### Overloading & Overriding - A different example 

```java
class Printer {
   static print() { sop("Static method of Printer") }
   printTest() { sop("Instance method of Printer") }
}

class DeskJetPrinter extends Printer {
   static print() { sop("Static method of DeskJetPrinter") }
   
   @Override
   printTest() { sop("Instance method of DeskJetPrinter") }
}

main(){
   DeskJetPrinter djp = new DeskJetPrinter()
   djp.printTest()
   
   Printer prt = djp
   prt.print()
   prt.printTest()
}

Output:   
Instance method of DeskJetPrinter   
Static method of Printer  
Instance method of DeskJetPrinter
```

### Access Modifiers 

- private
- protected
- default 
- public 

### Design Patterns 

Creational (builders, factory, Singleton, Monostate, Fluent Interface Patterns)
Structural (adapter, decorator, facade)   
Behavioural(chain of responsibility, iterator & strategy)

1. Creational builder                    

```java 
AlertDialog.Builder(this).setTitle().build()
```

2. Structural
 - adapter                    
 Recylerview.Adapter
 - facade                     
 Using interface in retrofit

3. Behavioural 

- chain of responsibility process request in chain 


### Variables

- Local -> methods
- Instance -> declared in class 
- class -> marked static

### transient

any object marked with this keyword will not be serialized

### volatile 

no caching in cpu, reads directly from memory. 

### final, finally and finalize

```java
class MemoryClass {
   @Override  
    protected void finalize()   
    {   
        System.out.println("finalize method called");   
    }   
}

// final variable can not be changed.
// final methods can not be overriden.
// final class can not extend.

try{}
finally{
   // catch is not necessary here 
}
```

### synchronized 

when multiple threads are accessing one object, each should access it one at a time. 

### ThreadPoolExecutor

creates a pool where thread can be executed and checked.
ThreadPoolExecutor returns a future object so which can be basically used to cancel the task. 

### AtomicBoolean (used in concurrency)

compare(), compareAndSet()

### Primitive & Wrapper 

- primitive -> boolean, byte, char, short, int, long, float and double
- wrapper   -> Boolean, Byte, Character, Short, Integer, Long, Float and Double

### Defaults 

- boolean -> false
- byte -> 0
- short -> 0
- int -> 0
- long -> 0L
- char -> \u0000
- float -> 0.0f
- double -> 0.0d
- object -> null

```
int a; // Initialized variable
a = 9; // Instantiation 
```

### String 

The String class is immutable, so that once it is created a String object cannot be changed,
in order to prevent malicious manipulation of data.

- String Constant Pool

  When string is assigned value using "", it looks into the String Pool 
  Constant. 
  If the value exists same reference is returned else a new Constant is 
  created and referenced is returned.

- Heap Space vs String Constant Pool 

  - Heap Space - A space which holds objects created using new keyword 
  - Constant Pool - A space which holds string objects created with 
    double quotes and non repetitive.
 
```java
main(){
   String s1 = "Cat"
   String s2 = "Cat"
   String s3 = new String("Cat");
        
   sop("s1 == s2 :"+(s1==s2));
   sop("s1 == s3 :"+(s1==s3));
}

// Output:
true 
false
```


 - String.intern()
1. checks for the same string exists in pool. 
2. if not, it is added and reference of the same is returned 

#### Example: 
```java

// This goes in Java Heap [ "Leo" ] & SCP [  ] is empty 
String s1 = new String("Leo") 

// Checks in SCP, creates a new constant in SCP [ "Leo" ]
String s2 = s1.intern()        
String s3 = "Leo"

// since both reference to different location 
// (1 in Heap and other in constant pool)
print(s1 == s2) // => false  
    
// comparing values
print(s1 .equals s2) // => true  

// since both are referring to same reference which is coming from SCP 
print(s2 == s3) // => true       

```

 - StringBuffer 

   Slow and thread safe

- StringBuilder 

  Fast and non thread safe

### Collections & Generics 

Arrays, ArrayLists, HashSet, TreeSet, HashMap, HashSet, Stack, Queues.

- #### Enumeration (forward only)   
  Enumeration is a legacy interface used to traverse only the legacy classes like Vector, HashTable and Stack.

- #### Iterator (forward only)   
  Can be used with any Collections objects and can add/remove.

- #### ListIterator (both direction)   
  Can add/remove and traverse in both direction with any list


### HashSet (no order)

No duplicates, can accept single null value  

### TreeSet (in order) 

same as above 

### HashMap (no order)

No duplicates, can accept single null as key 
works with key & value.

example:
 HashMap {1->”Hello”, 2->”Hi”, 3->”Bye”, 4->”Run”}

### TreeMap (ascending order by keys)

same as above 

### LinkedHashMap (maintains link order)

same as above 

### Stack 
```
Stack => [Jack, Queen, King, Ace]  
push(Leo)  //[Jack, Queen, King, Ace, Leo]
pop() => Leo // [Jack, Queen, King, Ace]   
peek() => Ace  
Current Stack => [Jack, Queen, King, Ace]
```

### Queue (FIFO)

add, peek, remove(removes the head)

### CountDownLatch

when you are working with multiple thread and you want them to flag you when they finish or 
want to hold the block of execution until all finish. 
```
Thread(latch){
   run(){
      Thread.sleep(10_000)
      latch.countDown()
   }
}

latch = CountDownLatch(1) // Thread count
new Thread(latch)
latch.await()        // waits infinitely till the thread flags 
or 
latch.await(2 sec)   // waits till the specified time
```
