

1. **Class**  
   Template for objects. Defines properties (variables) and behaviors (methods).  
   *Example:* `class Car { String model; void start() { ... } }`  

2. **Object**  
   Instance of a class. Created using the `new` keyword.  
   *Example:* `Car myCar = new Car();`  

3. **Instance**  
   A single occurrence (object) of a class.  

4. **Inheritance**  
   Child class acquires properties/methods from a parent class. Uses `extends`.  
   *Example:* `class ElectricCar extends Car { ... }`  

5. **Polymorphism**  
   Same method behaves differently (e.g., overriding `start()` in `ElectricCar`).  

6. **Encapsulation**  
   Bundling data (variables) and methods with access control (`private`, `public`).  

7. **Abstraction**  
   Hiding complexity. Achieved via abstract classes/interfaces.  

8. **Abstract Class**  
   A class with `abstract` methods (no body). Cannot be instantiated.  

9. **Interface**  
   A contract with method signatures. Uses `implements`.  
   *Example:* `interface Drivable { void drive(); }`  

10. **Constructor**  
    Special method to initialize objects. Same name as the class.  

11. **Static**  
    Belongs to the class, not instances. Shared across all objects.  
    *Example:* `static int count;`  

12. **Final**  
    Prevents modification (variables), overriding (methods), or inheritance (classes).  

13. **Super**  
    Refers to the parent class. Used to call its methods/constructors.  

14. **Method Overriding**  
    Redefining a parent method in a child class (same name/parameters).  

15. **Method Overloading**  
    Multiple methods with the same name but different parameters.  

16. **Singleton**  
    Design pattern ensuring only one instance of a class exists.  

17. **SOLID**  
    Design principles: Single Responsibility, Open/Closed, Liskov Substitution, Interface Segregation, Dependency Inversion.  

18. **Coupling**  
    Degree of dependency between classes. Low coupling = better design.  

19. **Cohesion**  
    How focused a class is on a single task. High cohesion = better design.  

20. **Composition**  
    Building complex objects by combining simpler ones ("has-a" relationship).  

21. **Aggregation**  
    A type of composition where parts can exist independently.  

22. **Instance Variables**  
    Variables declared in a class (unique to each object).  

23. **Local Variables**  
    Variables declared inside a method (scope limited to the method).  

24. **Access Modifiers**  
    Control visibility: `public`, `private`, `protected`, default (package-private).  

25. **Garbage Collection**  
    Automatic memory management in Java (removes unused objects).  

---

**Quick Tips:**  
- **“Is-a”** → Inheritance (e.g., `ElectricCar` **is a** `Car`).  
- **“Has-a”** → Composition (e.g., `Car` **has an** `Engine`).  
- **Abstract Class vs Interface** → Use abstract classes for shared code, interfaces for contracts.  

