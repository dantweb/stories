# Mastering SOLID principles in PHP: Building robust and maintainable code

<p><strong>Explore the SOLID principles in PHP with practical examples, learn how they enhance code maintainability, and reduce technical debt in your applications.</strong></p>
<p>Discover how SOLID principles can transform your PHP code into a robust, scalable, and maintainable system with practical examples and actionable insights.</p>
<div>
<h3>Introduction to SOLID Principles</h3>
The SOLID principles are a set of design guidelines that help developers create software that is easy to maintain, extend, and understand. These principles are particularly important in PHP development, where applications often grow in complexity over time. By adhering to SOLID, you can ensure your codebase remains clean and manageable.
<h3>Single Responsibility Principle (SRP)</h3>
The Single Responsibility Principle states that a class should have only one reason to change, meaning it should have only one job or responsibility. This principle helps in reducing the complexity of the code and makes it easier to test and maintain.
<pre><code>class User {
    public function __construct(private string $name, private string $email) {}

    public function getName(): string {
        return $this-&gt;name;
    }

    public function getEmail(): string {
        return $this-&gt;email;
    }
}

class UserPrinter {
    public function print(User $user): void {
        echo $user-&gt;getName() . ' - ' . $user-&gt;getEmail();
    }
}</code></pre>
In this example, the <code>User</code> class is responsible only for managing user data, while the <code>UserPrinter</code> class handles the printing logic. This separation adheres to SRP.
<h3>Open/Closed Principle (OCP)</h3>
The Open/Closed Principle suggests that software entities should be open for extension but closed for modification. This means you should be able to add new functionality without changing existing code.
<pre><code>interface Shape {
    public function area(): float;
}

class Rectangle implements Shape {
    public function __construct(private float $width, private float $height) {}

    public function area(): float {
        return $this-&gt;width * $this-&gt;height;
    }
}

class Circle implements Shape {
    public function __construct(private float $radius) {}

    public function area(): float {
        return pi() * pow($this-&gt;radius, 2);
    }
}</code></pre>
Here, the <code>Shape</code> interface allows for the addition of new shapes without modifying the existing code, adhering to OCP.
<h3>Liskov Substitution Principle (LSP)</h3>
The Liskov Substitution Principle states that objects of a superclass should be replaceable with objects of a subclass without affecting the correctness of the program. This ensures that a subclass can stand in for its superclass without causing errors.
<pre><code>class Bird {
    public function fly(): void {
        echo 'Flying';
    }
}

class Sparrow extends Bird {
    public function fly(): void {
        echo 'Sparrow flying';
    }
}

class Ostrich extends Bird {
    public function fly(): void {
        throw new Exception('Cannot fly');
    }
}</code></pre>
In this example, the <code>Ostrich</code> class violates LSP because it cannot fly, unlike its superclass <code>Bird</code>. To adhere to LSP, we should reconsider the inheritance hierarchy.
<h3>Interface Segregation Principle (ISP)</h3>
The Interface Segregation Principle advocates for creating small, specific interfaces rather than large, general-purpose ones. This ensures that implementing classes only need to be concerned with the methods that are relevant to them.
<pre><code>interface Printer {
    public function print(): void;
}

interface Scanner {
    public function scan(): void;
}

class AllInOnePrinter implements Printer, Scanner {
    public function print(): void {
        echo 'Printing';
    }

    public function scan(): void {
        echo 'Scanning';
    }
}

class SimplePrinter implements Printer {
    public function print(): void {
        echo 'Printing';
    }
}</code></pre>
Here, the <code>Printer</code> and <code>Scanner</code> interfaces are segregated, allowing classes to implement only the methods they need.
<h3>Dependency Inversion Principle (DIP)</h3>
The Dependency Inversion Principle states that high-level modules should not depend on low-level modules. Both should depend on abstractions. This principle promotes the use of interfaces or abstract classes to decouple the system's components.
<pre><code>interface Database {
    public function save($data): void;
}

class MySQLDatabase implements Database {
    public function save($data): void {
        echo 'Saving data to MySQL database';
    }
}

class UserService {
    public function __construct(private Database $database) {}

    public function createUser($userData): void {
        $this-&gt;database-&gt;save($userData);
    }
}</code></pre>
In this example, the <code>UserService</code> depends on the <code>Database</code> interface, not on a specific database implementation, adhering to DIP.
<h3>Conclusion</h3>
By mastering the SOLID principles, PHP developers can create code that is not only robust and scalable but also easy to maintain and extend. These principles provide a solid foundation for building high-quality software that stands the test of time.

</div>

[Original Post](https://dantweb.dev/?p=597)
