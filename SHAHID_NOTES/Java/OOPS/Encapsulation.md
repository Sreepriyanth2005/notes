**Encapsulation** = bundling data (fields) and the methods that operate on that data into one unit (a class), and **controlling access** to that data so the class can protect its internal invariants.

Goal: **Expose behaviour, hide representation.** Consumers call methods (what to do); the class decides how it does it (how it’s stored).


### Access Modifier

|Modifier|Same Class|Same Package|Subclass (Different Package)|Other Packages|Typical Use Case|
|---|---|---|---|---|---|
|**private**|✅ Yes|❌ No|❌ No|❌ No|Hide internal data/methods completely; only accessible inside the class.|
|**default** _(no keyword)_|✅ Yes|✅ Yes|❌ No|❌ No|Package-private: Useful for utilities within a package.|
|**protected**|✅ Yes|✅ Yes|✅ Yes|❌ No|Share with subclasses, even in other packages, but keep hidden from unrelated classes.|
|**public**|✅ Yes|✅ Yes|✅ Yes|✅ Yes|Full access; use for APIs, constants, and methods meant for all.|

### Getter & Setter

1. Getters and setters control how data is accessed and changed.
2. They protect internal details by hiding how data is stored.
3. Setters can check values to prevent invalid data.
4. They make future changes easier by centralizing data access.
5. Getters and setters keep your data safe from direct outside changes.
6. You can add extra actions like logging or validation inside them.

```java
class Person {
    private int age;  // private field

    // Getter method
    public int getAge() {
        return age;
    }

    // Setter method with validation
    public void setAge(int age) {
        if (age >= 0) {       // only allow non-negative age
            this.age = age;
        } else {
            System.out.println("Age cannot be negative");
        }
    }
}
```

