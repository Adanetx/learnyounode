Реализуйте HTTP **сервер** который принимает только POST запросы и конвертирует все символы тела запроса в верхний регистр и возвращает их клиенту.

Ваш сервер должен слушать порт, который Вы получите в качестве первого аргумента командной строки.

----------------------------------------------------------------------
## ИНФОРМАЦИЯ

Пока Вы не ограничены в использовании потоковых возможностей объектов `request` и `response`, это будет намного легче, если Вы ими воспользуетесь.

Есть множество различных библиотек в npm, которые Вы можете использовать для *"преобразования"* потока данных. Библиотека `through2-map` предоставляет самое простое API для данной задачи.

`through2-map` позволяет создать *преобразованный поток*, используя только одну функцию, которая принимает фрагмент данных и возвращает фрагмент данных. Это работает практически так же как `Array#map()`, только с потоками:

```js
const map = require('through2-map')
inStream.pipe(map(function (chunk) {
  return chunk.toString().split('').reverse().join('')
})).pipe(outStream)
```

В примере выше, входящий поток данных из `inStream` конвертируется в строку (если еще не строка), символы переставляются в обратном порядке, и результат направляется в `outStream`. Таким образом мы сделали преобразователь фрагментов данных в обратном порядке. Помните о том, что размер фрагментов данных определяется вне потока и Вы мало что можете сделать с этим размером для входящих данных.

Для установки `through2-map` наберите:

```sh
$ npm install through2-map
```

Если у Вас отсутствует соединение с интернетом, просто создайте директорию `node_modules` и скопируйте туда директорию с библиотекой, которую Вы хотите использовать из {appname}:

  {rootdir:/node_modules/through2-map}

Документацию для through2-map Вы cможете получить, набрав в браузере:

  {rootdir:/docs/through2-map.html}
