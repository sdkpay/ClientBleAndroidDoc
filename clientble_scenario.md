# [ClientBleAndroidDoc](https://sdkpay.github.io/ClientBleAndroidDoc/)

#### [Сценарии работы с SDK](https://sdkpay.github.io/ClientBleAndroidDoc/clientble_scenario) | [Сущности и классы](https://sdkpay.github.io/ClientBleAndroidDoc/clientble_classes) | [Актуальная версия SDK](https://sdkpay.github.io/ClientBleAndroidDoc/clientble_version)

<br>

# Сценарии работы SDK

#### [Базовый сценарий](https://sdkpay.github.io/ClientBleAndroidDoc/clientble_scenario#базовый-сценарий-для-sdk)
#### [Фоновый сценарий](https://sdkpay.github.io/ClientBleAndroidDoc/clientble_scenario#фоновый-сценарий-для-sdk)
#### [Разлогирование_пользователя](https://sdkpay.github.io/ClientBleAndroidDoc/clientble_scenario#разлогирование-пользователя)

<br>

## Базовый сценарий для SDK

Чтобы запустить базовый сценарий нужно выполнить код:

```kotlin
ClientBleSdk
    .getInstance()
    .pay(BleSdkConfig())
```

## Фоновый сценарий для SDK

Фоновый сценарий запустится при соблюдении условия наличия пермиссий у приложения. Список пермиссий:

```kotlin
if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.S) {
    // Android 12+ (API 31+)
    arrayOf(
        Manifest.permission.ACCESS_FINE_LOCATION,
        Manifest.permission.ACCESS_COARSE_LOCATION,
        Manifest.permission.BLUETOOTH_SCAN,
        Manifest.permission.BLUETOOTH_CONNECT,
        Manifest.permission.BLUETOOTH_ADVERTISE,
    )
} else {
    // До Android 12 (включая API 28)
    arrayOf(
        Manifest.permission.BLUETOOTH,
        Manifest.permission.BLUETOOTH_ADMIN,
        Manifest.permission.ACCESS_FINE_LOCATION,
        Manifest.permission.ACCESS_COARSE_LOCATION,
    )
}

```

Чтобы запустить запуск SDK из фона нужно выполнить код:

```kotlin
ClientBleSdk
    .getInstance()
    .startBackgroundPayment(BleSdkConfig())
```

Чтобы прекратить отслеживания терминалов в фоне:

```kotlin
ClientBleSdk
    .getInstance()
    .stopBackgroundPayment()
```

## Разлогирование пользователя

Чтобы разлогировать пользователя нужно выполнить код:

```kotlin
ClientBleSdk
    .getInstance()
    .logout(context)
```