## Use of Static Factory instead of basic constructors

public static boolean valueOf(boolean b) {
    return b ? Boolean.TRUE : BOOLEAN.FALSE;
}

***Advantages***

 - This factory method has a name
 - They are not required to create a new object
 - Unlike constructor they can return an object of any subtype of their return type
 - Returned object can vary from call to call as a function of the input parameters
 - The class of the returned object need not exist when the class containing the method is written

***Drawbacks***

 - Class without public constructors cannot be subclassed
 

## Consider a builder when faced with many constructor parameters

 - The builder pattern simulates named optional parameters
 - The builder pattern is well suited to class hierarchies
 - Use it when designing classes with a lot of parameters

## Enforce the singleton property with a private constructor or an enum type

public class Elvis {
    private static final Elvis INSTANCE = new Elvis();
    private Elvis() {...}
    public static Elvis getInstance() {return INSTANCE;}
}

public enum Elvis {
    INSTANCE;

}
 - Gives flexibility to change if the class is a singleton or not
 - Using static factory, a method reference can be used as a supplier (Elvis::instance)

## Enforce noninstantiability with a private constructor

For example utility classes are made up with static methods and static fields, this class doesnt have to be an instance if you want to enforce noninstantiability, you have to make the contructor private

public class UtilityClass {

    private UtilityClass() {
        throw new AssertionError();
    }
}

 - With the private constructor, no subclass is possible
 - We cannot instatiate the class now

## Prefer dependency injection to hardwriting resources

For instance a SpellChecker class would need a dictionary to work, but each language got its own spelling, but static utility classes and singletons are inapropriate.

The solution is then to pass the underlying resource as a parameter of the constructor.

public class SpellChecker {
    private final Lexicon dictionary;

    public SpellChecker(Lexicon dictionary) {
        this.dictionary = Objects.requireNonNull(dictionary);
    }

}

 - Provides flexibility and testability

## Avoid creating unnecessary objects

String s = new String("Ballon"); --> Creates a new instance of STring each time!!!!

Do this instead String s = "ballon"; Using a single String instance

 - Be careful of not creating unnecessary instances
 - Creates static final instance to improve performance and reuse it
 

