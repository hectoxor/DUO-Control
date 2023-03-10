# Аналог

## Основы аналоговых датчиков

Аналоговые датчики могут сообщать о практически бесконечном количестве состояний, в отличие от цифровых датчиков, которые сообщают только о двух состояниях. При изменении состояния датчика изменяется и напряжение, передаваемое роботу. Вспомните выключатель, яркость света в комнате зависит от положения ползунка или ручки на шкале потенциальных положений. При регулировке ручки уровень напряжения изменяется пропорционально, и свет непрерывно меняется в соответствии с выходом ручки. &#x20;

{% hint style="success" %}
Можете ли вы вспомнить что-нибудь, что действует как аналоговые датчики в вашем доме? Вот некоторые, о которых мы подумали: весы, термометр, регулятор громкости.
{% endhint %}

В отличие от двоичного (низкий/высокий) статуса цифровых датчиков, аналоговые датчики учитывают все числа в определенном, заданном диапазоне. При использовании аналогового датчика действие триггера будет зависеть от датчика. Рассмотрим потенциометр, прикрепленный к руке; выходное напряжение (сигнал) будет соответствовать углу наклона руки. Зная угол наклона рычага, можно решить, где остановить рычаг на пути его движения.&#x20;

{% hint style="info" %}
Концентратор управления и концентратор расширения могут считывать напряжение в диапазоне от 0 до 5 В.&#x20;
{% endhint %}

REV Robotics предлагает аналоговый датчик, известный как потенциометр ([REV-31-1155](https://www.revrobotics.com/rev-31-1155/)). Потенциометр можно использовать для определения или измерения углового положения вала.

## Проводка&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MFpxo5ekLNYiSEamSF2%2F-MFpy4npwGIxk0gowHcE%2FControl\_Hub\_Port\_Specific\_Pinout\_ANALOG\_LARGER\_SIZE-01.png?alt=media\&token=d5036d25-9a34-4f78-bcc3-9935012cbf08)

Аналоговые датчики подключаются к концентратору управления ([REV-31-1595](https://www.revrobotics.com/rev-31-1595/)) или концентратору расширения ([REV-31-1153](https://www.revrobotics.com/rev-31-1153/)) через 4-контактный сенсорный кабель JST PH и аналоговые порты, показанные на рисунке выше. Цветовая маркировка аналоговых портов на изображении соответствует каждому проводу в JST PH 4-Pin Sensor Cable. По традиции, черный провод - это земля, а красный - питание. Синий (n) провод и белый (n+1) провод являются каналами связи (сигнала), по которым датчик посылает обратную связь на концентраторы.

Каждый аналоговый порт концентратора может работать как два отдельных порта благодаря двум каналам связи. Именно поэтому порты обозначены как 0-1 и 2-3. На рисунке выше показано, какой канал связи соответствует тому или иному порту. Канал n+1 работает с нечетными портами 1-3, а канал n - с четными портами 0-2.

Два аналоговых датчика могут быть размещены на одном физическом порту с помощью кабеля Sensor Splitter Cable ([REV-31-1386](https://www.revrobotics.com/rev-31-1386/)). При этом важно проверить схему выводов, включенную в технические описания каждого отдельного датчика, поскольку некоторые датчики, например, потенциометр REV, используют только один из каналов связи.

## Конфигурация

Прежде чем программировать датчик, его необходимо добавить в конфигурацию робота. Файл конфигурации сохраняет все сконфигурированные устройства в "hardwareMap" концентратора управления, к которому можно обратиться в коде для установления линии связи между устройствами.&#x20;

Приведенные ниже шаги показывают базовую конфигурацию для аналоговых устройств ****. В примере потенциометр будет настроен как "Аналоговый вход\`" на порт 0.&#x20;

#### Шаг 1

Находясь в конфигурации, выберите опцию **Устройства аналогового ввода**. Откроется окно, на котором будут показаны четыре аналоговых порта.

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MFlMDDJDqDR1Bl7viMZ%2F-MFlh44cHXFDjx95r83N%2FAnalog%20sensor%20config%20step%201.svg?alt=media\&token=aadb04f7-0f3f-4ff0-90c9-efd0456c0270)

#### Шаг 2

В выпадающем меню для порта 0 выберите "Аналоговый вход". После выбора дайте имя датчику. В данном примере потенциометр назван "potentiometer", но можно использовать любое название.&#x20;

![](https://2589213514-files.gitbook.io/\~/files/v0/b/gitbook-legacy-files/o/assets%2F-M4\_pJHI8HTuZFQTNfcy%2F-MFlMDDJDqDR1Bl7viMZ%2F-MFlj5YzRTH5KaHjq\_ar%2FAnalog%20sensor%20config%20step%202.svg?alt=media\&token=4473a795-c3cc-498a-bf87-34570d1cf804)

#### Step 3&#x20;

Когда вы закончите настройку датчика, нажмите **Done**. Приложение вернется к предыдущему экрану.

## Приложения

Как потенциометр помогает роботу ориентироваться в окружающем мире? Потенциометры чаще всего используются для измерения угла наклона сустава руки. Измерение угла может быть использовано для установки или поиска определенного положения вдоль шарнира руки.&#x20;

Для получения дополнительной информации о технических характеристиках датчика потенциометра REV, примерах кодирования и многом другом нажмите на одну из ссылок ниже, чтобы перейти к техническим описаниям датчиков.

| |
| :-----------

