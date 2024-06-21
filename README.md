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
