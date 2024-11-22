# Flutter and Dart Programming Tutorial

## Module 2: Dart Programming Fundamentals
**Objective**: Establish a solid foundation in Dart programming.

### Basic Syntax and Structure

#### Data Types, Variables, and Operators

##### Data Types
Dart is a statically-typed language, meaning you must specify the type of variables. Common data types include:
- Numbers: `int` (integer), `double` (floating-point)
- Strings: `String`
- Booleans: `bool`
- Lists: `List`
- Maps: `Map`

##### Variables
Variables store data and are declared using `var`, explicit types, or constants using `final` and `const`.

```dart
// Using var (type inferred)
var name = 'Alice';
// Explicit type declaration
int age = 30;
// Constants
final DateTime now = DateTime.now(); // Runtime constant
const double pi = 3.1416; // Compile-time constant
```

##### Operators
Operators perform operations on variables and values.
- Arithmetic Operators: `+`, `-`, `*`, `/`, `%`, `~/` (integer division)
- Assignment Operators: `=`, `+=`, `-=`, etc.
- Comparison Operators: `==`, `!=`, `>`, `<`, `>=`, `<=`
- Logical Operators: `&&`, `||`, `!`

Example:
```dart
int a = 10;
int b = 3;
int sum = a + b; // 13
int diff = a - b; // 7
int product = a * b; // 30
double quotient = a / b; // 3.333...
int intQuotient = a ~/ b; // 3
int remainder = a % b; // 1
bool isEqual = a == b; // false
bool isGreater = a > b; // true
```

### Control Structures

#### Loops and Conditionals

##### Conditionals
If-Else Statement:
```dart
int score = 85;
if (score >= 90) {
  print('Grade: A');
} else if (score >= 80) {
  print('Grade: B');
} else {
  print('Grade: C');
}
```

Switch Statement:
```dart
String command = 'OPEN';
switch (command) {
  case 'OPEN':
    print('Opening');
    break;
  case 'CLOSE':
    print('Closing');
    break;
  default:
    print('Unknown command');
}
```

##### Loops
For Loop:
```dart
for (int i = 0; i < 5; i++) {
  print('Iteration $i');
}
```

While Loop:
```dart
int count = 0;
while (count < 5) {
  print('Count is $count');
  count++;
}
```

Do-While Loop:
```dart
int count = 0;
do {
  print('Count is $count');
  count++;
} while (count < 5);
```

For-In Loop (Iterating over collections):
```dart
List<String> fruits = ['Apple', 'Banana', 'Cherry'];
for (var fruit in fruits) {
  print(fruit);
}
```

### Functions and Classes

#### Defining and Using Functions

##### Functions
Functions encapsulate reusable code blocks.
```dart
// Function with no return type
void greet(String name) {
  print('Hello, $name!');
}
// Function with return type
int add(int x, int y) {
  return x + y;
}
// Arrow function (short-hand syntax)
int multiply(int x, int y) => x * y;
```

Usage:
```dart
greet('Alice'); // Output: Hello, Alice!
int sum = add(5, 3); // sum = 8
int product = multiply(4, 2); // product = 8
```

#### Object-Oriented Programming Concepts

##### Classes and Objects
Defining a Class:
```dart
class Person {
  // Properties
  String name;
  int age;
  // Constructor
  Person(this.name, this.age);
  // Method
  void introduce() {
    print('My name is $name, and I am $age years old.');
  }
}
```

Creating an Object:
```dart
void main() {
  Person person = Person('Bob', 25);
  person.introduce(); // Output: My name is Bob, and I am 25 years old.
}
```

##### Inheritance
```dart
class Employee extends Person {
  String position;
  Employee(String name, int age, this.position) : super(name, age);
  @override
  void introduce() {
    super.introduce();
    print('I work as a $position.');
  }
}
void main() {
  Employee employee = Employee('Carol', 28, 'Engineer');
  employee.introduce();
  // Output:
  // My name is Carol, and I am 28 years old.
  // I work as a Engineer.
}
```

### Exception Handling and Asynchronous Programming

#### Try-Catch Blocks
Exception Handling:
```dart
void main() {
  try {
    int result = 10 ~/ 0; // Division by zero
  } catch (e) {
    print('An error occurred: $e');
  } finally {
    print('Execution completed.');
  }
}
```

#### Futures and Async-Await

##### Futures
A Future represents an asynchronous operation that returns a value in the future.
```dart
Future<String> fetchData() {
  return Future.delayed(Duration(seconds: 2), () => 'Data loaded');
}
void main() {
  fetchData().then((data) {
    print(data); // Output after 2 seconds: Data loaded
  });
}
```

##### Async-Await
Simplifies working with futures.
```dart
Future<void> main() async {
  print('Fetching data...');
  String data = await fetchData();
  print(data); // Output after 2 seconds: Data loaded
}
```

## Module 3: Flutter Basics
**Objective**: Introduce core Flutter concepts and project structure.

### Understanding Flutter's Architecture

#### Widgets, Rendering, and Framework Layers

##### Widgets
- Widgets are the basic building blocks of a Flutter app's user interface
- Every component in Flutter is a widget, including layout models, controls, and styles

##### Rendering
- Flutter uses its own rendering engine, Skia, to draw widgets
- The rendering process converts the widget tree into pixels on the screen

##### Framework Layers
- Widgets Layer: High-level, platform-independent widgets
- Rendering Layer: Layout and painting of widgets
- Foundation Layer: Core building blocks and utilities

### Exploring the Flutter Project Structure

#### Directories and Files
Typical Project Structure:
```
my_app/
├── android/
├── ios/
├── lib/
│   └── main.dart
├── pubspec.yaml
├── test/
```

- `lib/`: Contains Dart code
- `main.dart`: Entry point of the app
- `android/`: Android-specific files
- `ios/`: iOS-specific files
- `pubspec.yaml`: Project configuration and dependencies
- `test/`: Unit tests

# Flutter Tutorial (Continued)

## Module 4: Widgets and UI Design
**Objective**: Learn to build user interfaces using Flutter's widget system.

### Introduction to Widgets

#### Stateless and Stateful Widgets

##### StatelessWidget
Immutable widgets that do not require mutable state.

Example:
```dart
class MyStatelessWidget extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Text('Hello, World!');
  }
}
```

##### StatefulWidget
Widgets that maintain mutable state. Consist of two classes: the StatefulWidget and its associated State.

Example:
```dart
class MyStatefulWidget extends StatefulWidget {
  @override
  _MyStatefulWidgetState createState() => _MyStatefulWidgetState();
}
class _MyStatefulWidgetState extends State<MyStatefulWidget> {
  int _counter = 0;
  void _incrementCounter() {
    setState(() {
      _counter++;
    });
  }
  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Text('Counter: $_counter'),
        ElevatedButton(
          onPressed: _incrementCounter,
          child: Text('Increment'),
        ),
      ],
    );
  }
}
```

### Building Layouts with Common Widgets

#### Container, Row, Column, Stack

##### Container
A versatile widget for layout, styling, and positioning.
```dart
Container(
  width: 100,
  height: 100,
  color: Colors.blue,
  child: Text('Hello'),
)
```

##### Row and Column
Row arranges children horizontally. Column arranges children vertically.

```dart
// Row Example
Row(
  mainAxisAlignment: MainAxisAlignment.spaceEvenly,
  children: [
    Icon(Icons.home),
    Icon(Icons.star),
    Icon(Icons.person),
  ],
)
// Column Example
Column(
  mainAxisAlignment: MainAxisAlignment.center,
  children: [
    Text('Line 1'),
    Text('Line 2'),
    Text('Line 3'),
  ],
)
```

##### Stack
Positions widgets on top of each other.
```dart
Stack(
  children: [
    Container(
      width: 200,
      height: 200,
      color: Colors.red,
    ),
    Positioned(
      top: 50,
      left: 50,
      child: Container(
        width: 100,
        height: 100,
        color: Colors.blue,
      ),
    ),
  ],
)
```

### Handling User Input with Form Widgets

#### TextField, Checkbox, Radio Buttons, Dropdowns

##### TextField
Input field for text.
```dart
TextField(
  decoration: InputDecoration(
    labelText: 'Enter your name',
  ),
)
```

##### Checkbox
Binary option widget.
```dart
bool _isChecked = false;
Checkbox(
  value: _isChecked,
  onChanged: (bool? newValue) {
    setState(() {
      _isChecked = newValue!;
    });
  },
)
```

##### Radio Buttons
Select one option from a group.
```dart
int _selectedValue = 1;
Column(
  children: [
    Radio<int>(
      value: 1,
      groupValue: _selectedValue,
      onChanged: (int? value) {
        setState(() {
          _selectedValue = value!;
        });
      },
    ),
    Radio<int>(
      value: 2,
      groupValue: _selectedValue,
      onChanged: (int? value) {
        setState(() {
          _selectedValue = value!;
        });
      },
    ),
  ],
)
```

##### DropdownButton
Select one option from a dropdown list.
```dart
String _selectedItem = 'Apple';
DropdownButton<String>(
  value: _selectedItem,
  items: <String>['Apple', 'Banana', 'Cherry'].map((String value) {
    return DropdownMenuItem<String>(
      value: value,
      child: Text(value),
    );
  }).toList(),
  onChanged: (String? newValue) {
    setState(() {
      _selectedItem = newValue!;
    });
  },
)
```

### Implementing Navigation and Routing

#### Navigator Class, Named Routes, Passing Data Between Screens

##### Basic Navigation
Using Navigator.push:
```dart
// Navigate to SecondScreen
Navigator.push(
  context,
  MaterialPageRoute(builder: (context) => SecondScreen()),
);
// SecondScreen Widget
class SecondScreen extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Center(child: Text('Second Screen')),
    );
  }
}
```

##### Named Routes
Define Routes in MaterialApp:
```dart
MaterialApp(
  initialRoute: '/',
  routes: {
    '/': (context) => HomeScreen(),
    '/second': (context) => SecondScreen(),
  },
);
// Navigate Using Named Routes
Navigator.pushNamed(context, '/second');
```

##### Passing Data Between Screens
```dart
// Passing Data
Navigator.push(
  context,
  MaterialPageRoute(
    builder: (context) => SecondScreen(data: 'Hello from HomeScreen'),
  ),
);
// Receiving Data in SecondScreen
class SecondScreen extends StatelessWidget {
  final String data;
  SecondScreen({required this.data});
  @override
  Widget build(BuildContext context) {
    return Text(data);
  }
}
```

## Module 5: State Management
**Objective**: Understand and implement state management in Flutter applications.

### Overview of State Management Approaches
- Local State: Managed within a single widget using setState
- Global State: Shared across multiple widgets or the entire app

### Using setState() for Local State Management

#### Updating UI in Stateful Widgets
```dart
class CounterWidget extends StatefulWidget {
  @override
  _CounterWidgetState createState() => _CounterWidgetState();
}
class _CounterWidgetState extends State<CounterWidget> {
  int _counter = 0;
  void _incrementCounter() {
    setState(() {
      _counter++; // Updates the UI
    });
  }
  @override
  Widget build(BuildContext context) {
    return Column(
      children: [
        Text('Counter: $_counter'),
        ElevatedButton(
          onPressed: _incrementCounter,
          child: Text('Increment'),
        ),
      ],
    );
  }
}
```

### Introduction to Provider for Global State Management

#### Managing App-Wide State

##### Adding Provider Dependency
In pubspec.yaml:
```yaml
dependencies:
  provider: ^6.0.0
```
##### Creating a ChangeNotifier
```dart
class Counter extends ChangeNotifier {
  int _count = 0;

  int get count => _count;

  void increment() {
    _count++;
    notifyListeners(); // Notifies listeners to rebuild
  }
}
```

##### Providing the ChangeNotifier
```dart
void main() {
  runApp(
    ChangeNotifierProvider(
      create: (context) => Counter(),
      child: MyApp(),
    ),
  );
}
```

##### Consuming the Provider
```dart
class CounterDisplay extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    int count = Provider.of<Counter>(context).count;
    return Text('Count: $count');
  }
}
class IncrementButton extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return ElevatedButton(
      onPressed: () => Provider.of<Counter>(context, listen: false).increment(),
      child: Text('Increment'),
    );
  }
}
```

### Other State Management Solutions

#### Bloc Pattern
##### Adding Bloc Dependency
```yaml
dependencies:
  flutter_bloc: ^8.0.0
```
##### Creating a Bloc
```dart
enum CounterEvent { increment }

class CounterBloc extends Bloc<CounterEvent, int> {
  CounterBloc() : super(0) {
    on<CounterEvent>((event, emit) {
      if (event == CounterEvent.increment) {
        emit(state + 1);
      }
    });
  }
}
```

##### Using BlocProvider and Consuming Bloc
```dart
// Provider
BlocProvider(
  create: (context) => CounterBloc(),
  child: MyApp(),
)
// Consumer
BlocBuilder<CounterBloc, int>(
  builder: (context, count) {
    return Text('$count');
  },
);
ElevatedButton(
  onPressed: () => context.read<CounterBloc>().add(CounterEvent.increment),
  child: Text('Increment'),
);
```

#### Riverpod
##### Adding Riverpod Dependency
```yaml
dependencies:
  flutter_riverpod: ^1.0.0
```
##### Using Riverpod
```dart
// Defining a Provider
final counterProvider = StateProvider<int>((ref) => 0);

// Consuming the Provider
Consumer(
  builder: (context, ref, child) {
    int count = ref.watch(counterProvider).state;
    return Text('Count: $count');
  },
);

ElevatedButton(
  onPressed: () {
    ref.read(counterProvider).state++;
  },
  child: Text('Increment'),
);
```
