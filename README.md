# Learn-Flutter
## my path in learning flutter

### covered basics of dart, felt similar to kotlin
### watched introduction to widgets, bit similar to flex-box in css

### made a basic login page UI and connected it to firebase

### following tutorial: https://fluttercrashcourse.com/
### https://fluttercrashcourse.com/blog

### Tutorial overall
link: https://www.youtube.com/watch?v=eegl7of4g-o
Flutter TextField or TextFormField - Get values using Controller or onChanged :-
link: https://www.youtube.com/watch?v=ccHt0cfDsOM 

## starting a new project

#### VS Code from palette: ctrl+shift+P, flutter ...
link: https://docs.flutter.dev/development/tools/vs-code
From terminal:   flutter create project_one
link: https://www.woolha.com/tutorials/flutter-creating-new-project

### Naming conventions
The name should be all lowercase, with underscores to separate words, just_like_this.
link: https://dart.dev/tools/pub/pubspec#name

### Material app
building the app on the widget materialApp, it works with both android and ios. Also comes with nav bar and body.
Need to make a stateless or stateful widget to have a personal widget.
convention is to have a app.dart fiel which wraps the overall content

### Using templates
link: https://www.youtube.com/watch?v=ZT_rn5qqMTU&list=PL__UlMMmv_rz1CS6GLOYIn8x-eSb1tzjs&index=3

### controlling notification bar
link: https://stackoverflow.com/questions/43877288/how-to-hide-android-statusbar-in-flutter
code:
import 'package:flutter/services.dart';
$$ Hide Statusbar
	WidgetsFlutterBinding.ensureInitialized();
  SystemChrome.setEnabledSystemUIMode(SystemUiMode.manual, overlays: [
    SystemUiOverlay.bottom, //This line is used for showing the bottom bar
  ]);
$$ Transparant Statusbar
	SystemChrome.setSystemUIOverlayStyle(SystemUiOverlayStyle(statusBarColor: Colors.transparent,));
--- You need to put the above code on :-

For Single Screen:
@override
  void initState() {
    // put it here
    super.initState();
  }

For All pages in main.dart:
 void main() {
      // put it here
      runApp(...);
  }
  
### Adapttive screen
<- want the two colums to ompletely fill the device screen, but if the screen length is smaller than total length, i want it t be scrollable ->

link: https://medium.com/flutter-community/how-to-make-an-adaptable-layout-in-flutter-4abe8376f426

its done using ConstrainedBox, flex, math and so on

code:
import 'dart:math';
class AdaptableRow extends StatelessWidget {
  final minWidth = 500.0;  
  @override
  Widget build(BuildContext context) {
    final screenWidth = MediaQuery.of(context).size.width;
    return SingleChildScrollView(
      scrollDirection: Axis.horizontal,
      child: ConstrainedBox(
        constraints: BoxConstraints(
          maxWidth: max(screenWidth, minWidth),
        ),
        child: Row(
          children: [
            Expanded(
              flex: 2,
              child: Container(color: Colors.yellow),
            ),],),),);}}

### async:
await: waits for that function to complete before moving ahead
but needs the fun to be of 'future'

// run only after executing above fun:
WidgetsBinding.instance.addPostFrameCallback((_) {});

### subscript and superscript
A ⁰ ¹ ² ³ ⁴ ⁵ ⁶ ⁷ ⁸ ⁹ ⁺ ⁻ ⁼ ⁽ ⁾ 
A ₀ ₁ ₂ ₃ ₄ ₅ ₆ ₇ ₈ ₉ ₊ ₋ ₌ ₍ ₎ 
A ᵃ ᵇ ᶜ ᵈ ᵉ ᶠ ᵍ ʰ ⁱ ʲ ᵏ ˡ ᵐ ⁿ ᵒ ᵖ ʳ ˢ ᵗ ᵘ ᵛ ʷ ˣ ʸ ᶻ 
A ᴬ ᴮ ᴰ ᴱ ᴳ ᴴ ᴵ ᴶ ᴷ ᴸ ᴹ ᴺ ᴼ ᴾ ᴿ ᵀ ᵁ ⱽ ᵂ 
A ₐ ₑ ₕ ᵢ ⱼ ₖ ₗ ₘ ₙ ₒ ₚ ᵣ ₛ ₜ ᵤ ᵥ ₓ 
A ᵅ ᵝ ᵞ ᵟ ᵋ ᶿ ᶥ ᶲ ᵠ ᵡ ᵦ
A ᵧ ᵨ ᵩ ᵪ

### Publishing app
-- run:

$ flutter clean

$ flutter build apk --split-per-abi

This command results in three APK files :-
/build/app/outputs/apk/release/app-armeabi-v7a-release.apk
/build/app/outputs/apk/release/app-arm64-v8a-release.apk
/build/app/outputs/apk/release/app-x86_64-release.apk

-- after connecting device run:

$ flutter install 
