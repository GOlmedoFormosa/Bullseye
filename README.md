# SwiftUI

This project is a game in which I'm working to earn some experience with SwiftUI and remember some concepts of Swift.

## SwiftUI vs UIKit

- 2019 apple introduced SwiftUI, is the new way to create user interfaces in Swift. One of the cool things is that user interfaces are created completely in code. But while you're coding you can see a dynamic preview of this code in SwiftUI canvas editor, and you have a choice, you can either code the user interface yourself or you can use SwiftUI canvas editor to code it on your behalf. So SwiftUI gives you the benefit of being able to construct user interface via code, combined with the benefits of being able to visualize your work as you go.
- 2008 was released UIKit which is still a valid way to make IOS apps, and there are three main reasons for which developers are still using it.

  1. SwiftUI only works on IOS 13 or later, even IOS 14 is out now, some companies still need to support IOS 12 or earlier, so they can't switch to SwiftUI quite yet.
  2. SwiftUI is still not as mature as UIKit. UIKit is being there for more than 8 years and also is based on Application Kit, which has even more history.
  3. Many companies have already written their apps using UIKit and will be just too much work to rewrite the entire app in SwiftUI.

- Add User
- Create Channel
- Create Chat
- Listen Messages

## Views

You can think as a view like everything that gets drawn on the screen (Texts, Buttons, Sliders, etc). Some views can act as containers for other views, for example you will have a big view container which will be the screen. There are different types of view in SwiftUI and they all have one thing in common, they can all be drawn on the screen. Examples:

1. Text: is a view that displays one or more lines of read-only text. The put the bullseye as close as you can message is a text view, as are all of the other labels in the app. Even a buuton with the label "hit me" is an example of a text view.
2. Slider: lets user enter a number by sliding a control, which is called a thumb, along with a straight line track where one side represents a minimum and the other side represents a maximum value.
3. Button: is a view that performs an action when you tap on it. You can put any view you'd like inside a button, and usually you put a Text view inside the button.
4. VerticalStack or VStack: is a view that act as a container for other views. The views that contains are called it's children and VStack's job is to arrange its children in a vertical stack. This is invisible by default.
5. HorizontalStack or HStack: is like VStack but horizontally instead of vertically.

## Test

- Create new XCode project.
- Choose template IOS -> App and Next.
- Product name: Bullseye. Team -> default. Organization identifier -> com.name. Everything else default.
  The main view of our app by default is called Content.View
- We will have to press "resume" on the right to see the visualizer.
- Update the text name with "PUT THE BULLSEYE AS CLOSE AS YOU CAN TO" and delete the padding.
- If you hit control+command+space. "emojiemojiemoji\nPUT THE BULLSEYE AS CLOSE AS YOU CAN TO"
- In order to add a new view press the + button in the top right. If you select a View and you hover over the line below our existing Text View we will see a blue line, so if we drop the new View there, we will add the Text View inside our VStack view.

## Modify SwiftUI Modifiers

SwiftUI has a bunch of built-in modifiers that you can use in your apps to modify the style of the views. For example, there are view modifiers to add a shadow, a corner radius, or a button to your view. Example: Text("100").opacity(0.5)
Everytime you apply a view modifier like that behaind scenes, SwiftUI is creating new modified version of the original view. So first SwiftUI creates the Text view and when you apply the opacity modifier, it creates a new view that's a version of the previous view, that is now partially transparent. This is really important to understand because you can apply in multiple view modifiers in a row like this: Text("100").opacity(0.5).border(Color.red, width: 2) so in this case the border will be opaque, this is because everytime you apply a modifier, behaind scenes, SwiftUI is creating a new modified version of the original view. So first we will have a Text view, then we will have a transparent Text View, and then we will add the border so the border won't be transparent because order is important.
Some examples of view modifiers:

1. Kerning
2. Bold
3. Font
4. Line Spacing
5. Multiline Text Alignment

So in oder to add a modifier we can click the + button and look for modifiers, we can select the bold and drag and drop it in some Text View.
Kerning is a fancy way of saying the spacing between the characters in a font. Getting kerning right can make a subtle, but positive to your apps. And getting it worse can have the opposite effect.

### Font

How font size works in IOS? IOS has a wey to increase or decrease the font size in your apps. This is very helpfull for people who wants to see big letters or has problems to read. However, if you just choose a hard-coded font size for your fonts, like say 12 points, then your app wouldn't benefit from this feature which will be frustrating for some users. So instead of hardcoding the font size, apple encourages you to use the built-in text styles that they provide like the title text style that you just saw. There are also styles for headlines, body, captions and so on. Let's see how we can choose the proper built-in text style for this label [Apple Docs](https://developer.apple.com/design/human-interface-guidelines/ios/visual-design/typography/) We can choose for example .footnote.

## Objects, Data & Methods

Programmers like to group related data and functionality into small pieces, so to do this you define a "template". Once you have that template you can create multiple instances of that template, you can think of instances as just filled version of those templates. There are two main ways to define these templates in Swift, you can either use the keyword class, or you can use the keyword struct. In some programming languages class and struct are radically different in functionality. Usually you can do a lot more with classes than you can with structs, but in Swift, structs are very powerful and full featured. So the differences between the two are a lot more subtle.
You can think of your Swift App as a bung of classes of structs templates that communicate each other. IOS provides many templates for you, such as the Button or Text Views, and sometimes you have to create your own, like you do in your ContentView. A class or struct, or an instance of a class or struct could have both data and functionality.
The part that provides functionality is commonly called a method, there's also the term function used in Swift. A method is simply a function that belongs to an instance (Ex: TextView bold, and kerning).
In Swift the way you store data on an instance is through something called a property. And there are two main types of properties provided by Swift.

1. Stored Properties, this is when you want the instance to simply store a piece of data for you, like the subtotal of a bill or the tax that you need to pay. Second.
   Ex:
   ```
     var subtotal: Double
     var tax: Double
   ```
2. Computed Properties, this is when you want an instance to run some code that you write in order to calculate the piece of data. For example: the total bill based on the subtotal and tax Stored Properties that you created earlier.
   `var total: Double { return subtotal + tax }`
   Key Points:  
    a. Your app is made up of instances of classes or structs.
   b. These contains two things: 1. Data 2. Methods

## Buttons & Actions

When you add a button view you can notice that if you press that button it doesn't do anything in the emulator, that's because we need to add the behaviour for it, and we can do this by adding code in the first parameter that the Button receives, which is action.

```
      Button(action: {
        print("Hello SwiftUI")
      }) {
        Text("Hit me")
      }
```

And then we can run the app in the simulator and we can notice everytime we click the button we will see "Hello SwiftUI" in the output console
CMD+R is a shortcut to run the app in the simulator.
Prints is an example of a function. A function is like a method, except that it's not attached to any particular instance. Not being attached to a class or a struct, means that you can use it without having to name an instance first. In Swift eveytime you see a name that starts with lowercase letter, that's immediately followed by parentheses, such as font, weight, or print. You're probably looking at the name of a function or a method. The difference is that methods are proceeded by the instance that you're calling the method on while functions don't belong to any instance and simply appear on their own. The print function takes in some text and prints it in XCode's console.

## SwiftUI State

We declare a state using @State and whenever this changes SwiftUI will compute the body again. You are forced to develop your apps in such a way so that your user interface and your state are always consistent. To do this, you keep track of your app state using variables marked with @State. Each state variable will have an initial value, then when the app starts up, IOS calls body to get a dashboard based on the current app state.

```
  @State private var alertIsVisible: Bool = false
  ...
  Button(action: {
    print("Hello SwiftUI")
    self.alertIsVisible = true
  }) {
    Text("Hit me")
  }
```

## SwiftUI Bindings

SwiftUI was designed to solve the problem of the mismach between your user interface and your application state. And one of the ways that SwiftUI provides to help with this is something called bindings. Bindings are a fancy way of saying that a particular user interface view will always be tied to a particular state value. The way you convert a state variable to a binding is using the dolar sign. Example:

```
  @State private var sliderValue: Double = 50.0
  ...
  ...
  Slider(value: self.$sliderValue, in: 1.0...100.0)
```

## Strings

To create a string in Swift you simply surround some text by some quotes. Now behind the scenes, strings are just a sequence of characters. String in swift have a feature called interpolation "Hello, \(name)!" this is kind of a placeholder that is replaced dynamically by code when the app runs.

## Variables

A variable allows your app to remember things, you can think about that as a temporary storage container for a single piece of data. You don't just put stuff in the container and then forget about it. You'll often replace this contents with a new value later on, that's the whole point behand variables, they can vary. This is the syntax to create a variable in Swift.

```
  @State private var variableName: Type = InitalValue
```

If this variable is a property on a class or struct, you can optionally put private, and that will mark it as private only accesible by the particular class or struct. We use the keyword 'var' to create a variable that we can change, I mean it can vary, on the contrast, if that variable won't change we can use the keyword 'let'. Types:

1. Bool, which is a varialble that can be true or false.
2. Double, numbers with decimal values, we use a dot to separate integers from decimals.
3. Int, integers.
4. Float.
5. String, is a collection of characters, we declare it with quotes.

So you may think how can we convert one type to another, like for example a Float to Integer. It turns out that you can create another Int given a double value, that process is called casting, and we can do it with the following:

```
  var x: Float = 3.14
  var y: Int = x // error
  var y: Int = Int(x)
```

We said that a variable is a temporary storage container, but how long will store its contents? Well, each variable has a certain lifetime, that depends on exactly where in your program you define that variable. In the case of the Slider, the value will stick around for just as long as its owner content view does. Their fates are intertwined. The ContentView and the Slider value are there for the duration of the app. They don't get destroyed until the app quits. There also variables that are short-lived variables known as local variables.
The concept of how long variable lives, is often called scopes.

## App Architecture

The ContentView job is to display the user interface for the app. Asking ContentView to worry about the gameplay logic in addition, would be violating our single responsability principle, because it would have more than one job. We want our classes and structs to be lazy, so instead it will be better to create a new struct that handles all of the gameplay logic and we can call it Game. Objects like this new game class or struct that are responsible for you app's data are commonly called model classes. When you're thinking about app architecture, you also need to to think about how these objects are connected, how they can communicate. In this case, we want our view classes to have an instance of the game model as property. The view classes can then communicate with the model classes whenever they need to interact with the app's data. We don't want the view to call methos on, or even know about the views. This makes the model classes more independent and therefore more reusable and more testeable.

## Creating a method in Swift

```
  func yourMethodName(parameterName: ParameterType) -> ReturnType {
    // Your code here!
    return yourReturnValue
  }
```

## Swift Standard Library

The swift language comes with many pre-built data type and functions you can use any of your own apps to solve a variety of common programming tasks called the Swift Standard Library. The data types int, double, string and bool are all part of the Swift Standard Library. The print method that you use to print a message is also a part of the Swift Standard Library. XCode has its own detailed developer documentation, that includes every single class or method that you can use in IOS including everything in the Swift Standard Library. Press shift+comand+0 to open de documentation.

## Unit Testing

Unit testing is when you write coe to test your other code. The nice thing about testing is that you can write it once, and then you can use them forever. XCode makes unit testing super easy with nice built-in support.

```
  class YourTestCaseName: XCTestCase {
  }
```

Each test needs to provide a setup and a tear down method. The setup method does everything you need to do to get rid for your other tests.

```
  class YourTestCaseName: XCTestCase {
    override func setUpWithError() throws {
      // your code here
    }

    override func tearDownWithError() throws {
      // your code here
    }
  }
```

Finally you add a method into your test case for every test that you want to run. You can put any code you want into these tests, but at some point you should call some special built-in functions that apple provided to test whether what actually happened matches what you expect to happen.

```
  class YourTestCaseName: XCTestCase {
    override func setUpWithError() throws {
      // your code here
    }
    override func tearDownWithError() throws {
      // your code here
    }
    func yourTestName() throws {
      // your code here
    }
  }
```

This special built-in functions are called Asserts, and these are function you can call a test if something you expect to work in a certain way actually doesn't practice. There are manny types of asserts

1. XCTAssertTrue
2. XCTAssertEqual
3. XCTAssertGreaterThan
4. ...and many more.

We can run tests in different ways:

1. Go to Product -> Test (command+U), this will run the app and all tests.
2. Another way is to click the checkmarks and then you will run an specific test or a group of tests.

## Test-Driven Development

The basic idea of test-driven development is that rather than writing the test after you write your code, you write your test first. Obviously, at first your test will fail because you haven't actually written the code yet. But then when you write your code, you have some more confidence that it works exactly the way that you intended it to. One of the nice things about test-driven development is that it forces you tu put some thought upfront about how you want your code to work before you write the code. It's also a great way to ensure that you definitely take the time to write tests for all your code, instead of forgetting to test some parts.

## Variables & constants

Swift makes a distinction between the variables and constants. The keyword var creates variable while let creates a constant. Whenever you declare a variable that will never change in swift, it's better to make it a constant with let, that makes your intent clear, which in turn helps the swift compiler to understand your program better. That way, the swift compiler can optimize your code as much as posible.
