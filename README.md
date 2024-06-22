# Chapter 1: Building your first Compose App
![image](https://github.com/chihyeonwon/Kotlin_Compose/assets/58906858/e4dfd5c1-56f4-4dd9-b8a1-cb6f85f9b1a0)
```kotlin
class MainActivity : ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContent {
            Welcome()
        }
    }
}

@Composable
@Preview
fun Welcome() {
    Text(
        text = stringResource(id = R.string.welcome,),
        style = MaterialTheme.typography.titleSmall
    )
}
```
```
Flutter와 마찬가지로 선언적 UI를 사용함에 따라 @Preview 어노테이션을 사용하여서 바로 변경사항을 미리 볼 수 있다. (flutter의 hot-reloading과 동일)

```
![image](https://github.com/chihyeonwon/Kotlin_Compose/assets/58906858/f74ad741-fa77-4faa-8e3c-dafbd22b7957)
```kotlin
@Composable
@Preview
fun Greeting(name: String = "원치현") {
    Text(
        text = stringResource(id = R.string.hello, name),
        textAlign = TextAlign.Center,
        style = MaterialTheme.typography.titleMedium
    )
}
```
string.xml
```kotlin
<string name="hello">Hello, %1$s \nNice to meet you.</string>
```
```
strings에 문자열을 html로 넣어서 읽을 수 있다. @Preview 미리보기를 사용하기 위해 함수의 매개변수에 기본 값으로 이름을 넣어주었다.
```
## 컴포즈의 미리보기 기능
![image](https://github.com/chihyeonwon/Kotlin_Compose/assets/58906858/df72c0dc-3901-49ac-9565-9cc681dc5081)
```
SetContent 에서 Hello 함수와 Greeting 함수 중 Hello만 넣고 기기를 실행하면 실제 에뮬레이터에는 Hello 함수만 실행되어 보이지만
미리보기 화면에서는 Hello와 Greeting이 모두 보이는 것을 알 수 있다.
```
## Row, TextField
```kotlin
@Composable
fun TextAndButton(name: MutableState<String>, nameEntered: MutableState<Boolean>) {
    Row(modifier = Modifier.padding(top = 8.dp)) {
        TextField(
            value = name.value,
            onValueChange = {
                name.value = it
            },
            placeholder = {
                Text(text = stringResource(id = R.string.hint))
            },
            modifier = Modifier
                .alignByBaseline()
                .weight(1.0F),
            singleLine = true,
            keyboardOptions = KeyboardOptions(
                autoCorrect = false,
                capitalization = KeyboardCapitalization.Words,
            ),
            keyboardActions = KeyboardActions(onAny = {
                nameEntered.value = true
            })
        )
    }
}
```
```
Flutte와 유사하게 Row, Column으로 레이아웃의 배치를 한다.
Row는 modifier 매개변수를 받고 외형과 행위에 영향을 준다.

Row안에 여러 컴포저블 함수를 배치한다.
```
```kotlin
  Button(modifier = Modifier
            .alignByBaseline()
            .padding(8.dp),
            onClick = {
                nameEntered.value = true
            }) {
            Text(text = stringResource(id = R.string.done))
```
```
Row 안에 Button 컴포저블 함수를 추가했다. 버튼을 클릭하면 nameEntered의 값의 상태를 true로 변경한다.
```
![2024-06-22 11;26;12](https://github.com/chihyeonwon/Kotlin_Compose/assets/58906858/9b7e96f6-d5f0-458e-b959-b2045689fe03)
```kotlin
@Composable
fun Hello() {
    val name = remember { mutableStateOf("") } // 상태 생성: mutableStateOf 상태 기억: remember
    val nameEntered = remember { mutableStateOf(false) }
    Box(
        modifier = Modifier
            .fillMaxSize()
            .padding(16.dp),
        contentAlignment = Alignment.Center
    ) {
        if (nameEntered.value) {
            Greeting(name.value)
        } else {
            Column(horizontalAlignment = Alignment.CenterHorizontally) {
                Welcome()
                TextAndButton(name, nameEntered)
            }
        }
    }
}
```
```
mutableStateOf 는 상태를 생성하고 remember는 상태를 기억한다.
Column은 Row(가로)와 마찬가지로 컴포저블 요소의 위치 상태를 세로로 결정한다.
위 코드를 실행하면 nameEntered.value가 true라면 Greeting의 매개변수로 전달한다. (TextButton 클릭 시 true로 변경됨)
버튼 클릭 하기 전에는 Welcome와 TextAndButton을 실행한다.
```
## 미리 보기 설정
![image](https://github.com/chihyeonwon/Kotlin_Compose/assets/58906858/17f1fbb6-1090-4bc0-a39e-1bb81550a77b)
```kotlin
@Preview(showBackground = true, backgroundColor = 0xffff0000)
```
```
Preview 어노테이션에 showBackground 속성과 backgroundColor 속성을 이용하여 미리보기의 배경색을 설정할 수 있다.
```
![image](https://github.com/chihyeonwon/Kotlin_Compose/assets/58906858/04e968f9-a3f9-4a4a-843b-0b4f71df6142)
```kotlin
@Preview(widthDp = 100, heightDp = 100)
```
```
widthDp와 heightDp 속성값을 이용하여 미리 보기의 면적을 지정할 수 있다. (.dp는 생략, 밀도 독립 픽셀)
```













