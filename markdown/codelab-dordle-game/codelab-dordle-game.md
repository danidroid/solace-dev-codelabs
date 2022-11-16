author: danidroid
summary:
id: codelab-dordle-game
tags:
categories:
environments: Web
status: Published
feedback link: https://github.com/danidroid/solace-dev-codelabs/blob/master/markdown/codelab-dordle-game

# Flutter Games Workshop - FlutterFaro #2 - Dordle Game Code Lab

## What you'll learn: Overview

Duration: 0:05:00

Flutter-Faro is part of the Flutter Meetup Network and is bringing some events to the local community related, you guess, with Flutter !! :) Join us!

### Doordle Game - a Wordle game alternative

![Soly Image Caption](img/event_cover.png)

## What you need: Prerequisites

Duration: 0:07:00

# ⚠️ Required materials

Computer with internet access :) The course will run on all of the latest versions of the popular browsers. For the best experience, the laptop should have Flutter installed on it prior to starting the study jam to save time. Windows/Linux/Mac would all be fine.

Check out: [Setup Flutter](https://flutter.dev/docs/get-started/install)
After you should be able to run `flutter doctor` without any errors.

A device to connect to the laptop (iOS or Android ) OR an Emulator (iOS or Android)
[Android Studio](https://developer.android.com/studio) or [VS Code](https://code.visualstudio.com/) installed with Dart and Flutter Plugins

### lets start :D

![Game Page](img/dordle_game.png)

## Step 1 - main.dart

Lets start by creating a new demo project, edit the `main.dart` file:

```dart
void main() {
  runApp(const MyApp());
}
```

```dart
class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Dordle Game',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      scaffoldMessengerKey: scaffoldMessengerKey,
      home: const GamePage(),
    );
  }
}
```

## Step 2 - Game Page

So now its time to start building the game page, lets start by creating a new [StatefulWidget](https://api.flutter.dev/flutter/widgets/StatefulWidget-class.html)

```dart
class GamePage extends StatefulWidget {
  const GamePage({super.key});

  @override
  State<GamePage> createState() => _GamePageState();
}
```

```dart
class _GamePageState extends State<GamePage> {
  
  @override
  Widget build(BuildContext context) {
    // TODO: implement build
    throw UnimplementedError();
  }
}
```

Will see that this will throw an error, keep calm, will fix that shortly...

## Step 3 - Game UI

So, now that we have a red screen in our simulator, lets fix that, by changing the 

```dart
...
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      backgroundColor: Colors.black,
      body: SafeArea(
        bottom: false,
        child: Flex(
          mainAxisAlignment: MainAxisAlignment.spaceBetween,
          direction: Axis.vertical,
          children: [],
        ),
      ),
    );
}
...
```

Saving it, will get rid of the red error, but now is plain black!!!

Lets fix it again, lets create the `GameGridView` widget into to the `Flex` widget children:

```dart
...
Flex(
    ...
    children: [
        GameGridView()
    ],
)
...
```

## Step 4 - Game UI - GameGridView

Now will start by creating the `GameGridView` widget:

Can create this in the same file

```dart
class GameGridView extends StatelessWidget {
  const GameGridView({super.key});

  @override
  Widget build(BuildContext context) {
    return Expanded(
      flex: 2,
      child: Container(
        padding: const EdgeInsets.symmetric(horizontal: 16, vertical: 16),
        child: GridView.builder(
            physics: const NeverScrollableScrollPhysics(),
            itemCount: 25,
            gridDelegate: const SliverGridDelegateWithFixedCrossAxisCount(
                mainAxisSpacing: 0.1,
                crossAxisSpacing: 0.1,
                childAspectRatio: 1.0,
                crossAxisCount: 5),
            itemBuilder: (BuildContext context, int index) {
              return Container();
            }),
      ),
    );
  }
}
```

hmm, no changes right? same black plain screen, so much code and no changes!!!

Lets update create a new `GameGridBoxView` widget:

```dart
class GameGridBoxView extends StatelessWidget {
  const GameGridBoxView({
    Key? key,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container(
      width: 40,
      height: 40,
      margin: const EdgeInsets.all(8),
      alignment: Alignment.center,
      decoration: const BoxDecoration(
        color: Color(0xff858b8b),
        borderRadius: BorderRadius.all(
          Radius.circular(8.0),
        ),
      ),
      child: const Text(""),
    );
  }
}
```

hmm still nothing?? can you figure out what is missing?

## Step 4 - Game UI - GameGridView

Correct!!! will need to change this line in the `GridView.builder`:

```dart
    itemBuilder: (BuildContext context, int index) {
        return Container();
    }),     
```

Replace the `Container()` with `GameGridBoxView()`

Finally we see somthing!!!

You can tweak the numbers on the grid to experiment and hot-reload to see the changes.

## Takeaways

Duration: 0:07:00

✅ < Fill IN TAKEAWAY 1>   
✅ < Fill IN TAKEAWAY 2>   
✅ < Fill IN TAKEAWAY 3>   

![Soly Image Caption](img/soly.gif)

Thanks for participating in this codelab! Let us know what you thought in the [Solace Community Forum](https://solace.community/)! If you found any issues along the way we'd appreciate it if you'd raise them by clicking the Report a mistake button at the bottom left of this codelab.
