# Подключение к консоли управления роботом

Для управления Control Hub ([REV-31-1595](https://www.revrobotics.com/rev-31-1595/)) **** или его программирования с помощью встроенных языков программирования, компьютер или другое устройство с поддержкой Wi-Fi необходимо подключить к консоли управления роботом от Control Hub. Консоль управления роботом - это локальная сеть, созданная Control Hub для программирования и управления устройством.

{% hint style="info" %}
В данном примере предполагается, что пользователь использует Windows 10 в качестве операционной системы. Если вы не используете Windows 10, процедура подключения к сети будет отличаться. Подробные сведения о подключении к сети Wi-Fi см. в документации к вашему устройству.
{% endhint %}

По умолчанию Control Hub имеет имя, начинающееся с "FTC-" или "FIRST-", за которым следуют четыре символа, назначаемые случайным образом. Пароль по умолчанию для сети - "password". Если один из этих паролей забыт, существует [несколько способов восстановления или сброса пароли на узле управления](../updating-and-managing/managing-wi-fi-on-the-control-hub.md)[.](broken-reference)

Существует два способа доступа к консоли Robot Controller Console. В первом случае мы рассмотрим, как получить доступ к консоли Robot Controller Console с помощью аппаратного клиента REV. Рекомендуется использовать[REV Hardware Client](podklyuchenie-k-konsoli-upravleniya-robotom.md#rev-hardware-client), поскольку он позволит пользователю получить доступ к консоли Robot Controller Console через проводное соединение. Во втором разделе будет рассмотрен доступ к [консоли управления роботом через браузер](podklyuchenie-k-konsoli-upravleniya-robotom.md#web-browser).

## REV Hardware Client&#x20;

[Скачайте последнюю версию REV Hardware Client](../updating-and-managing/rev-hardware-client.md) и установите на ПК с Windows.&#x20;

| Шаги                                                                                                                                                                                    |                                                                                                                                                                                                                                                                                              |
| --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Включите Control Hub, подключив 12-вольтовую тонкую батарею ([REV-31-1302](https://www.revrobotics.com/rev-31-1302/))  к разъему XT30 с надписью "BATTERY" на концентраторе управления. | ![C:\Users\Rachel\AppData\Local\Microsoft\Windows\INetCache\Content.Word\g20714.png](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gHM0EmnJzRcHEz%2F48.png?generation=1590614867898772\&alt=media)     |
| Control Hubготов к подключению к ПК, когда индикатор загорится зеленым цветом. Примечание: индикатор мигает синим цветом каждые \~5 секунд, показывая, что Control Hub исправен.        | ![C:\Users\Rachel\AppData\Local\Microsoft\Windows\INetCache\Content.Word\rect22073.png](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2Fftc-control-system%2F-M8MwLCHioGUmBeHgdmq%2F-M8N18gICw6\_gms8beSs%2F49.png?generation=1590614867893475\&alt=media) |
| Подключите концентратор управления к ПК с помощью кабеля USB-A - USB-C ([REV-11-1232](https://www.revrobotics.com/rev-11-1232/))                                                        |                                                                                                                                                                                                                                                                                              |

Запустите клиент REV Hardware Client. После полного подключения Control Hub, он появится на первой странице пользовательского интерфейса на вкладке "Оборудование". Выберите Control Hub.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGiTkPM64QDvClOs1pw%2F-MGiVDNfFRESoYAwBz8s%2FResetAP%20-%20Start%20screen.svg?alt=media\&token=63f90329-95e7-4fc7-a0e9-652b5ff84168)

После выбора "Подключенное оборудование" ("Connected Hardware"), откроется вкладка "Обновления" ("Update"). Выберите вкладку "Программирование и управление" ("Program nad Manage"). Это приведет вас к консоли управления роботом, встроенной в REV Hardware Client.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGiTkPM64QDvClOs1pw%2F-MGiVq2dC15lP3XjXlZg%2FResetAP%20-%20%20home%20screen.svg?alt=media\&token=0e3569e0-edd5-4285-b580-1aa7e25bc850)

{% hint style="info" %}
На этом этапе целесообразно обновить [Операционную систему Control Hub](../updating-and-managing/updating-operating-system/), [приложение управления роботом](../updating-and-managing/updating-robot-controller-application.md), и [Прошивку самого hub](../updating-and-managing/updating-firmware/).&#x20;
{% endhint %}

После входа в консоль управления роботом, появится главная страница консоли. В правом верхнем углу находится навигационное меню, которое позволяет пользователям получить доступ к страницам Blocks, OnBot Java и Manage внутри консоли.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MGiTkPM64QDvClOs1pw%2F-MGiWtKw2qnPRcb0-SUj%2FResetAP%20-%20%20program%20and%20manage%201.svg?alt=media\&token=9f73a40b-196a-4db7-bb3d-56f98387ba09)

## Веб Браузер

Включив Control Hub, откройте селектор сетей Wi-Fi на ПК. Для устройств Windows 10 щелкните значок сети Wi-Fi в правом нижнем углу рабочего стола.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_aS-LR2ytGbAwcSOLU%2F-M\_b-AsOKjBNvaLfutRw%2FAccessing%20RCC%20-%20opening%20available%20networks.svg?alt=media\&token=fd0258a1-768d-4fd0-8a2d-7907126c2b25)

Ищите Wi-Fi, который соответствует протоколу именования устройства.

{% hint style="info" %}
Чтобы убедиться, что вы сможете определить местонахождение нужного устройства, рекомендуется сначала подключиться в месте, где нет других активных концентраторов управления или значительных соединений Wi-Fi.
{% endhint %}

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_aS-LR2ytGbAwcSOLU%2F-M\_b0S35\_75GS5oQxrjB%2FAccessing%20RCC%20-%20checking%20for%20WiFi%20networks.svg?alt=media\&token=c90d4022-29df-40f8-8441-c5e2b625aef6)

{% hint style="info" %}
В зависимости от версии Windows или других настроек темы список сетей Wi-Fi может иметь разный вид.
{% endhint %}

Найдя в списке нужную сеть, щелкните по ней, чтобы выбрать ее, а затем нажмите кнопку подключиться.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_aS-LR2ytGbAwcSOLU%2F-M\_b1LU2DCjFY1E31Cfe%2FAccessing%20RCC%20-%20selecting%20network.svg?alt=media\&token=a2b978fc-3780-42b4-a3f3-12767325cd64)

Введите пароль сети (в данном примере "password") и нажмите "Next" для продолжения.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_aS-LR2ytGbAwcSOLU%2F-M\_b1qEvHy1YdPruZwa1%2FAccessing%20RCC%20-%20logining%20in.svg?alt=media\&token=85ee902b-fe38-427e-80bc-91d73eebf0e7)

{% hint style="warning" %}
Пароли чувствительны к регистру. Убедитесь, что ваше написание и капитализация совпадают с оригинальным написанием и капитализацией пароля.
{% endhint %}

После установления беспроводного соединения статус отображается в настройках беспроводной связи устройства.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_aS-LR2ytGbAwcSOLU%2F-M\_b2SOCPhXMyAkVAaZo%2FAccessing%20RCC%20-%20secured.svg?alt=media\&token=fd3dc4b1-8758-4108-aedc-5acfa6da6426)

{% hint style="danger" %}
При подключении к концентратору управления подключенное устройство не будет иметь доступа к Интернету. Оно имеет только прямой доступ к концентратору управления.
{% endhint %}

Откройте веб-браузер (Chrome, Firefox, Internet Explorer) и перейдите по адресу "192.168.43.1:8080" через адресную строку.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_aS-LR2ytGbAwcSOLU%2F-M\_b2zPuip\_ollQIVXvu%2FAccessing%20RCC%20-%20accessing%20RCC.svg?alt=media\&token=e8a24da9-e916-4934-9ced-d9d750a9c302)

С консоли управления роботом пользователи могут[ обновить настройки Wi-Fi](obnovlenie-nastroek-wi-fi.md), обновить [операционную систему](../updating-and-managing/updating-operating-system/) и [прошивку](../updating-and-managing/updating-firmware/), а также [запрограммировать ](../programming/hello-robot-introduction-to-programming.md)устройство. Перед началом программирования настоятельно рекомендуется выполнить все описанные выше шаги.
