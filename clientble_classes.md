# [ClientBleAndroidDoc](https://sdkpay.github.io/ClientBleAndroidDoc/)

#### [Сценарии работы с SDK](https://sdkpay.github.io/ClientBleAndroidDoc/clientble_scenario) | [Сущности и классы](https://sdkpay.github.io/ClientBleAndroidDoc/clientble_classes) | [Актуальная версия SDK](https://sdkpay.github.io/ClientBleAndroidDoc/clientble_version)

<br>

# Классы в ClientBle SDK

<br>

### Класс ClientBleSdk

Класс, через который происходит всё взаимодействие с SDK

Пример старта SDK:

```kotlin
ClientBleSdk
    .getInstance()
    .pay(BleSdkConfig())
```

Открытые функции класса:
- pay(config: BleSdkConfig) - запускает оплату в SDK
- startBackgroundPayment(config: BleSdkConfig) - запускает поиск терминала в фоне. Если терминал будет обнаружен, то будет открыто SDK автоматически
- stopBackgroundPayment() - отменяет поиск терминала в фоне
- logout(context: Context) - производит деавторизацию пользователя в SDK

### Класс BleSdkConfig

Класс-конфигуратор. Данный класс служит для настройки SDK

Параметры класса:
- context: Context - android контекст
- apiKey: String - ключ мерчанта
- appPackageName: String - package-имя приложения мерчанта
- applicationName: String - название приложения мерчанта
- typeface: SdkTypeface - класс шрифтов
- callBack: PaymentResult - callback с результатом оплаты (typealias PaymentResult = (BleSdkResult) -> Unit)

### Класс SdkTypeface

Класс шрифтов, которые используется в SDK

Параметры класса:
- main: Typeface - основной шрифт (sans_text)
- semibold: Typeface - полужирный шрифт (sans_display_semibold)

### Класс PaymentResult

typealias над лямбдой (BleSdkResult) -> Unit

Код класса:
```kotlin
typealias PaymentResult = (BleSdkResult) -> Unit
```

### Класс BleSdkResult

Класс хранящий результат работы SDK

Параметры класс:
- state: SPayState - состояние оплаты
- description: String - описание завершения сценария

### Класс SPayState

enum класс с перечисленными в нём состоянимями оплаты

Состояния:
- SUCCESS - Оплата успешно произведена
- FAIL - Во время оплаты произошла ошибка
- CANCEL - Пользователь самостоятельно покинул SDK
- WAITING - Оплата поизводится
