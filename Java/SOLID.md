## SOLID princioles in JAVA


### Single Responsibility Principle

 - Each class is doing ONLY one task or solve ONE problem.

public class Book {

    private String name;
    private String author;
    private String text;

    //constructor, getters and setters

    // methods that directly relate to the book properties
    public String replaceWordInText(String word, String replacementWord){
        return text.replaceAll(word, replacementWord);
    }

    public boolean isWordInText(String word){
        return text.contains(word);
    }
}

### Open-Closed Principle

Instead of changing a class to add a functionality is better to extend it

 - Open for extension, meaning that the class’s behavior can be extended
 - Closed for modification, meaning that the source code is set and cannot be changed

public class Guitar {

    private String make;
    private String model;
    private int volume;

    //Constructors, getters & setters
}

public class SuperCoolGuitarWithFlames extends Guitar {

    private String flameColor;

    //constructor, getters + setters
}


### Liskov Substitution Principle

 - If class A is a subtype of class B, we should be able to replace B with A without disrupting the behavior of our program

For instance a rectangle cannot extends a Square because it doesnt have the same properties


### Interface Segregation

Larger interfaces should be split into smaller ones. By doing so, we can ensure that implementing classes only need to be concerned about the methods that are of interest to them

public interface BearCleaner {
    void washTheBear();
}

public interface BearFeeder {
    void feedTheBear();
}

public interface BearPetter {
    void petTheBear();
}

public class BearCarer implements BearCleaner, BearFeeder {

    public void washTheBear() {
        //I think we missed a spot...
    }

    public void feedTheBear() {
        //Tuna Tuesdays...
    }

public class CrazyPerson implements BearPetter {

    public void petTheBear() {
        //Good luck with that!
    }
}


### Dependency Inversion

The principle of dependency inversion refers to the decoupling of software modules. This way, instead of high-level modules depending on low-level modules, both will depend on abstractions.

 - It's better to manipulate Interface than the object !!