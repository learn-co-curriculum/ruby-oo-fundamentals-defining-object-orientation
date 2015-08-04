# Object Orientation

## Objectives

1. Introduce the concept of Object Oriented Programming (OOP)
2. Understand the definition of a class and an instance in OOP
3. Understand that methods enable objects to have attributes and behaviors.
4. Learn how to define a class and initialize instances of that class
5. Learn about instance methods vs. class methods


## Object-Oriented Programming (OOP)

*An object-oriented approach to application development makes programs more intuitive to design, faster to develop, more amenable to modification, and easier to understand.*  
—[*Object-Oriented Programming with Objective-C*][apple_oop_guide_intro], Apple Inc.

[apple_oop_guide_intro]: https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/OOP_ObjC/Introduction/Introduction.html#//apple_ref/doc/uid/TP40005149-CH1-SW2

It's natural to wonder, "how can a string of ones and zeroes be referred to as an 'object'?" The use of the word "object" is an abstraction of thought. An "object" in code has no more physical form than does a word in any human language. Sure, words have physical representations: speaking a word causes air to vibrate in a sound wave, ink on a page can be shaped into symbols that represent the word, a meaning can be pointed at or mimed out; but none of these are the word itself. Human language is a system of abstraction: it communicates the *idea* of a thing, but not the thing itself.

![](https://upload.wikimedia.org/wikipedia/en/b/b9/MagrittePipe.jpg)  
—[*The Treachery of Images*][not_a_pipe], [René Magritte][magritte], 1927  
trans. "This is not a pipe."

[not_a_pipe]: https://en.wikipedia.org/wiki/The_Treachery_of_Images
[magritte]: https://en.wikipedia.org/wiki/Ren%C3%A9_Magritte

This image of a pipe is no more a pipe than the word "pipe" is a pipe; in the same way, a code object named `pipe` is not a pipe, but only another form of representing a pipe.

>As humans, we’re constantly faced with myriad facts and impressions that we must make sense of. To do so, we must abstract underlying structure away from surface details and discover the fundamental relations at work. Abstractions reveal causes and effects, expose patterns and frameworks, and separate what’s important from what’s not. Object orientation provides an abstraction of the data on which you operate; moreover, it provides a concrete grouping between the data and the operations you can perform with the data—in effect giving the data behavior.  
>—[*Object-Oriented Programming with Objective-C*][apple_oop_guide_oop], Apple Inc.

[apple_oop_guide_oop]: https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/OOP_ObjC/Articles/ooOOP.html#//apple_ref/doc/uid/TP40005149-CH8-SW3

A code object representing a water pipe (instead of a smoking pipe) might contain values for `length`, `diameter`, `material`, and `manufacturer`. The bundling of these individual pieces of information together begins to form a larger whole.

Object-Oriented Programming, however, does more than just bundling up individual pieces of data that represent a "thing"—it also bundles customized functions that can be performed *on* that data. These are called **methods**: behaviors that an object performs upon its internal data and even upon other code objects. 


### Object Orientation: A Brief History


Back in the day, we had procedural programming. 

######Example (in BASIC)
```
READY
10 PRINT "Hello there."
20 INPUT "Do you like me? (Type y or n)"; ans$
30 IF ans$ = "n" then GOTO 50
40 END "Cool. I like you too!"
50 PRINT "Maybe you didn't understand the question. Let me ask it again."
60 GOTO 20
```

Later, programmers made a transition to naming blocks of code, which became known as functions or methods. All of a sudden instead of going to a specific line number we could say something that was somewhat english-y to tell the program what code we wanted to run next and call it by name.

######Example (in C)

```
void DisplayWhoIAm(){
    printf("I am the writer of this tutorial!");
}
```

With this trend towards digital life really reflecting our real lives, object-oriented programming was born. In the 1970's, [Alan Kay](https://en.wikipedia.org/wiki/Alan_Kay) developed an object-oriented language at Xerox Parc called Small Talk, the language to be used in the first personal computer. 


## Object Definition and Behavior

In object-oriented programming, we think of discrete units of code as objects. You can think of your code as being alive––it is a concrete entity with attributes and behaviors. We "encapsulate" (think: box up) all of these related behaviors and properties in one place, and then give it a name, the name of the object. The box we keep all of these behaviors and properties in is our **Class**. It serves as the instruction manual or factory to create a specific type of object.

Let's take the example of a Person class which produces individual person objects. The Person class is the collection of code that acts as the template, or blueprint, for the individual people it produces. Each individual person object produced by our class is referred to as an **instance** of that class, or a person instance. 

We can define our person class such that the individual person instances it makes have certain **attributes**, like `height`, `name`, `hair color`. And we can define the Person class such that the person instances it produces have certain **behaviors**, like `say_hello` or `argue` (our people are feeling a little litigious). Both the attributes and behaviors of the person class are defined as methods in the Person class. Such methods, called **instance methods** can be called on each individual instance of Person. 

Let's take a look at our very first class. We're not going to explain everything in the below example right now. Just take a look and try to get an idea of how a class is constructed and used to create instances of itself. We'll get to know class and method definitions much better in the upcoming sections and lessons. 

```ruby
class Person

  def initialize(name)
    @name = name
  end
  
  def name
    @name
  end
  
  def hair_color
    "brown"
  end
  
  def say_hello
    "Hello!"
  end
  
  def argue
    "I'm right and you're wrong!"
  end
  
end
```

Here, we have a Person class, defined by the `class Person`, `...some code...`, `end` syntax. The class contains an initialize method, which allows us to make Person instances that contain certain attributes upon creation (more on that later), and various methods, as previously discussed, that confer attributes and behaviors upon each instance of the Person class. 

Let's take a look at an instance of Person right now: 

```ruby
sophie = Person.new("Sophie")

sophie.name 
=> "Sophie"

sophie.say_hello
=> "Hello!"
```

We created a new person via the `Person.new` syntax and saved it (her) to a variable, `sophie`. We were then able to call any of our Personal instance methods on `sophie`. Again, don't worry too much for now about that `initialize` method or the `Person.new` code, there'll be more on that later. 


## Instance Variables and Methods

The methods defined in the above example inside our Person class are called **instance methods** because we call them on individual instances of our Person class. You may have noticed that the `name` variable was prefaced with an `@` symbol and used in not one, but *two* methods––the `initialize` method and the `name` method. That variable is called an **instance variable**. 

**Instance Methods** are methods designed to be called on instances of a class. 

**Instance Variables** are bound to an instance of a class. That means that the value held by an instance variable is specific to whatever instance of the class it happens to belong to. Instance variables hold information about an instance, usually an attribute of that instance, and can be called on throughout the class, **without needing to be passed into other methods as arguments**. For example, once we set the value of `@name` equal to whatever string is passed in as an argument to our `initialize` method, we could call that same `@name` variable in our `name` method. 

Let's take a closer look:

```ruby
class Person
  def initialize(name)
    @name = name
  end
  
  def name
    @name
  end
end
```

Our `initialize` method, which takes in an argument of name and is immediately invoked when we types `Person.new`, sets an instance variable, `@name` equal to a name. Our `.name` instance method will return the `@name` variable, which is equal to a name! Check it out:

```ruby
sophie = Person.new("Sophie")
sophie.name
=> "Sophie"
```

Now that we understand the concept of instance variables and methods, we'll take a closer look at that `initialize` method. 

## Initializers

Now that we understand *what* a class is and how to define one and seen an instance of a class being created, or initialized, let's talk about *how* to give our classes the ability to instantiate (or initialize) new instances of itself with certain attributes.

Any Ruby class can produce new instances of itself, via the `<Class Name>.new` method, whether or not that class has an `initialize` method. However, if you want each instance of your class to be created with certain attributes, you must define an `initialize` method. 

In the above example, repeated here: 

```ruby
class Person
  def initialize(name)
    @name = name
  end
end
```

our `initialize` method takes in an argument of a name and sets an **instance variable** equal to the name that is passed into the method call. 

The `initialize` method is what's called a **callback** method, because it is automatically invoked every time the `.new` method is used to create a new instance of the class. 

So, because of how we defined our `initialize` method, every time you type `Person.new("Some name")`, a new person instance is created that has a name of `"Some name"` (i.e. whatever string you give the `.new` method). 

You may notice that instance methods, being method available to every *instance* of a class, are called on individual instances of a class. Just like the `.name` instance method is called on the variable `sophie` that we pointed to an instance of Person via this line: 

```ruby
sophie = Person.new("Sophie")
``` 

On the other hand, `.new` is called on the Person class itself. This is called a class method and we'll discuss it in further in the next section. 


## Class Variables and Methods

If an instance method is a method called on each individual instance of a class, a class method is called on the class itself. The class method that we've seen so far is the `.new` method. The `.new` method is special, it is a class method built into the Ruby language (meaning you don't have to define it in your class––it is already available to you) and it is called on a class to instantiate new instances of itself. Let's take a look at an example of a class method that we will build ourselves. 

### Building a Class Method

When we need to define an attribute of an individual person or some behavior that an individual person should be able to enact, we create an instance method. However, what if we want to keep track of *all* of our instances of person? It isn't really the responsibility of an *individual* person to look around itself and count up each and every other person instance that has been created. Instead, we can think of such a task as being the responsibility of the class as a whole. So, let's make a class method, `.all`, that will keep track of all of our people. 

### Defining the Method

To define a class method, we preface the method name with `self.`. Let's take a look: 

```ruby
class Person

  def self.all
    #some code here!
  end

  def initialize(name)
    @name = name
  end
  
  def name
    @name
  end
  
  def hair_color
    "brown"
  end
  
  def say_hello
    "Hello!"
  end
  
  def argue
    "I'm right and you're wrong!"
  end
  
end
```

Now that we've defined our method, we need to figure out our class can keep track of each instance of itself that is created *and* how our `.all` class method can return the list of all of those instances. 

### Keeping Track of All the Instances with a Class Variable

A **class variable** is accessible to both instance methods and class methods and contains information that is pertinent to the class as a whole, *not* every instance of that class. A class variable will be the perfect way to store a list of instances of our Person class. Class variables are prefaced with `@@`. 

Let's create a class variable, `@@all_instances`, and set it equal to an empty array: 

```ruby
class Person

  @@all_instances = []
  
  ...
end
```

Now, every time we use `.new` to create a new Person instance, we can keep track of that instance by adding it to our `@@all_instances` array: 

```ruby
class Person

  @@all_instances = []
  
  def initialize(name)
    @name
    @@all_instances << self
  end
  
end
```

Inside an instance method, like `initialize`, `self` refers to the *instance of the class* that you are operating on. Meanwhile, inside a class method, `self` refers to the class itself. So, in the above code, we are pushing the object that is an instance of Person class into our `@@all_instances` array every time a Person is instantiated. Now, we need to tell our `.all` class method to return our `@@all_instances` array: 


```ruby
class Person
  @@all_instances = []
  
  def initialize(name)
    @name = name
    @@all_instances << self
  end
  
  def self.all
    @@all_instances
  end
  
end
```

Let's try it out!

```ruby
sophie = Person.new("Sophie")
george = Person.new("George")

Person.all
=>  [#<Person:0x007fc021a3df20 @name="Sophie">, #<Person:0x007fc021a2dcb0 @name="George">]
```

Invoking our class method, `Person.all` has returned an array of person instances or objects. Each object has an object-id and a name. 

## Conclusion

Object Orientation is big topic. This was meant to be an introduction to some of the basic concepts of object-oriented Ruby. We'll be getting a lot of practice with what we've discussed here and we'll be learning even more as we move forward through the next two units. Before you go, here is a quick recap of the important key terms and concepts

| Term    |Definition|
|----------------|-----|
|class    | a collection of code that acts as a template for created individual Ruby objects with shared attributes and behaviors|
| instance    | an object created by a class|
|instance method | a method that contains information about an instance of a class or describes behavior of a an instance of a class. can be called on instances of a class|
|instance variable| a variable that is available to all instance methods on a particular object/instance of a class.
| class method| a method called on a class itself, *not* on instances of a class|
|class variable| a variable available to instance methods and class methods. used to store information about the class as a whole. 
|initialize method| a type of instance method that gets automatically called on an instance of a class immediately after it is created via the `.new` class method|




