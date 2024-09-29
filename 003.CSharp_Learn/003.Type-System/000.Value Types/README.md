# Value Types
Value types and reference types are the two main categories of C# types. A variable of a value type contains an instance of the type. This differs from a variable of a reference type, which contains a reference to an instance of the type. By default, on assignment, passing an argument to a method, and returning a method result, variable values are copied. In the case of value-type variables, the corresponding type instances are copied. The following example demonstrates that behavior:(值类型和引用类型是c#类型的两大类。value类型的变量包含该类型的实例。这与引用类型的变量不同，引用类型的变量包含对该类型实例的引用。默认情况下，在赋值、向方法传递参数和返回方法结果时，都会复制变量的值。对于值类型的变量，会复制对应的类型实例。下面的例子演示了这种行为:)
> 即： 引用类型和值类型的不同：在于是否会进行深度复制

```c#
using System;

public struct MutablePoint
{
    public int X;
    public int Y;

    public MutablePoint(int x, int y) => (X, Y) = (x, y);

    public override string ToString() => $"({X}, {Y})";
}

public class Program
{
    public static void Main()
    {
        var p1 = new MutablePoint(1, 2);
        var p2 = p1;
        p2.Y = 200;
        Console.WriteLine($"{nameof(p1)} after {nameof(p2)} is modified: {p1}");
        Console.WriteLine($"{nameof(p2)}: {p2}");

        MutateAndDisplay(p2);
        Console.WriteLine($"{nameof(p2)} after passing to a method: {p2}");
    }

    private static void MutateAndDisplay(MutablePoint p)
    {
        p.X = 100;
        Console.WriteLine($"Point mutated in a method: {p}");
    }
}
// p1 after p2 is modified: (1, 2)
// p2: (1, 200)
// Point mutated in a method: (100, 200)
// p2 after passing to a method: (1, 200)
```

As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.（如前面的例子所示，值类型变量上的操作只影响存储在该变量中的值类型实例。）

If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied. Both the copy and original value-type instance have access to the same reference-type instance. The following example demonstrates that behavior:（如果值类型包含引用类型的数据成员，那么在复制值类型的实例时，只复制引用类型实例的引用。复制类型实例和原始值类型实例都可以访问同一个引用类型实例。下面的例子演示了这种行为:）
> 若值类型里面包含引用类型，那么在复制时仅复制引用的值，并不会对引用类型进行深度复制
```c#
     using System;
     using System.Collections.Generic;
     
     public struct TaggedInteger
     {
         public int Number;
         private List<string> tags;
     
         public TaggedInteger(int n)
         {
             Number = n;
             tags = new List<string>();
         }
     
         public void AddTag(string tag) => tags.Add(tag);
     
         public override string ToString() => $"{Number} [{string.Join(", ", tags)}]";
     }
     
     public class Program
     {
         public static void Main()
         {
             var n1 = new TaggedInteger(0);
             n1.AddTag("A");
             Console.WriteLine(n1);  // output: 0 [A]
     
             var n2 = n1;
             n2.Number = 7;
             n2.AddTag("B");
     
             Console.WriteLine(n1);  // output: 0 [A, B]
             Console.WriteLine(n2);  // output: 7 [A, B]
         }
     }
```

## Kinds of value types and type constraints(值类型和类型约束的种类)
A value type can be one of the two following kinds:(值类型可以是如下两种类型之一)
- a structure type, which encapsulates data and related functionality (一种结构类型，封装了数据和相关功能)
- an enumeration type, which is defined by a set of named constants and represents a choice or a combination of choices (枚举类型，由一组命名常量定义，表示一个或多个选项的组合)

A nullable value type T? represents all values of its underlying value type T and an additional null value. You cannot assign null to a variable of a value type, unless it's a nullable value type.(一个可空值类型T?表示其基础值类型T的所有值和一个额外的空值。不能将null赋值给值类型的变量，除非它是可空值类型。)

You can use the struct constraint to specify that a type parameter is a non-nullable value type. Both structure and enumeration types satisfy the struct constraint. You can use System.Enum in a base class constraint (that is known as the enum constraint) to specify that a type parameter is an enumeration type.(你可以使用struct约束来指定类型参数是一个非空值类型。结构类型和枚举类型都满足结构约束。你可以使用System.Enum在基类约束(也叫Enum约束)中指定类型参数是枚举类型。)


## Built-in value types
C# provides the following built-in value types, also known as simple types:
- Integral numeric types
- Floating-point numeric types
- bool that represents a Boolean value
- char that represents a Unicode UTF-16 character

All simple types are structure types and differ from other structure types in that they permit certain additional operations:（所有简单类型都是结构类型，与其他结构类型的区别在于，它们允许某些额外的操作。）
- You can use literals to provide a value of a simple type. For example, 'A' is a literal of the type char and 2001 is a literal of the type int.（可以使用字面量来提供简单类型的值。例如，'A'是char类型的字面量，2001是int类型的字面量。）
- You can declare constants of the simple types with the const keyword. It's not possible to have constants of other structure types.（用const关键字可以声明简单类型的常量。其他结构类型的常量是不可能的。）
- Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.（常量表达式的操作数都是简单类型的常量，在编译时计算。）

A value tuple is a value type, but not a simple type.



## 参考资料
1. [https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/value-types](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/builtin-types/value-types)




