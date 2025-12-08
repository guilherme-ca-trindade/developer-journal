# Code Questions from the Test 2 Practice

#### Define two interfaces, Steerable and Drivable. The Steerable interface must contain the method ‘turn’ which accepts an integer number of degrees. The Drivable interface must contain the methods: ‘go’ and ‘stop’. Now define a class named Vehicle that implements both these interfaces with any necessary code so that the following code produces the indicated output: 

var v = new Vehicle(“Corvette”); v.turn(10); // prints “The Corvette turned 10 degrees” 
v.go(); // prints “Vroom! The Corvette is driving.” 
v.stop(); // prints “Screech! The Corvette stopped.”

```java
public interface Steerable {
    void turn(int degrees);
}

public interface Drivable {
    void go();
    void stop();
}

class Vehicle implements Steerable, Drivable {
    private String car;

    public Vehicle(String car) {
        this.car = car;
    }

    @Override
    public void turn(int degrees) {
        System.out.println("The " + car + " turned " + degrees + " degrees.");
    }

    @Override
    public void go() {
        System.out.println("Vroom! The " + car + " is driving.");
    }

    @Override
    public void stop() {
        System.out.println("Screech! The " + car + " stopped.");
    }
}
```


#### Write two classes named Point and LabelledPoint where LabelledPoint is a subclass of Point.  Use appropriate constructors, instance variables, setters, getters, and overrides such that the following code produces the indicated output:

System.out.println(new Point(1, 2));   // prints “(1,2)” 
System.out.println(new LabelledPoint(1, 2, “a”)); // prints “a:(1,2)”

```java
// Base class Point
class Point {
    private int x;
    private int y;

    // Constructor
    public Point(int x, int y) {
        this.x = x;
        this.y = y;
    }

    // Getters
    public int getX() { return x; }
    public int getY() { return y; }

    // Setters
    public void setX(int x) { this.x = x; }
    public void setY(int y) { this.y = y; }

    // Override toString to print "(x,y)"
    @Override
    public String toString() {
        return "(" + x + "," + y + ")";
    }
}

// Subclass LabelledPoint
class LabelledPoint extends Point {
    private String label;

    // Constructor
    public LabelledPoint(int x, int y, String label) {
        super(x, y);   // call Point’s constructor
        this.label = label;
    }

    // Getter and Setter for label
    public String getLabel() { return label; }
    public void setLabel(String label) { this.label = label; }

    // Override toString to print "label:(x,y)"
    @Override
    public String toString() {
        return label + ":" + super.toString();
    }
}
``` 
