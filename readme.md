# MAD - Exercise 01
## Tasks
* Watch the Kotlin Crashcourse Video in Moodle or complete the tutorials **[Introduction to programming in Kotlin](https://developer.android.com/courses/pathways/android-basics-compose-unit-1-pathway-1)** and **[Kotlin fundamentals](https://developer.android.com/courses/pathways/android-basics-compose-unit-2-pathway-1
)**.
* Answer the questions inside this Readme.md file and push it to your repository.
* Submit your coding solution of the Number Guessing Game inside the repository.
* Submit the link to your repository in Moodle.

## Questions
### Describe how Kotlin handles null safety. What are nullable types and non-null types in Kotlin? (0,5 points)
<span style="color:blue">Provide your answer here! </span>

In Kotlin, the type system distinguishes between references that can hold null (nullable references) and those that cannot (non-nullable references).
For example, a regular variable of type String cannot hold null:
```kotlin 
var a: String = "abc" // Regular initialization means non-nullable by default
a = null // compilation error
```
To allow nulls, you can declare a variable as a nullable string by writing String?:
```
var b: String? = "abc" // can be set to null
b = null // ok
```
Trying to access b's properties results in a compilation error since it is not safe.
```
val l = b.length // error: variable 'b' can be null
```
You need to make sure that b is not null to access its properties:
```
val b: String? = "Kotlin"
if (b != null && b.length > 0) {
    print("String of length ${b.length}")
} else {
    print("Empty string")
}
```
Or like this using safe calls: 
```
val a = "Kotlin"
val b: String? = null
println(b?.length)
println(a?.length) // Unnecessary safe call
```


### What are lambda expressions and higher order functions in Kotlin? Why would you store a function inside a variable? (0,5 points)
In Kotlin, lambda expressions are a concise way to declare anonymous functions. They are often used for defining short functions without the need for a full function declaration.
Example of a lambda expression:
```
val add: (Int, Int) -> Int = { a, b -> a + b }
```
In this example, add is a variable storing a lambda expression that takes two Int parameters and returns their sum.

Higher-order functions are functions that take one or more functions as parameters or return a function. 
Kotlin supports higher-order functions, allowing you to pass functions as arguments or return them from other functions.
Example of a higher-order function:
```
fun operateOnNumbers(a: Int, b: Int, operation: (Int, Int) -> Int): Int {
    return operation(a, b)
}
```
Why would you store a function inside a variable?
Functions stored in variables can be easily passed as arguments to other functions.
Also, functions stored in variables can also be returned from other functions.

### Provide a solution for the following number guessing game inside `App.kt`. (3 points)

## Number Guessing Game in Kotlin
The game is a simple number guessing game. The task is to generate a random, max 9-digit, number. The number must **not contain repeating digits**. Valid digits are 1-9.
Ask the user to guess the max 9-digit number. The game is finished when the user guesses the correct digits in the correct order.
In each round, the user gets feedback about the number of correct digits and the number of correct digits in the correct position.
The output should be in the format "n:m", where "n" is the number of digits guessed correctly regardless of their position, 
and "m" is the number of digits guessed correctly at their correct position. Here are some examples:

This example shows the game flow with 4-digits to guess (the default argument)

Generated number: 8576
-	User input: 1234, Output: 0:0
-	User input: 5678, Output: 4:1
-	User input: 5555, Output: 1:1
-	User input: 3586, Output: 3:2
-	User input: 8576, Output: 4:4 -> user wins

Take a look into the provided code structure in `src/main/kotlin/App.kt`. Implement the following methods (lambda expressions):
- _playNumberGame(digitsToGuess: Int = 4)_ (1 point): The main game loop that handles user input and game state. Make use of _generateRandomNonRepeatingNumber_ and _checkUserInputAgainstGeneratedNumber_ here. This function also utilizes a default argument 
- _generateRandomNonRepeatingNumber_ (1 point): A lambda expression that generates a random number with non-repeating digits of a specified length.
- _checkUserInputAgainstGeneratedNumber_ (1 point): A lambda expression that compares the user's input against the generated number and provides feedback.

``CompareResult.kt`` This class is a data structure which helps with bundling the result of the comparison of the user input and the generated number. Look at the toSting() and use it in your output.

Run the project with `./gradlew run` and test your implementation with the provided tests in `src/test/kotlin/AppTest.kt` with `./gradlew test`.

# Project Structure
The project is structured into two main Kotlin files:

**App.kt**: Contains the main game logic and functions.

**AppTest.kt**: Contains unit tests for the various functions in App.kt.

