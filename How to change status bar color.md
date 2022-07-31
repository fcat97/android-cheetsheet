# How to change status bar color in Android?

### Old way

```kotlin
class CostActivity: ComponentActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)

        val mode = resources?.configuration?.uiMode?.and(Configuration.UI_MODE_NIGHT_MASK)
        if (mode == Configuration.UI_MODE_NIGHT_YES) {
            window.statusBarColor = lightSoftBlack.toArgb()
        } else {
            window.decorView.systemUiVisibility = View.SYSTEM_UI_FLAG_LIGHT_STATUS_BAR
            window.statusBarColor = softWhite.toArgb()
        }
    }   
}
```

### New Way with jetpack compose

> Add dependency
```gradle
def accompanist_version = '0.23.1'
inplementation "com.google.accompanist:accompanist-systemuicontroller:$accompanist_version"
```

> Now in `@Composable` function
```kotlin
// Remember a SystemUiController
val systemUiController = rememberSystemUiController()

// change status bar color to background color
SideEffect {
    systemUiController.setStatusBarColor(
        color = backgroundColor
    )
}
```
