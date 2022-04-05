# Groovy

Groovy is a *dynamic object-oriented (scripting) language* that combines the best from Smalltalk, Python and Ruby
in an all-in-one package using a *Java-like syntax*. Groovy is *100 % Java* and compiles scripts 
straight to Java bytecode that *run on any Java virtual machine*. 
Groovy offers seamless and smooth Java integration: from Groovy you can *access all Java libraries*, 
you can build applets or Java beans, you can derive from Java classes in Groovy and vice versa. 

* Groovy is the Next Generation Java
* Groovy is Java for the 21st Century



### First Impression - Servus Groovy Example

Groovy

```
$ groovy -e "print 'Servus Groovy'"
=> Servus Groovy
```

Java (`ServusGroovy.java`):

```
public class ServusGroovy
{
  public static void main( String args[] )
  {
     System.out.println( "Servus Groovy" );
  }
}
```

```
$ javac ServusGroovy.java
$ java ServusGroovy
=> Servus Groovy
```




### Second Impression - Higher-Level Functions, Loops and Data Types

Groovy (`HelloWorld.groovy`):

```
 1. def country = [ "Canada", "Austria", "Brazil" ]
 2. 
 3. country.sort()
 4. 
 6. country.each { it -> println "Hello ${it}" }
```

```
$ groovy HelloWorld.groovy
=> Hello Austria
=> Hello Brazil
=> Hello Canada
```

or

```
$ groovyc HelloWorld.groovy
$ java HelloWorld
```


Java (`HelloWorld.java`):

```
 1. import java.util.*;
 2.
 3. public class HelloWorld
 4. {
 5.  public static void main( String args[] )
 6.  {
 7.    List country = new ArrayList();
 8.    country.add( "Canada" );
 9.    country.add( "Austria" );
10.    country.add( "Brazil" );
11.
12.     Collections.sort( country );
13.
14.     for( Iterator it = country.iterator(); it.hasNext(); )
15.        System.out.println( "Hello " + it.next() );
16.  }
17. }
```


### Third Impression - Groovy Beans vs Java Beans

Groovy

```
 1. class Country
 2. {
 3.  String name
 4.  String capital
 5. }
 6.
 7. def world = [new Country(name:"Austria", capital:"Vienna"),
 8               new Country(name:"Canada", capital:"Ottawa")]
 9.
10. world.each { country -> println "The capital of ${country.name} is ${country.capital}." }
```


Java 

```
 1. import java.util.*;
 2.
 3. public class Country
 4. {
 5.  private String name;
 6.  private String capital;
 7.
 8.  public String getName()    { return name; }
 9.  public String getCapital() { return capital; }
10.
11.  public void setName( String name ) { this.name = name; }
12.  public void setCapital( String capital ) { this.capital = capital; }
13.
14.  public static void main( String args[] )
15.  {
16.    Country austria = new Country();
17.    austria.setName( "Austria" );
18.    austria.setCapital( "Vienna" );
19.
20.    Country canada = new Country();
21.    canada.setName( "Canada" );
22.    canada.setCapital( "Ottawa" );
23.
24.    List world = new ArrayList();
25.    world.add( austria );
26.    world.add( canada  );
27.
28.    for( Iterator it = world.iterator(); it.hasNext(); )
29.    {
30.      Country country = (Country) it.next();
31.      System.out.println( "The capital of " + country.getName() + " is " +  country.getCapital() + "." );
32.    }     
33.  }
34. }
```


### Why Groovy? What's wrong with Ruby (JRuby), Python (Jython), or Smalltalk (Bistro)?


Why yet another scripting language?

1. Groovy uses a Java-like syntax; easy to switch from Java to Groovy or from Groovy to Java
2. Groovy builds on (reuses) the Java standard class library; Ruby, Python or Smalltalk include their own batteries (that is, standard libraries)
3. Groovy compiles straight to standard Java bytecode; you can use `groovyc` as an alternative compiler to `javac`

What is Java? 

1. Java is a (systems) programming language (syntax).
2. Java is a "standard" class library.
3. Java is a bytecode runtime (virtual machine).

=> Groovy is Java


### Application vs. Systems (Hard-Core) Programming / Groovy vs. Java

Groovy does **not** replace Java. Groovy complements Java and doesn't compete head-on. Groovy is a 
dynamic (scripting) language for application development. 
Java is a programming language for (hard-core) systems development.

* **No compilation** (Fast Build-Cycle Turnaround)
* **Dynamic Typing** (No Need to Declare Variables For Use)
* **Easy Syntax** (Higher Level Datatypes, Functions and Loops, Semicolons and Return Optional, and more)
* **Embedabble** (Scripting Power for Your Apps)
* **Interactive** (Create, View, Change Objects At Run-Time)

<!-- -->

* **50 % less code**
* **2 to 3 times higher productivity (that is, less development time)**
 


### Groovy is Java 

Groovy Standard Class Library Types == Java Standard Class Library Types

* A Groovy String is a Java String

```
$ hello = "Hello"
$ hello.class
=> java.lang.String
```

* A Groovy List is a Java List

```
$ list = [ "Vancouver", "Ottawa" ]
$ list.class
=> java.util.ArrayList
```

* A Groovy Map is a Java Map

```
$ map = [ "Vancouver":"British Columbia", "Ottawa":"Ontario" ]
$ map.getClass()
=> java.util.LinkedHashMap
```

* A Groovy Regex is a Java Regex

```
$ regex = ~/[a-zA-Z_0-9]+/
$ regex.class
=> java.util.regex.Pattern
```


### Groovy is Java Continued: Annotations

```
@Entity
@Name("hotel")
class Hotel implements Serializable
{
     @Id @GeneratedValue
     Long id
 
     @Length(max=50) @NotNull
     String name
 
     @Length(max=100) @NotNull
     String address
 
     @Length(max=40) @NotNull
     String city
 
     @Length(min=2, max=10) @NotNull
     String state
 
     @Length(min=4, max=6) @NotNull
     String zip
 
     @Length(min=2, max=40) @NotNull
     String country
 
     @Column(precision=6, scale=2)
     BigDecimal price
 
     @Override
     String toString() {
         return "Hotel(${name}, ${address}, ${city}, ${zip})"
     }
}
```

(Source: [What's New in Groovy 1.5](http://www.infoq.com/articles/groovy-1.5-new))

### Groovy is Java Continued:  Enums, Static Imports, Generics

```
class Talk {
     String title
}
class Speaker {
     String name
     List<Talk> talks = []
}
def me = new Speaker(
     name: 'Guillaume Laforge',
     talks: [
         new Talk(title: 'Groovy'),
         new Talk(title: 'Grails')
     ])
 
def talksField =  me.class.getDeclaredField('talks')
assert talksField.genericType.toString() == 'java.util.List<Talk>'
```

(Source: [What's New in Groovy 1.5](http://www.infoq.com/articles/groovy-1.5-new))

### Groovy Joint Compiler

Compiles Groovy and Java code; can handle any dependency cycles

Use the `-j` compiler switch to enable the joint compilation. Example:

Country.groovy:

```
class Country
{
   String name
   String capital
   String toString() { return "The capital of ${name} is ${capital}." }
}
```

World.java:

```
public class World
{
  public static void main( String args[] )
  {
    Country canada = new Country();
    
    canada.setName( "Canada" );
    canada.setCapital( "Ottawa" );
    System.out.println( canada.toString() );
  }
}
```

Let's joint compile the Groovy and Java source.

```
$ groovyc -j Country.groovy World.java 
```

That's it. Run it.

```
$ java World
=> The capital of Canada is Ottawa.
```

Voila.


### Groovy Goodies Missing In Java

* built-in syntax for lists, maps, regex and ranges (e.g (`1..1000`)) (=higher level data types)
* built-in syntax for markup (XML)
* higher-level functions and loops (=closures/code blocks)
* built-in Velocity-style/XPath-style expression for Java bean acess (e.g. `${movie.director.name}`)
* many new helper methods added to core Java classes (e.g. `any`, `each`, `findAll`, `print` and more)
* operator overloading (e.g. `[1,2,3]+[3,4,5]`, `map['one']`)
* everything is an object (e.g. no need for boxing and unboxing)
* metaprogamming (MOP - Meta Object Protocol e.g. `method_missing`) (="easy" on-the-fly code generation)
* and much more!

### Groovy Lists: Built-In Syntax for Lists

Groovy

```
list = [1, 2, 3]
```

Java

```
List list = new LinkedList();
list.add( new Integer( 1 ) );
list.add( new Integer( 2 ) );
list.add( new Integer( 3 ) );
```


### Groovy Maps: Built-In Syntax for Maps

Groovy

```
map = [ 'one' : 1, 'two' : 2, 'three': 3 ]
print map[ 'one' ]
print map.one // works too
```

Java

```
Map map = new HashMap();
map.put( "one", new Integer( 1 ) );
map.put( "two", new Integer( 2 ) );
map.put( "three", new Integer( 3 ) );
System.out.println( map.get( "one" ) );
```


### More Groovy List and Map Examples

Empty List

```
list = []
```

Empty Map

```
map = [:]
```

Nested Lists

```
list = [1, 2, [4, 5], 'hello']
```

Negative (Reverse) Index

```
last = list[-1] 
```

Ranges

```
list = 1..100
sub  = list[1..20]
sub  = list[-5..-1]
sub  = list[1,5..10,15]
```

Operator Overloading

```
[1,2,3] + [4,5,6]    // returns [1,2,3,4,5,6]
[1,2,3,4] - [2,4,6]  // returns [1,3]
map[ 'one' ]
```

Many Helper Methods

```
[1,2,3,1,2,3].count(3)  // return 2
['one', 'two', 'three'].join( '+' )
[3,2,1].sort()
```


### Groovy Loops: Higher-Level Loops Using Closures (Code Blocks)

Java

```
for( int i=1; i<=1000; i++ )
  System.out.println( "The lucky number is" + i + "today" );
```

Groovy

each

```
(1..1000).each { i -> println "The lucky number is ${i} today" }
```

or

```
(1..1000).each { println "The lucky number is ${it} today" }
```

upto

```
1.upto(1000) { println "The lucky number is ${it} today" }
```

step

```
1.step(1001,1) { println "The lucky number is ${it} today" }
```

times

```
1000.times { println "Groovy rocks big time!" }
```



### What is a Closure (Code Block/Anonymous Function)? 

Closures are a powerful way of passing around blocks of executable code (code blocks/functions).
Think of a closure as an anonymous inner method/function that can accept parameters.

```
{ x -> println x }   // closure with parameter x
{ println it }       // closure with default parameter it
{ x, y -> x > y }    // closure with parameter x, y
{ println "Hello" }  // closure without parameters
squared_closure = { x -> x * x }   // store closure in a variable 
squared_closure.call( 2 ) // call closure like a method; returns 4
squared_closure( 2 )      // v2.0: call closure like a method 
```

Functions (Closures/Code Blocks) as First-Class Citizens:

* Store functions in variables
* Pass functions to functions as arguments
* Call functions stored in variables (or passed in as arguments)



### Closures In Action: Groovy Collections vs. Plain Old Java Collections

Groovy

```
   1. def names = ["Ted", "Fred", "Jed", "Ned"]  
   2. println names  
   3.   
   4. def shortNames = names.findAll { it.size() <= 3 }  
   5. println shortNames.size()  
   6. shortNames.each { println it }  
```

Java

```
   1. import java.util.*;  
   2.   
   3. public class Erase {  
   4.     public static void main(String[] args) {  
   5.         List names = new ArrayList();  
   6.         names.add("Ted");  
   7.         names.add("Fred");  
   8.         names.add("Jed");  
   9.         names.add("Ned");  
  10.         System.out.println(names);  
  11.         Erase e = new Erase();  
  12.         List shortNames = e.filterLongerThan(names, 3);  
  13.         System.out.println (shortNames.size());  
  14.         for (Iterator i = shortNames.iterator(); i.hasNext(); ) {  
  15.             String s = (String) i.next();  
  16.             System.out.println(s);  
  17.         }  
  18.     }  
  19.   
  20.     public List filterLongerThan (List strings, int length) {  
  21.         List result = new ArrayList();  
  22.         for (Iterator i  = strings.iterator(); i.hasNext(); ) {  
  23.             String s = (String) i.next();  
  24.             if (s.length() < length+1) {  
  25.                 result.add(s);  
  26.             }  
  27.         }  
  28.         return result;  
  29.     }  
  30. }
```

Java Refactored

```
   1. import static java.lang.System.out;  
   2. import static java.util.Arrays.asList;  
   3. import java.util.ArrayList;  
   4. import java.util.List;  
   5. import org.apache.commons.collections.CollectionUtils;  
   6. import org.apache.commons.collections.Predicate;  
   7.   
   8. public class ListTests {  
   9.    public static void main( String[] args ) {  
  10.       List<String> names = asList( "Ted", "Fred", "Jed", "Ned" );  
  11.       out.println( names );  
  12.       List<String> shortNames = new ArrayList<String>();  
  13.       shortNames.addAll( names );  
  14.       CollectionUtils.filter( shortNames, new Predicate(){  
  15.          public boolean evaluate( Object input ) {  
  16.             return ((String) input).length() < 4;  
  17.          }  
  18.       } );  
  19.       out.println( shortNames.size() );  
  20.       for( String s : shortNames )  
  21.          out.println( s );  
  22.    }  
  23. }  
```

(Source: [From Java to Groovy, Part 2: Closures and Built-In Syntax For Lists](http://groovy.dzone.com/news/java-groovy-part-2-closures-an))


### Higher-Level Loops and Functions For Maps And Lists

each

```
[5, 9, 1, 6].each { println it }
```

find

```
[5, 9, 1, 6].find { x -> x > 5 }    // returns 9
```

findAll

```
[5, 9, 1, 6].findAll { x -> x > 5 }  // returns [9, 6]
```

map

```
[5, 9, 1, 6].map { x -> x * 2 }   // returns [10, 18, 2, 12]
```

min / max

```
[5, 9, 1, 6].min()   // returns 1
[5, 9, 1, 6].max()   // returns 9
```

reverse

```
[1,2,3].reverse()   // returns [3,2,1]
```


### Groovy JDK - Groovy Adds New Methods To Core Java Classes 

Groovy adds new methods to the core Java classes to help productivity and polymorphism
e.g. new closure methods: `each`, `select`, `filter`, `collect`

#### java.util.Collection

|      |                                    |
|------|------------------------------------| 
| int  |	**count**(java.lang.Object value) |
| void |	**each**(groovy.lang.Closure closure) |
| java.lang.Object |	**find**(groovy.lang.Closure closure) |
| java.util.List |	**findAll**(groovy.lang.Closure closure)  |
| java.util.List |	**getAt**(java.lang.String property)  |
| java.lang.String | 	**join**(java.lang.String separator)  |
| java.util.List   |	**map**(groovy.lang.Closure closure)  |
| java.lang.Object |	**max**(java.util.Collection self)    |
| java.lang.Object |	**max**(java.util.Comparator comparator) |
| java.lang.Object |	**max**(groovy.lang.Closure closure)  |
| java.lang.Object |	**min**(java.util.Collection self) |
| java.lang.Object |	**min**(java.util.Comparator comparator)  |
| java.lang.Object |	**min**(groovy.lang.Closure closure)  |
| java.util.List   |	**plus**(java.util.Collection right)  |
| java.util.List   |	**plus**(java.lang.Object right)     |

and many more

#### java.io.File

|      |                                    |
|------|------------------------------------| 
| void | 	**eachByte**(groovy.lang.Closure closure) |
| void |	**eachFile**(groovy.lang.Closure closure) |
| void |	**eachLine**(groovy.lang.Closure closure) |
| void |	**splitEachLine**(java.lang.String sep, groovy.lang.Closure closure)  |
| void |	**withOutputStream**(groovy.lang.Closure closure)  |
| void |	**withPrintWriter**(groovy.lang.Closure closure)  |
| void |	**withReader**(groovy.lang.Closure closure) |
| void |	**withWriter**(groovy.lang.Closure closure) |

and many more

#### java.lang.Number

|      |                                    |
|------|------------------------------------| 
| java.lang.Number | 	**minus**(java.lang.Number right) |
| java.lang.Number |	**multiply**(java.lang.Number right) |
| java.lang.Number |	**plus**(java.lang.Number right)  |
| java.lang.Number |	**power**(java.lang.Number exponent)  |
| void |	**step**(java.lang.Number to, java.lang.Number stepNumber, groovy.lang.Closure closure) |
| void |	**times**(groovy.lang.Closure closure)  |
| void |	**upto**(java.lang.Number to, groovy.lang.Closure closure)  |

and many more

#### java.lang.Object

|      |                                    |
|------|------------------------------------| 
| boolean  |	**any**(groovy.lang.Closure closure) |
| void  |	**each**(groovy.lang.Closure closure)  |
| boolean  | 	**every**(groovy.lang.Closure closure)  |
| java.lang.Object  | 	**find**(groovy.lang.Closure closure)  |
| java.lang.Object  |	**findAll**(groovy.lang.Closure closure)  |
| java.lang.Object  |	**invokeMethod**(java.lang.String method, java.lang.Object arguments)  |
| java.util.List    | 	**map**(groovy.lang.Closure closure)  |
| void |	**print**(java.lang.Object value) |

and many more 

(Source: [Groovy Class Library Reference (Groovy JDK)](http://groovy.codehaus.org/groovy-jdk/))


### Groovy Template Strings: Expressions In Strings

You can put Groovy expressions (including method calls) inside strings using the `${expression}` syntax
similar to Velocity or JSTL-EL.

Groovy

```
movie    = "Lost in Translation"
director = "Sofia Coppola"
println "${director} directed the movie ${movie}."
```

Java Flashback

```
String movie    = "Lost in Translation";
String director = "Sofia Coppola";
System.out.println( director + " directed the movie " + movie + "." );
```

Groovy

```
num = 4
println "${num} squared equals ${num*num}"
class Movie
{
  String title
  Person director
}
class Person
{
  String name
}
person = new Person( name:'Sofia Coppola' )
movie = new Movie( title:'Lost in Translation', director:person )
println "${movie.director.name} directed the movie ${movie.title}"
// ${movie.director.name} is the same as movie.getDirector().getName() in Java
```



### Groovy Strings: Multi-Line/Here-Doc Strings And More

In Groovy you can start and end strings with single or double quotes
and use the other kind of quote without escaping inside the string. Example:

```
println "Alice says, 'Groovy rocks.'"
println 'Alice says, "Groovy rocks."'
```

Multi-Line Strings/Here-Doc Strings

In Groovy you can create multi-line strings
using the triple quote (`"""` or `'''`) syntax that
lets you paste blocks of text into your source without any need for quotes.
Example:

```
out = """
<html>
 <head>
   <title>Groovy Servlet</title>
 </head>
 <body>
  Hello, ${request.remoteHost}: ${session.counter}! ${new Date()} 
 </body>
</html>
"""
```


### Groovy Path Expression Language

To avoid the risk of `NullPointerException` when walking object hierachies
you can use the "`?.`"operator instead of "`.`".

```
class Movie
{
  String title; Person director
}
class Person
{
  String name
}
movie = new Movie( title:'Leaving Las Vegas' )
// Doesn't throw NullPointerException
println "${movie.director?.name} directed the movie ${movie.title}"
// Throws NullPointerException
println "${movie.director.name} directed the movie ${movie.title}"
```

Not for Groovy strings only. You can use the Groovy path expression language (including closures) everywhere. Example:

```
if( customers.orders.any { it.amount > 1000 && it.product.type == "citrus" } ) 
{
  doSomething()
}
```

or

```
for( order in customers.findAll { it.country.code == "AT" }.orders ) 
{
  println "order ${order.id} has value ${order.value}"
} 
```

### Groovy Markup (XML) Syntax

Alternative XML syntax similar to Groovy map and list syntax but for trees of anything. Example:

```
import groovy.xml.MarkupBuilder;
xml = new MarkupBuilder()
xml.xul() {
  menubar( id:"main" ) {
    menu( label:"Bookmarks" ) {
      menuitem( label:"Vancouver Groovy/Grails User Group", link:"http://groovyvan.com" )
      menuitem( label:"Gerald Bauer's Blog", link:"http://geraldbauer.wordpress.com" )
      menuitem( label:"Gerald Bauer's Tumblelog", link:"http://geraldbauer.tumblr.com" )
      menuitem( label:"Slide Show (S9)",  link:"http://slideshow.rubyforge.org" )
    }
  }
}   
println xml
```

generates the following XML markup:

```
<xul>
  <menubar id="main">
     <menu label="Bookmarks">
       <menuitem label="Vancouver Groovy/Grails User Group"  link="http://groovyvan.com" />
       <menuitem label="Gerald Bauer's Blog" link="http://geraldbauer.wordpress.com" />
       <menuitem label="Gerald Bauer's Tumblelog"    link="http://geraldbauer.tumblr.com" />
       <menuitem label="Slide Show (S9)"            link="http://slideshow.rubyforge.org" />
     </menu>
  </menubar>
</xul>
```

Note that you can mix and match Groovy markup with Groovy script
(e.g. loops, method calls, variables, expressions, conditionals and so on). 

### Groovy SQL


Groovy Script using Groovy SQL and Groovy Markup

```
import groovy.xml.MarkupBuilder;
import groovy.sql.Sql
import java.sql.DriverManager
Class.forName( "org.hsqldb.jdbcDriver" )
con = DriverManager.getConnection( "jdbc:hsqldb:.", "sa", "" )
sql = new Sql( con )
xml = new MarkupBuilder()
xml.xul() {
  menubar( id:'main' ) {
    menu( label:'Bookmarks' )
    sql.queryEach( 'select title, link from bookmark' ) { row ->
         menuitem( label:"${row.title}", link:"${row.link}" )
    }
  }
}
println xml
```

Output

```
<xul>
  <menubar id="main">
     <menu label="Bookmarks">
       <menuitem label="Vancouver Groovy/Grails User Group"  link="http://groovyvan.com" />
       <menuitem label="Gerald Bauer's Blog" link="http://geraldbauer.wordpress.com" />
       <menuitem label="Gerald Bauer's Tumblelog"    link="http://geraldbauer.tumblr.com" />
       <menuitem label="Slide Show (S9)"            link="http://slideshow.rubyforge.org" />
     </menu>
  </menubar>
</xul>
```

### Scripting Ant Using Groovy Markup (Gant)

Using Gant you can use Ant tasks and mix and match markup with scripts
(e.g. you can pass on variables to Ant tasks and use Groovy code anywhere within the markup).

```
sourceDirectory = 'source'
buildDirectory = 'build'
includeTargets << gant.targets.Clean
cleanPattern << '**/*~'
cleanDirectory << buildDirectory
Ant.taskdef (  name : 'groovyc' , classname : 'org.codehaus.groovy.ant.Groovyc' )
target ( compile : 'Compile source to build directory.' ) {
   javac ( srcdir : sourceDirectory , destdir : buildDirectory , debug : 'on' )
   groovyc ( srcdir : sourceDirectory , destdir : buildDirectory )
}
```

(Source: [Gant Project Site](http://gant.codehaus.org))


### Building Swing Desktop Apps Using Groovy Markup

Groovy snippet:

```
 1. swing = new SwingBuilder()
 2. 
 3. frame = swing.frame( title:'Counter', size:[200,100]) {
 4.   panel(layout:new FlowLayout() ) {
 5.     display = textField( preferredSize:[200,30], horizontalAlignment:SwingConstants.CENTER )
 6.     button( text:"Inc", size:[65,70], actionPerformed:{ value++; setDisplay() } )
 7.     button( text:"Clear", size:[65,70], actionPerformed:{ value=0; setDisplay() } )
 8.     button( text:"Dec", size:[65,70], actionPerformed:{ value--; setDisplay() } )
 9.   }
10. }        
```

Java edition:

```
 1. frame = new JFrame( "Counter" );
 2. frame.getContentPane().setLayout( new FlowLayout() );
 3. frame.setSize( 200, 100 );
 4.
 5. display = new JTextField();
 6. display.setPreferredSize( new Dimension( 200, 300 );
 7. display.setHorizontalAlignment( SwingConstants.CENTER );
 8. frame.getContentPane().add( display );
 9.
10.  increment = new JButton( "Inc" );
11.  increment.setSize( 65, 70 );
12.  increment.addActionListener( new ActionListener() {
13.    public void actionPerformed( ActionEvent ev )
14.    {
15.       onIncrement();
16.    }
17.  } );
18.  frame.getContentPane().add( increment );
19.
20.  clear = new JButton( "Clear" );
21.  clear.setSize( 65, 70 );
22.  clear.addActionListener( new ActionListener() {
23.    public void actionPerformed( ActionEvent ev )
24.    {
25.      onClear();
26.    }
27.  } );
28.  frame.getContentPane().add( clear );
29.
30.  decrement = new JButton( "Dec" );
31.  decrement.setSize( 65, 70 );
32.  decrement.addActionListener( new ActionListener() {
33.    public void actionPerformed( ActionEvent ev )
34.    {
35.      onDecrement();
36.    }
37.  } );
38.  frame.getContentPane().add( decrement );
```    


### Groovy in Action 

From Industry Giants...

* [IBM Project Zero](http://projectzero.org) (WebSphere for the 21st Century/The Next Generation WebSphere)
* [SAP NetWeaver - Composition On Grails](https://wiki.sdn.sap.com/wiki/display/Community/Composition+on+Grails)

...to Let's Build a Blog in 5 Minutes

* [GroovyBlogs.org](http://code.google.com/p/groovyblogs/) - Open Source Groovy Powered  Collective Blog Engine by Glen Smith
* [Gravl](http://code.google.com/p/gravl) - Open Source Groovy Powered Blog Engine by Glen Smith  



### Groovy Heroes - G2One Inc. - The Groovy/Grails Startup

G2One Inc. - [G2One.com](http://g2one.com)

Founders include:

* Guillaume Laforge (Groovy Project Lead) 
* Graeme Rocher (Grails Project Lead)

Similar to Sun (Java), SpringSource (Spring), RedHat (JBoss), IBM (Eclipse), etcetera



### Groovy/Grails in Print - Books

* **The Definitive Guide to Grails** (Apress) by Graeme Rocher (384 pages, ISBN: 1-59059-758-3), December 2006
* **Groovy in Action** (Manning) by Dierk Koenig with Andrew Glover, Paul King, Guillaume Laforge and Jon Skeet (696 pages, ISBN: 1-932394-84-2), January 2007
* **Groovy Recipes**: Greasing the Wheels of Java (Pragmatic Bookshelf) by Scott Davis (264 pages, 
ISBN: 978-0-9787392-9-4), February 2008
* **Programming Groovy**: Dynamic Productivity for the Java Developer (Pragmatic Bookshelf) by Venkat Subramaniam (200 pages, ISBN: 978-1-9343560-9-8), March 2008

Upcoming

* **Practical Grails Projects** (Apress) by Christopher M. Judd , Joseph Faisal Nusairat, Jim Shingler (350 pages, ISBN: 1-59059-974-8)
* **The Definite Guide to Grails**, 2nd Edition (Apress) by Graeme Rocher, Scott Davis (600 pages, ISBN: 1-59059-995-0)


### Groovy/Grails Articles & Blogs

* IBM DeveloperWorks Series: Mastering Grails by Scott David
  * [Build your first Grails application](http://www.ibm.com/developerworks/java/library/j-grails01158)
  * [GORM: Funny name, serious technology](http://www.ibm.com/developerworks/web/library/j-grails02128) - Understanding databases and Grails

<!-- -->

* IBM DeveloperWorks Series: Practically Groovy by Andrew Glover
  * [Mark it up with Groovy Builders](http://www.ibm.com/developerworks/java/library/j-pg04125)
  * [Reduce code noise with Groovy](http://www.ibm.com/developerworks/java/library/j-pg09196.html)
  * [JDBC programming with Groovy](http://www.ibm.com/developerworks/java/library/j-pg01115.html)
  * [Unit test your Java code faster with Groovy](http://www.ibm.com/developerworks/java/library/j-pg11094)

<!-- -->

* [Groovy Dzone](http://groovy.dzone.com)
  * [From Java to Groovy in a Few Easy Steps](http://groovy.dzone.com/news/java-groovy-few-easy-steps) by Guillaume Laforge
  * [Introduction to Groovy](http://groovy.dzone.com/articles/introduction-groovy) by Andres Almiray 
  * [GraphicsBuilder Tutorial: Paints & Colors](http://groovy.dzone.com/articles/graphicsbuilder-tutorial-iii-p) by Andres Almiray 
  * [EasyB: Introducing Conversational Unit Tests for Java](http://groovy.dzone.com/news/easyb-introducing-conversation) - Q&A with Andrew Glover
  * [Groovy & Eclipse: Lead Plugin Developer Speaks](http://groovy.dzone.com/news/groovy-eclipse-lead-plugin-dev) - Q&A with Ed Povazan 

<!-- -->

* [InfoQ Groovy](http://infoq.com/groovy)
  * [What's New in Groovy 1.5](http://www.infoq.com/articles/groovy-1.5-new) by Guillaume Laforge
  * [Securing a Grails Application with Acegi Security](http://www.infoq.com/articles/grails-acegi-integration) by Fadi Shami
  * [Getting Started with Grails](http://www.infoq.com/minibooks/grails) by Jason Rudolph

<!-- -->

* [GroovyBlogs](http://groovyblogs.org)


### Groovy/Grails Experience (2GX) Conference 

Talk Highlights

* Powerful Metaprogramming Techniques With Groovy by Jeff Brown 
* The Whole 9 Yards: Things you can do in 10 Minutes w/ Grails that will Make Users Love You by Glen Smith
* Five Groovy/Grails Web Applications You Can Write in Two Days by Steven Devijver 
* The Grails Plug-in System: Plug into Productivity by Graeme Rocher 
* Empowering Spring with Groovy Domain-Specific Languages (DSLs) by Graeme Rocher
* GORM - Object Relational Mapping with Hibernate De-mystified Graeme Rocher 
* Testing with Groovy by Venkat Subramaniam 
* Easy Behavior-Driven Development (BDD) with EasyB by Andrew Glover
* and many more

Next [Groovy/Grails Experience](http://groovygrails.com) (2GX) Conference in San Jose (California) in Fall 2008


### Getting Started - Installing Groovy - 1-2-3 Steps

1. Download and unzip Groovy archive from [`groovy.codehaus.org`](http://groovy.codehaus.org/Download)
2. Set `GROOVY_HOME` environment variable
3. Add `%GROOVY_HOME%/bin` to `PATH`

### Hello Groovy

```
$ groovy --version
=> Groovy Version: 1.5.4 JVM: 10.0-b19
```

```
$ groovy -e "println 'Servus Groovy'"
=> Servus Groovy
```

Hello.groovy:

```
println "Servus Groovy"</pre>
```

```
$ groovy Hello.groovy
=> Servus Groovy
```

### The End - Q&A - Thanks
