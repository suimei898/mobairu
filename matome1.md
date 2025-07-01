# デフォルトのmain.dart
サンプル
```
import 'package:flutter/material.dart';

void main() {
  runApp(const MyApp());
}

class MyApp extends StatelessWidget {
  const MyApp({Key? key}) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Flutter Demo',
      theme: ThemeData(
        primarySwatch: Colors.blue,
      ),
      home: const MyHomePage(title: 'Flutter Demo Home Page'),
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
  int _counter = 0;

  void _incrementCounter() {
    setState(() {
      _counter++;
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
          children: <Widget>[
            const Text(
              'You have pushed the button this many times:',
            ),
            Text(
              '$_counter',
              style: Theme.of(context).textTheme.headline4,
            ),
          ],
        ),
      ),
      floatingActionButton: FloatingActionButton(
        onPressed: _incrementCounter,
        tooltip: 'Increment',
        child: const Icon(Icons.add),
      ),
    );
  }
}
```
実行するとメッセージと「0」という数字が画面中央に表示されます。「＋」アイコンをクリックすると、数字が一つずつ増えていきます。
# main.dartの内容
## 1.MyAppクラス
buildメソッドでMaterialAppを作成し返す処理が用意されています。  
themeという値が追加されていますが、これはテーマを指定するためのものです。  
## 2.MyHomePageクラス
コンストラクタとcreateStateがあるだけのシンプルなクラスです。コンストラクタは以下のような形で用意されています。  
```
const MyHomePage({Key? key, required this.title}) : super(key: key);
```
引数の値をthis.titleに設定しています。その他に、Keyという値も渡されています。これは、ウィジェットを識別するためのIDのようなものです。  
ただし、MyAppクラスでこのMyHomePageインスタンスを作成している部分を見ると、こうなっているのがわかります。
```
const MyHomePage(title: 'Flutter Demo Home Page')
```
Keyの値は用意されていません。Keyは用意しなくとも自動的に割り当てられるのです。  
ただ、実際にこのキーは特に使われていません。
## 3.MyHomePageStateクラス
ステートの処理を行う_MyHomePageStateクラスでは、_counterというフィールドを用意しています。そして、setStateでは、この値を1ずつ増やす処理を用意してあります。  
この_counterの値をTextに表示するのに少し変わったやり方をしています。
```
Text (
  '$_counter',
……);
```
Textに表示するテキストに、'\$_counter'という値が指定されています。  
この\$_counterという値は、変数_counterをテキストリテラル内に埋め込んでいるものです。Dartでは、このように「$変数」という形で変数をリテラル内に埋め込むことができます。  
この他、CenterやColumnといったクラスが使われていますが、これらはレイアウトに関するウィジェットです。