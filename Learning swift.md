# Language Syntax
#PROJECTS/LEARNING_SWIFT

Swift feels a lot like Go with some traits of JS.
These are my personal notes of [YouTube](https://www.youtube.com/watch?v=Pd8IvykiW20&t=1586s)


### Variables
	* Declaring a variable: `var str = “Hello world!”`
	* Declaring a constant: `let str = “Hello world!”`
	* Declaring a strongly typed var: `var str : String = “Hello world!”`
	* Printing shit: `print(“Hello world!”)`
	* Printing interpolation: `print(“String is \(str)”)`
	* Booleans are:  `Bool`
	* Characters are:  `Character`
	* Casting is like go type adapting: `var a: Int = Int(5.3)`
	* There are data types for `Int8`, `UInt8`,  `Int64`, etc
	* Math is like every language ever
	* Int `++` and `—-` aren’t a thing
	* Random value between 1 and 10: `var rand = Int.random(in: 1…10)`
	* Math functions like `abs`, `floor`, `round`, `pow` etc are build in

### Conditionals
Conditions are exactly what you’d expect, but you can check if two objects point to the same reference using `===` (and `!==` to check if they point to different memory)

##### If statements
They are without the brackets, like go
```swift
if age > 5 {
	// something
}
```

##### Terminary opperator
Same concept as `? :`
```swift
var canDrive: Bool = age >= 18  ? true : false
```

### Arrays
	* Arrays are just shit like: `var a = [1, 2, 3]`
	* Loop over array: `for item in a {}`
	* Loop: `for i in 1...5 { print(i) }`
	* Loop with logic: `for i in 1..10 where i % 2 == 0 {}`
	* Foreach: `a.forEach{ print($0) }`
	* Cool reverse loops: `for i in (5…10).reversed() {}` BRO FUCKING LOOK AT IT
	* Conatins: `(1…5).contains(3)`
	
### Functions
Function declarations are a bit like those in Go, but with the order all changed and fucked. You can disable parameter labels in invokers by adding an underscore in the declaration, like `func fuck(_ x: Int)`. Functions that don’t have a return value need to be declared as `-> Void`. Method overflowing IS supported. Method parameters are constants by default, but you can make them. You can also return multiple values just like in go, thank FUCK. You can accept infinite arguments and handle them as an array just like Java (by adding `…` at the end)
```swift
fun getSum(x: Int, y: Int) -> Int {
	return x + y
}
print(getSum(x: 5, y: 4))
```

Functions have support for `defer`, just like Go.

### Closure
Closures are basically Lambda’s
```swift
var square: (Int) -> (Int) = {
	num in
	return num * num
}
Print(square(5))
```

### Arrays
So, you love arrays? Name every, yeah, nevermind, that joke doesn’t work here.
```swift
// cool shit!
var array1 = [Int]()
print(array.isEmpty) // pretty ez
// add 5
array1.append(5)
// or add more items
array1 += [10, 7] // pretty neat!
// or get one
print(array1[0])
// inserting something? Pretty useful! And fucking ez
array1.insert(10, at: 2) // WHY DOESN’T EVERY LANGUAGE HAVE THIS
// or remove something specific
array1.remove(at: 3)
// bulk replace? Ofc!
array1[0…2] = [1,2,3]
print(array.count)
// note that you can COMBINE arrays by doing var array 3 = array1 + array2
// HOW SICK IS THAT

// you sometimes want to make careful loops, just do
for (index, value) in array1.enumerated() {
}
array1.min()! // returns the minimal value, the ! Means that its optional, and can be null
```

### Dicts
Dicts are one of the things I’m most curious about! Let’s see how they are implemented here :)
They are initiated like so `var dict1 = [Int: String]()`

They have an `.isEmpty` flag just like arrays, and follow assignments (just like go), so using the line above as an example, you could do `dict1[1] = “One`

We can also define dicts with default values
```swift
var friendAges: [String, Int] = [
	“Femke”: 19,
	“Joost”: 22,
	“Nika”: 18,
	“Damian”: 20
]
```

Wanna check if a value is present and only then handle it, well, can do! And it’s actually pretty elegant
```swift
if let age = friendAges[“Femke”] {
	print(“My girlfriend is \(age) years old”)
}
```

Deleting values goes through nil assignments, like `friendAges[“Joost”] = nil`

### Operations
This is slightly disappointing, swift doesn’t seem to have common string utility that even Go provides in its `strings` package. Here’s a cheat sheet
	* You can get characters from a string by accessing it as an array, or even looping over it. Example: `str[0]`
	* So with that, get the first character like `str[str.startIndex]`
	* You CAN do `str.contains(“mats”)`
	* Or even check multiple separately, `str.contain{“abc”.containst($0)}` accepts one of those
	* Filter (replace) characters `”Derek”.filter{“aeiou”.contains($0)}`, so that’ll only have the aeio and u
	* Get the first 4 characters, can do, `String(str.prefix(4))` but note how the [Characters] need to be converted to a String
	* Splitting is like `var arr = str.split{$0 == “ “}`
	* Remove a character from an index like `str.remove(at: 2)`
	* Or insert a character like `str.insert(“a”, at: str.startIndex)`
	* Or insert a string like `str.insert(contentsOf: “ is great”, at: str.index(str.startIndex, offsetBy: 15))`
	* Get a substring, `var sub = str[3…8]`
	* Replace a range `str.replaceSubrange(sub, with: “ is super)`
	* Ore remove a range `str.removeSubrange(sub)`

### TUPLES (pronounced TOOPLS)
WHO THE FUCK COMES UP WITH THESE NAMES? AM I EVEN TYPING THEM CORRECTLY? WHATS GOING ON?!!
Noting this down as a codeblock with example code, because that’s the only way to keep my mind together with this shit

```swift
var t1 : (String, Int)
// asign values
t1 = (“age”, 5)
```

WAIT HOLY FUCK IT’S JUST A PAIR! Notation is a lot like how Go handles multiple return types, but this accepts it as a type! That’s sick! Almost cool enough to make me forgive it for the lacking String helpers

### Sets
Unordered lists of unique elements, same like java
`var nums = Set<Int>()` note how it uses the same type definition as java, pretty interesting.

Api is exactly like what you would expect

### Enums
Thank FUCK, i was almost afraid that Swift didn’t have enums, but here we are
Example
```swift
enum Emotion {
	case joy
	case anger
	case fear
	case disgust(reason :String)
}

var feeling = Emotion.joy
```

Cool thing tho! Notice how disgust has a value? That’s because you can add properties to enum types! These aren’t static or contant like in java.
Example:
```swift
var moods = [Emotion.disgust(reason: “Bad joke”), Emotion.disgust(reason: “Awful human”)]
```

### Optionals
Whoowh! My least favourite java API makes a return (Kotlin PTSD kicks in)
Like some wise man old said
> To have or not to have, that is the Optional  
(That’s actually my quote, but its so cringy that I don’t wan’t to claim it as my own)

It’s actually exactly the same as in kotlin, so yeah, take that as you will.

### Exception handling
Because you’re the unique exceptional snowflake that you are 👉👈
Exceptions are handled like Enums that you extend, so making a custom exception looks something /like this
```swift
enum DivisionError: Error{
	case DivideByZero
}

func fuckUp() throws -> void{
	throw DivisionError.DivideByZero
}
```

Try catch is a little different though, we need to make a codeblock that can catch, and then explicitly flag methods that are expected to explode violently.
```swift
do {
	try fuckUp()
} catch DivisionError.DivideByZero {
	print(“Well, what did you expect”)
}
```
The catch above only handles specific `DivideByZero` errors but doesn’t cover all `DivisionError` types. You can catch general types with `} catch DivisionError {`, or an un-typed `} catch {`, the catch-block has access to an `error` variable, which is the exception originally thrown. You can assign the error and cast it inline to print, like so `} catch let divisionErr as DivisionError }` and then print it.

We can get really fancy through, let’s say that we have a `get` method that does a HTTP get request, and it returns a String or throws an exception, we can catch it INLINE as an optional
```sift
let body: String? = try? Get(“https://example.com/“)
```
Tada! Now we have an optional string, that’s present when get succeeded, and nil when it fucked up big time.

### Constructs
Yessss YESSS **YESSSSSS**
So Swift has **BOTH** Constructs **AND** classes!
Constructs are strictly meant to describe objects/models and don’t support inheritance.

Let’s make a construct with some default values
```swift
struct Rectangle {
	var height = 0.0
	var length = 0.0
	func area() -> Double{
		let area = height * length
		return area
	}
}

// create, and no, its not a rectum
var myrect = Rectangle(height: 10.0, length: 5.0)
print(myrect.area())
```

### Classes
You’re a man of class, right? God, I’m so good at these punchlines. 
Main difference between classes and constructs is that classes can, like mentioned before, extend and implement. There’s more than that, but just keep this in mind for now.

Make two warriors, both based on the same class. The class should have default values, a constructor and basic methods.

```swift
class Warrior {
	// default values
	var name: String = "Default warriod"
	var health: Int = 100
	var attackMax: Int = 10
	var blockMax: Int = 10

	// constructor
	init(_ name: String, _ health: Int, _ attackMax: Int, _ blockMax: Int) {
		self.name = name
		self.health = health
		self.attackMax = attackMax
		self.blockMax = bloxkMax
	}

	func attack() -> Int{
		return Int.random(in: 1...self.attackMax)
	}

	func block() -> Int{
		return Int.random(in: 1...self.blockMax)
	}

	static func getAttkResult(_ warriorA : Warrior, _ warriorB : Warrior) {
		let warriorAAttkAmt: Int = warriorA.attack()
		let warriorBBlockAmt: Int = warriorB.block()
		var dmg2WB: Int = warriorAAttkAmt - warriorBBlockAmt
		dmg2WB = dmg2WB <= 0? 0 : dmg2WB
		warriorB.health = warriorB.health - dmg2WB
		print("\(warriorA.name) attacks \(warriorB.name) and deals\(dmg2wB)damage")
		print("\(warriorB.name) is down to \(warriorB.health)")
	}
}
```

We can create an object instance like
`var w = Warrior(“Thor”, 150, 20, 8)`, and call static methods like `Warrior.getAttkResult(`

Let’s say that we wanted to clean up before the GC removes our instance, then we could add a `deinit {}` block that gets called before removal

### Protocols
Protocols are basically interfaces, and the name makes sense because it’s a predefined set of rules a class must follow to be compatible. Implementing is called adopting, so classes adopt protocols.

```swift
protocol Teleport {
	func teleport() -> String
}
```

Now let’s make two simple classes adopting this protocol
```swift
class CanTeleport : Teleports{
	func teleport() -> String{
		return "Teleports Away"
	}
}

class CantTeleport : Teleports{
	func teleport() -> String{
		return "Fails to teleport"
	}
}
```

Extending classes is more or less the same, as in, you adopt the other class, and can then override functions or call the parent constructor (or any other method for that matter) through `super.init(`. You can override functions with the `override` keyword, so that’d look like `override func block() -> Int {` to change the warrior block behaviour.

### Extensions
Extensions are a new concept in Swift that add custom functionality to classes, types, structs, etc (kinda like Prototype in JavaScript) but you **CAN’T** use them to override default methods.

Let’s add a custom method to the normal Double type
```swift
extension Double {
	var km: Double { return self * 1000.0 }
	var m: Double { return self }
	var cm: Double { return self * 100.0 }
	var mm: Double { return self / 1000.0 }
}

// use the custom method
let oneInch = 24.4.mm
```

We can also add extensions in the form of protocols
```swift
// create protocl
protocol Summable { static func (x: Self, y: Self) -> Self }

// make types use the protocol
extension Int: Summable{}
extension Double: Summable{}
extension String: Summable{}

// make a default method accepting everything of a type, and converting it on the fly
// kina like java dynamic typing
func sum<T: Summable>(_ x: T, _ y: T) -> T {
	return x + y
}
```

### Type Aliases
Swift supports type aliasing just like Go and Rust, this allows you to define a custom type that’s actually something else, but you may want to differentiate.
```swift
typealias UserID = UInt16
```

### Blobs
Not more to say about it
```swift
let multilineString = “””
I’m
A
Text
“””
```

### Apple API versions
You can check environment api availability like follows
```swift
if #available(iOS 10, macOS 10.12, *) {
    // Use iOS 10 APIs on iOS, and use macOS 10.12 APIs on macOS
} else {
    // Fall back to earlier iOS and macOS APIs
}
```

### Concurrency
Concurrency in Swift is similar to that in JS, as in, it uses asyncronemous methods and keywords and doesn’t let you interact with threads directly. It does differentiate between Parallel and Async but like it should be *fineeeeeee*

```swift
func listPhotos(inGallery name: String) async -> [String] {
    let result = // ... some asynchronous networking code ...
    return result
}
```

And you can pull it back using `await`, or prefix functions with `async`

Its also possible to await multiple async methods at once (like promise all)
```swift
async let firstPhoto = downloadPhoto(named: photoNames[0])
async let secondPhoto = downloadPhoto(named: photoNames[1])
async let thirdPhoto = downloadPhoto(named: photoNames[2])

let photos = await [firstPhoto, secondPhoto, thirdPhoto]
show(photos)
```

### Type Checking
Many languages support `instanceof`or `typeof`, swift has a more “no bullshit” approach and simply uses `is`, you can check hierarchy or protocol using that keyword. This would simply look like `if item is Movie {`

### Downcasting
It could happen that you get a variable of a type, but actually want to downcast it to a subtype after checking its type. Given `var item: Movie`, you can cast it to shortfilm (which extends Movie) using `let sf = item as? ShortFilm { print(sf.title) }`

### Any & AnyObject
Swift is a type safe language at its core, cut there might be cases where you don’t know the type of something. These can be `Any` if its literally anything (type, function, class, whatever) or `AnyObject` its any class instance, but has to be an instance.
```swift
var things: [Any] = []
things.append(0)
things.append("hello")
things.append(Movie(name: "Ghostbusters", director: "Ivan Reitman"))
things.append({ (name: String) -> String in "Hello, \(name)" })
```
