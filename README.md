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
