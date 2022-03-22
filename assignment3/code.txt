import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  // This widget is the root of your application.
  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'SE 373 Assignment',
      theme: ThemeData(
        primarySwatch: Colors.green,
      ),
      home: const MyHomePage(title: 'SE 373 Assignment'),
    );
  }
}

class MyHomePage extends StatefulWidget {
  const MyHomePage({Key? key, required this.title}) : super(key: key);



  final String title;

  @override
  State<MyHomePage> createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  int counter = 0; //this is my counter state
  String secondButtonText = "Second Button"; //this is my state for second button
  bool checkBoxState = false;
  bool isSecondButtonClicked = false;
  void sayHello(){
    setState(() {
      secondButtonText = "Hello!"; //i'm changing this state when this function is called
      checkBoxState = !checkBoxState; //i'm inverting this state when this function is called
      isSecondButtonClicked = true; //i'm changing this state when this function is called
    });
  }
  void incrementCounter() {
    setState(() {
      //i'm changing the state named counter when this function is called
      counter++;
    });
  }

  @override
  Widget build(BuildContext context) {

    return Scaffold(
      appBar: AppBar(

        title: Text(widget.title),
      ),
      body: Center(


        child: Column(

          mainAxisAlignment: MainAxisAlignment.center,
          children: <Widget>[Row(mainAxisAlignment: MainAxisAlignment.center ,
            children: [
              Checkbox(value: checkBoxState, onChanged: null),
              Checkbox(value: !checkBoxState, onChanged: null),
            ],
          ),
            ElevatedButton(onPressed: sayHello, child: Text(secondButtonText)),
            Text(isSecondButtonClicked ? "Second button is clicked!" : "Second button is not cliked yet!"),
            ElevatedButton(onPressed: incrementCounter, child: Text("Increase")) //this is the button widget, onPressed argument passed as _incrementCounter
            ,
            Text(
              '$counter',
              style: Theme.of(context).textTheme.headline4,
            ),
          ],
        ),
      ),

    );
  }
}