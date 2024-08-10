## this指针

1. 为区别**传入值**和**对象属性**的变量名，使用：
    ```c++
    this -> property
    ```
    表示内部属性
2. 成员方法返回`*this`返回自身，从而实现链式编程，比如：
   ```c++
   function().function()
   ```
    注意其中`function()`的返回值须是引用类型`ElementType&`，否则会不断创建新的对象。

## 常函数与常对象

- 常函数：在函数()后加const关键字,使得函数无法修改成员属性。
  
  被multible修饰的属性可以被常函数修改：

  ```c++
  class Person
  {

    public void show() const
    {
        this->b = 1;
    }

    int a;
    mutable int b;

  }
  ```

- 常对象只能调用常函数，因为非常函数可以修改属性。

## 友元

1. 函数作友元：将函数用关键字friend声明在类内，想要使全局函数`visit()`作友元，如下：
   ```c++
   class Building
   {

    friend void visit(Building &building);

    private:
        string room;

   }

   void visit(Building &building)
   {
        cout << "Succeed";
   }
   ```
   如果`visit()`是类内函数，声明时要加作用域：
   ```c++
   friend void someClass:: visit(); 
   ```
2. 类作友元：类内声明`friend class Fclass`可以使类Fclass成为该类的友元

## 运算符重载

设有如下定义的类Person：

```c++
class Person
{
public:
    int a;
    int b;
}
```
1. 成员函数运算符重载：

   ```c++
   class Person
   {
    public:
        Person operator+ (Person &person)
        {
            Person temp;
            temp.a = this->a + person.a;
            temp.b = this->b + person.b;
            return temp;
        }
   }
   ```
2. 全局函数运算符重载：
   
   ```c++
   Person operator+ (Person &person1, Person &person2)
   {
        Person temp;
        temp.a = person1.a + person2.a;
        temp.b = person1.b + person2.b;
        return temp;
   }
   ```

  