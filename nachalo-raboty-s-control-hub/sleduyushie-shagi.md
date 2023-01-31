# Следующие шаги

Возможность подключения к консоли контроллера робота, подключение Driver Station к Control Hub и основы подключения Control Hub к различным исполнительным механизмам и датчикам - это только начало. Этот раздел посвящен следующим шагам по использованию системы управления REV, включая начало программирования и лучшие практики управления концентратором управления и батареями Slim.

## Начало работы с программированием &#x20;

Теперь, когда концентратор управления настроен, можно приступать к программированию для управления роботом! В [руководстве по программированию Hello Robot](../programming/hello-robot-introduction-to-programming.md) описаны необходимые шаги для начала программирования. В руководстве есть рекомендации по выбору подходящего инструмента программирования, настройке робота и основам программирования.

Для того чтобы Control Hub мог правильно взаимодействовать с аппаратными компонентами, необходимо выполнить процесс, состоящий из двух частей, известный как сопоставление оборудования. Одним из наиболее важных и часто забываемых шагов при начале программирования является создание конфигурационного файла, который является первой частью процесса сопоставления оборудования. Правильно созданный файл конфигурации определяет каждый компонент оборудования уникальным именем, а также тип и номер порта. После подключения аппаратных компонентов к концентратору используйте приложение Driver Station для создания конфигурации, прежде чем приступать к программированию.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-M\_vq2eddt\_lpo7B4SoZ%2F-M\_w9VuqOatKGRtqwaGG%2Fconfiguring.svg?alt=media\&token=9974d9ca-2706-47ab-a3be-f909e3e09140)

{% hint style="info" %}
Для получения более подробной информации о важности аппаратного отображения и о том, как настроить вашего робота, пожалуйста, см. страницу [Hello Robot - Конфигурация](../programming/hello-robot-configuration.md).&#x20;
{% endhint %}

## Добавление к Expansion Hub

В зависимости от области применения может потребоваться больше портов для двигателей, датчиков или сервоприводов. Если вашему роботу требуется больше двигателей, может потребоваться добавление концентратора расширения. Добавление концентратора расширения добавляет в систему такое же количество аппаратных портов, как и один концентратор управления (дополнительные четыре порта двигателей, шесть портов сервоприводов и все порты датчиков).

{% hint style="info" %}
Для получения дополнительной информации о том, как добавить Expansion hub, посетите нашу страницу [Добавление Expansion Hub](../adding-more-motors/adding-an-expansion-hub.md).
{% endhint %}

## Управление Control Hub

Control Hub и Exnapnsion Hub являются устройствами с возможностью обновления в полевых условиях. При выпуске нового программного обеспечения с новыми функциями, исправлениями ошибок и изменениями в зависимости от сезона пользователи могут самостоятельно обновить устройство. Рекомендуется проверять наличие обновлений программного обеспечения в начале сентября и затем примерно каждые 6-8 недель. Для проверки обновлений программного обеспечения можно использовать [REV Hardware Client](../updating-and-managing/rev-hardware-client.md) или обратиться к разделу документации "Управление системой управления".

{% hint style="info" %}
Информацию об обновлении различных частей программного обеспечения для Control Hub, Expansion hub и Driver hub можно найти в разделе Управление системой управления.
{% endhint %}

## Slim Battery Best Practices

Для обслуживания и ухода за батареей ознакомьтесь с общими рекомендациями по эксплуатации батареи 12V Slim Battery ([REV-31-1302](https://www.revrobotics.com/rev-31-1302/)) страницу продукта или информацию, приведенную ниже. Сюда входит информация о том, как правильно хранить, заряжать и ухаживать за батареей в течение длительного времени.

Все аккумуляторные батареи имеют ограниченный срок службы. На срок службы влияют такие факторы, как количество циклов разряда/заряда и средняя нагрузка на батарею. Следующие передовые методы помогут максимально продлить срок службы батареи:

* Charge rate
  * Minimum: 1.5A
  * Maximum: 3.0A
  * Recommended: 1.8A or 2.0A
* Do not overcharge
  * Disconnect the battery from the charger once it indicates a full charge.
  * Typical charge time does not exceed 2 hours.
  * Do not charge a battery that hasn't been discharged significantly.
    * For example, running the robot under minimal load for a few minutes will not significantly discharge the battery.
* Minimum no-load voltage: 9.0V
  * Discharging the battery past 9.0V can reduce the lifespan of the battery and can permanently damage the cells.
  * Periodic dips below 9.0V when under load is expected and OK.
    * For example, don't forget to unplug your battery after you are finished running the robot and don't run your robot until it completely stops responding!
* Temperature
  * Let the battery cool before and after charging.
  * The battery may feel warm after heavy loading or after charging. This is normal.