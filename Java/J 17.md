
## Chapter 15 : Modules


Key Skills & Concepts
●Know the definition of a module
●Know Java’s module-related keywords
●Declare a module by use of the module keyword
●Use requires and exports
●Understand the purpose of module-info.java
●Use javac and java to compile and run module-based programs
●Understand the purpose of java.base
●Understand how pre-module legacy code is supported
●Export a package to a specific module
●Use implied readability
●Use services in a module


Modules give you a way to describe the relationships and dependencies of the code that comprises an application. Modules also let you control which parts of a module are accessible to other modules and which are not. Through the use of modules you can create more reliable, scalable programs.

As a general rule, modules are most helpful to large applications because they help reduce the management complexity often associated with a large software system. 

However, small programs also benefit from modules because the Java API library has now been organized into modules. Thus, it is now possible to specify which parts of the API are required by your
program and which are not. This makes it possible to deploy programs with a smaller run-time footprint, which is especially important when creating code for small devices, such as those intended to be part of the Internet of Things (IoT).


____

#### Module Basics

In its most fundamental sense, a module is a grouping of packages and resources that can be collectively referred to by the module’s name. 

A module declaration specifies the name of a module and defines the relationship a module and its packages have to other modules. 

Module declarations are program statements in a Java source file and are supported by several module-related keywords added to Java by JDK 9 :

```
exports   module   open   opens
provides  requires  to   transitive
uses      with
```

These keywords are recognized as keywords only in the context of a module declaration. Otherwise, they are interpreted as identifiers in other situations.

___

A module declaration is contained in a file called module-info.java. The module-info.java file must contain only a module definition. It is not a general-purpose file.

Thus, a module is defined in a Java source file. This file is then compiled by javac into a class file and is known as a module descriptor. 

A module declaration begins with the keyword module. Here is its general form:
```java
module moduleName {
	// module definition
}
```

The name of the module is specified by moduleName, which must be a valid Java identifier or a sequence of identifiers separated by periods. The module definition is specified within the braces.

Although a module definition may be empty (which results in a declaration that simply names the
module), typically it specifies one or more clauses that define the characteristics of the module.

___

#### A Closer Look at requires and exports

At the foundation of a module’s capabilities are two key features. : 

the ability to specify a dependence and the ability to satisfy that dependence. These capabilities are specified through the use of the requires and exports statements within a module declaration.


`requires moduleName;`

Here, moduleName specifies the name of a module that is required by the module in which the
requires statement occurs. This means that the required module must be present in order for
the current module to compile.

`exports packageName;`

Here, packageName specifies the name of the package that is exported by the module in which
this statement occurs. When a module exports a package, it makes all of the public and protected
types in the package accessible to other modules. Furthermore, the public and protected members
of those types are also accessible. However, if a package within a module is not exported, then
it is private to that module, including all of its public types.

even though a class is declared as public within a package, if that package is not explicitly exported by an exports statement, then that class is not accessible to other modules

public and protected types of a package, whether exported or not, are always accessible within that package’s module. The exports statement simply makes them accessible to outside modules. Thus, any nonexported package is only for the internal use of its module.


___

The key to understanding requires and exports is that they work together. 

requires and exports statements must occur only within a module statement. Furthermore, a module statement must occur by itself in a file called
module-info.java.

___

#### java.base and the Platform Modules

Of the platform modules, the most important is java.base. It includes and exports those
packages fundamental to Java, such as java.lang, java.io, and java.util, among many others.
Because of its importance, java.base is automatically accessible to all modules. Furthermore, all
other modules automatically require java.base.



#### Legacy Code and the Unnamed Module


Support for legacy code is provided by two key features. The first is the unnamed module.
When you use code that is not part of a named module, it automatically becomes part of the
unnamed module. The unnamed module has two important attributes. First, all of the packages
in the unnamed module are automatically exported. Second, the unnamed module can access
any and all other modules. Thus, when a program does not use modules, all API modules in the
Java platform are automatically accessible through the unnamed module.

The second key feature that supports legacy code is the automatic use of the class path,
rather than the module path.

many simple programs that you will write when learning the essentials
of Java, there is no need to contain them in modules. For the reasons stated at the start of
this chapter, modules are often of the greatest benefit when creating commercial programs.


#### Exporting to a Specific Module



#### Using requires transitive



#### Use Services

Service and Service Provider Basics

The Service-Based Keywords

A Module-Based Service Example

Additional Module Features


