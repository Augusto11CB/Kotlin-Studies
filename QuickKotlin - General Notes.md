
# Quick Kotlin - General Notes

## To Keep
[kotlin-programming](https://www.programiz.com/kotlin-programming/getters-setters)

## Init Block and Secondary Constructor

### What is the difference between init block and constructor in kotln?

The  **init**  block will executes immediately after the primary constructor. Initializer blocks effectively becomes part of the primary constructor. The  **constructor**  is the secondary constructor. Delegation to the primary constructor happens as the first statement of a secondary constructor, so the code in all initializer blocks is executed before the secondary constructor body.

  
The  **init**  block will executes immediately after the primary constructor. Initializer blocks effectively becomes part of the primary constructor. The  **constructor**  is the secondary constructor. Delegation to the primary constructor happens as the first statement of a secondary constructor, so the code in all initializer blocks is executed before the secondary constructor body.

**Example**

```kotlin
class Sample(private var s : String) {
    constructor(t: String, u: String) : this(t) {
        this.s += "$u"
    }
    init {
        s += "B"
    }
}
```
**Initialization**

``` kotlin
Sample("T","U")
// Result: TBU
	// T from primary constructor
	// B from the init block
	// U from the second constructor
```

## Lazy Initialization in Kotlin
https://medium.com/android-dev-br/quando-utilizar-inicializa%C3%A7%C3%A3o-lazy-do-kotlin-45377c8b68ad
[https://www.baeldung.com/kotlin-lazy-initialization](https://www.baeldung.com/kotlin-lazy-initialization)
