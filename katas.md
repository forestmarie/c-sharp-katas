#### yield return

When you use the yield keyword in a statement, you indicate that the method, operator, or get accessor in which it appears is an iterator. Using yield to define an iterator removes the need for an explicit extra class (the class that holds the state for an enumeration, see IEnumerator<T> for an example) when you implement the IEnumerable and IEnumerator pattern for a custom collection type.

Kata: Write a method that iterates over the integers 1 through 10 but breaks
once i becomes 5.

```
public IEnumerable<int> Consume()
{
  for(int i = 0; i < 10 ; i++)
  {
    if (i == 5)
      yield break;
    yield return i;
  }
}
```

#### structs

Kata: Write at least 4 characteristics of structs

* Structs can have methods, fields, indexers, properties, operator methods, and
  events
* C# does not allow structs to have initializers
* Structs can have defined constructors, but not destructors.
* Structs cannot have default/parameterless constructors.  It is implicitly
  defined and you cannot implement it yourself.
* Structs cannot be used as a base for other structs or classes
* Struct members cannot be specified as abstract, virtual or protected
* When you create a struct using the ```new ``` operator, it gets created and
  the appropriate ctor is called.  Unlike classes, structs can be instantiated
  without using the ```new``` operator.
* If the ```new``` operator is not used, the fields remain unassigned and the
  object cannot be used until all fields are initialized.

#### static constructors

Kata: Write at least 4 characteristics of static constructors

* A static ctor is used to initialize any static data or perform actions that
  need to be performed only once.
* A static constructor does not take access modifiers or have parameters
* A static constructor cannot be called directly
* A static constructor is called automatically to initialize the class before
  the first instance is created or any static members are referenced
* If a static ctor throws an exception, the runtime will not invoke it a second
  time, and the type will remain unitialized for the lifetime of the app domain
  in which your program is running.

#### String.Join

The string.Join method combines many strings into one. It receives two arguments:
an array or IEnumerable and a separator string. It places the separator between
every element of the collection in the returned string.

Kata: Create a single flattened string containing ```<br />``` behind every string
in a string array except the last element.

```
public void StringJoinFun()
{
  var employees = new [] {"Billy, "Bob", "Sue"};

  var employeesFlattened = string.Join("<br />", employees);

}
```

Kata 2: Think about how String.Join can more optimal than using a StringBuilder

#### Reflection

Kata 1: Create an extension method that returns an IEnumerable of all public
property information of a given object.  Provide the extension methods an
overload to pass in the binding flags.  The default method should assume all
public instance properties.


Kata 2: Same as Kata 1 except for methods instead of properties.

Kata 3: Extend the extension method from 1 and 2 with the ability to return
all attributes of a type.

Kata 4: Add an extension method to return information for all attributes that
are all methods of a type.  I.E, given a type with methods Foo and Bar both with attributes A,B,C your method would return something like:
{ {"Foo", {"A", "B", "C" }, { "Bar", {"A", "B", "C"}}}

Kata 5: Find all types in an assembly that implement a specific interface
