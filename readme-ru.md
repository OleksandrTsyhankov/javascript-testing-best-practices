<img src="/assets/jtbp-header-blue.png" width="1920px"/>

<br/>

# 👇 Почему это руководство сможет поднять твои навыки на новый уровень

<br/>

## 45+ лучших практик: Всеобъемлющий и исчерпывающий

Это руководство по надежности JavaScript & Node.js, от А до Я. В нем собрано огромное количество лучших постов из блогов, книг и инструментов, которые только может предложить рынок.

## 🚢 Продвинутое: На 10,000 километров впереди простых основ

Присоединяйся к путешествию, которое уходит далеко за пределы основ и включает в себя такие продвинутые темы как тестирование на продакшене, мутационное тестирование, тестирование на основе свойств, а также много других инструментов для профессионалов. После внимательного прочтения этого руководства, твои знания наверняка будут намного выше среднего. 

## 🌐 Full-stack: front, backend, CI, что угодно

Начни с понимания повсеместных практик тестирования, которые лежат в основе приложений любого уровня. Затем углубись в область по своему выбору: frontend/UI, backend, CI или может быть всё вместе?

<br/>

### Автор: Yoni Goldberg

- Консультант по вопросам JavaScript & Node.js
- 📗 [Testing Node.js & JavaScript From A To Z](https://www.testjavascript.com) - Мой всеобъемлющий  онлайн курс с более чем [десятью часами видео](https://www.testjavascript.com), 14 видов тестирования и более 40 лучших практик
- [Подписывайтесь на мой Твиттер ](https://twitter.com/goldbergyoni/)

<br/>

### Переводы - читай на своем языке

- 🇨🇳[Китайский](readme-zh-CN.md) - Любезно предоставлен [Yves yao](https://github.com/yvesyao)
- 🇰🇷[Корейский](readme.kr.md) - Любезно предоставлен [Rain Byun](https://github.com/ragubyun)
- 🇵🇱[Польский](readme-pl.md) - Любезно предоставлен [Michal Biesiada](https://github.com/mbiesiad)
- 🇪🇸[Испанский](readme-es.md) - Любезно предоставлен [Miguel G. Sanguino](https://github.com/sanguino)
- 🇧🇷[Португальский-BR](readme-pt-br.md) - Любезно предоставлен [Iago Angelim Costa Cavalcante](https://github.com/iagocavalcante) , [Douglas Mariano Valero](https://github.com/DouglasMV) и [koooge](https://github.com/koooge)
- Хочешь перевести на свой родной язык? Пожалуйста, открой issue 💜

<br/><br/>

## `Содержание`

#### [`Часть 0: Золотое правило`](#часть-0️⃣-золотое-правило)

Один совет, который является основой для всех остальных (1 специальный пункт)

#### [`Часть 1: Анатомия тестов`](#часть-1-анатомия-тестов)

Основы - структура чистых тестов (12 пунктов)

#### [`Часть 2: Backend`](#часть-2️⃣-backend)

Эффективное написание тестов для бэкенда и микросервисов (8 пунктов)

#### [`Часть 3: Frontend`](#часть-3️⃣-frontend)

Напишем тесты для web UI, включая компонентное тестирование и E2E тестирование (11 пунктов)

#### [`Часть 4: Измеряем эффективность тестов`](#часть-4️⃣-измеряем-эффективность-тестов)

Проверяем проверяющего - измерим качество тестов (4 пункта)

#### [`Часть 5: Continuous Integration`](#часть-5️⃣-и-другие-измерения-качества)

Руководство для CI в мире JS (9 пунктов)

<br/><br/>

# Часть 0️⃣: Золотое правило

<br/>

## ⚪️ 0 Золотое правило: Разрабатывай гибкие тесты

:white_check_mark: **Делай:**
Код тестов отличается от кода для продакшена - создавай его предельно простым, коротким, свободным от абстракций - таким, чтобы с ним было приятно работать. Одного взгляда на тест должно быть достаточно, чтобы понять, что он делает.

Наш разум и так заполнен кодом для продакшена, у нас нет лишнего "места в голове" для дополнительных сложностей. Как только мы попытаемся запихать еще один блок сложного кода в наш бедный мозг, как это тут же замедлит всю команду - а ведь это противоречит тому, зачем мы вообще пишем тесты. Именно на этом моменте многие команды зачастую забрасывают тестирование. 

Тесты это кое-что другое - дружелюбный и улыбчивый помошник, с которым одно удовольствие работать и который к тому же окупает себя очень быстро. Наука говорит, что у нас есть две мозговые системы: система 1 используется для простых действий, таких как как вождение автомобиля по пустой дороге. Система 2 служит для решения сложных задач, например математических уравнений. Разрабатывай свои тесты для системы 1, чтобы при взгляде на код тестов _было_ _ощущение_, что это также просто, как отредактировать HTML документ, а нет как решить уравнение 2X(17 × 24).

Это достигается тщательным выбором техник, инструментов и целей для тестирования, которые стоят того и окупят себя в будущем. Тестируй только то, что нужно, находи баланс. Иногда даже лучше отбросить часть тестов для упрощения.

![alt text](/assets/headspace.png "У нас нет места для дополнительных сложностей")

Большинство советов, приведенных ниже являются производными этого принципа.

### Готов начать?

<br/><br/>

# Часть 1: Анатомия тестов

<br/>

## ⚪ ️ 1.1 Включай в название каждого теста 3 части

:white_check_mark: **Делай:** Отчет с результатами тестов должен содержать информацию, соответствует ли текущая версия приложения всем требованиям. Эта информация должна быть понятна даже тем, кто не знаком с кодом: тестировщик, DevOps, который занимается деплоем или ты сам, через два года. Этого можно достичь, если тест сам расскажет про требования и в его имени будут три части:

(1) Что было протестировано? Например, метод ProductsService.addNewProduct

(2) Сценарий и обстоятельства? Например, значение цены не передано в метод

(3) Ожидаемый результат? например, новый продукт не был добавлен

<br/>

❌ **Иначе:** Разработка встала, тест "Добавлен продукт" провален. Говорит ли вам это о том, где ошибка и что не работает?

<br/>

**👇 Заметка:** Каждый пункт содержит пример с кодом и иногда картинку для илюстрации примера. 
<br/>

<details><summary>✏ <b>Пример кода</b></summary>
  
<br/>
  
### :clap: Делай правильно Пример: Название теста состоит из трех частей

![](https://img.shields.io/badge/🔨%20Example%20using%20Mocha-blue.svg "Использование Mocha для илюстрации")

```javascript
//1. unit under test
describe('Products Service', function() {
  describe('Add new product', function() {
    //2. scenario and 3. expectation
    it('When no price is specified, then the product status is pending approval', ()=> {
      const newProduct = new ProductService().add(...);
      expect(newProduct.status).to.equal('pendingApproval');
    });
  });
});

```

<br/>

### :clap: Делай правильно Пример: Название теста состоит из трех частей

![alt text](/assets/bp-1-3-parts.jpeg "Название теста состоит из трех частей")

</details>

<br/>
<details><summary>© <b>Источники</b></summary>
  1. <a href='https://osherove.com/blog/2005/4/3/naming-standards-for-unit-tests.html'>Roy Osherove - Naming standards for unit tests</a>
</details>

<br/><br/>

## ⚪ ️ 1.2 Структурируй свои тесты так, чтобы они соответствовали AAA паттерну

:white_check_mark: **Делай:** Разбей свои тесты на три части - Подготовка, Действие и Проверка (ориг. Arrange, Act & Assert). Такая структура позволит читателю понять тест-план не напрягая извилин:

Подготовка(Arrange): Весь код для запуска теста. Сюда входит создание тестого юнита, добавление записей в базу данных, создание заглушек или моков и любой код для подготовки.

Действие(Act): Запуск в тестовой среде. Обычно одна строка кода.

Проверка(Assert): Убедиться что полученное значение соответствует ожиданию. Обычно одна строка кода.

<br/>

❌ **Иначе:** Вы не только тратите часы на понимание основного кода, но и то, что должно было быть самой простой частью дня (тестирование), напрягает ваш мозг.

<br/>

<details><summary>✏ <b>Пример кода</b></summary>

<br/>

### :clap: Делай правильно Пример: Тест структурирован согласно AAA паттерну

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Пример с  Jest") ![](https://img.shields.io/badge/🔧%20Example%20using%20Mocha-blue.svg "Пример с Mocha")

```javascript
describe("Customer classifier", () => {
  test("When customer spent more than 500$, should be classified as premium", () => {
    //Arrange
    const customerToClassify = { spent: 505, joined: new Date(), id: 1 };
    const DBStub = sinon.stub(dataAccess, "getCustomer").reply({ id: 1, classification: "regular" });

    //Act
    const receivedClassification = customerClassifier.classifyCustomer(customerToClassify);

    //Assert
    expect(receivedClassification).toMatch("premium");
  });
});
```

<br/>

### :thumbsdown: Анти-паттерн Пример: Нет разделения, один блок, сложнее разобрать

```javascript
test("Should be classified as premium", () => {
  const customerToClassify = { spent: 505, joined: new Date(), id: 1 };
  const DBStub = sinon.stub(dataAccess, "getCustomer").reply({ id: 1, classification: "regular" });
  const receivedClassification = customerClassifier.classifyCustomer(customerToClassify);
  expect(receivedClassification).toMatch("premium");
});
```

</details>

<br/><br/>

## ⚪ ️1.3 Опиши ожидания на языке продукта: используй утверждения в стиле BDD

:white_check_mark: **Делай:** Тесты написанные в декларативном стиле позволяют читающему понять что происходит, без нагрузки на свой мозговой процессор. Если твои тесты написаны в императивном стиле, наполнены условной логикой, то читатель вынужден нагружать свой мозг. Поэтому используй язык, похожий на человеческую речь, декларативный BDD стиль, использующий такие слова как 'expect' или 'should' и не используй дополнительный код. Если Chai & Jest не содержат необходимой проверки и она часто повторяется, лучше используй [расширение для Jest](https://jestjs.io/docs/en/expect#expectextendmatchers) или напиши [плагин для Chai](https://www.chaijs.com/guide/plugins/)

<br/>

❌ **Иначе:** Команда будет писать меньше тестов и пропускать надоедливые при помощи .skip()

<br/>

<details><summary>✏ <b>Пример кода</b></summary><br/>

![](https://img.shields.io/badge/🔧%20Example%20using%20Mocha-blue.svg "Примеры с Mocha & Chai") ![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Примеры с Jest")

### :thumbsdown: Анти-паттерн Пример: Читатель должен пройтись по всему немаленкому куску императивного кода, просто чтобы понять что это за тест

```javascript
test("When asking for an admin, ensure only ordered admins in results", () => {
  //assuming we've added here two admins "admin1", "admin2" and "user1"
  const allAdmins = getUsers({ adminOnly: true });

  let admin1Found,
    adming2Found = false;

  allAdmins.forEach(aSingleUser => {
    if (aSingleUser === "user1") {
      assert.notEqual(aSingleUser, "user1", "A user was found and not admin");
    }
    if (aSingleUser === "admin1") {
      admin1Found = true;
    }
    if (aSingleUser === "admin2") {
      admin2Found = true;
    }
  });

  if (!admin1Found || !admin2Found) {
    throw new Error("Not all admins were returned");
  }
});
```

<br/>

### :clap: Делай правильно Пример: Легко читаемый декларативный тест

```javascript
it("When asking for an admin, ensure only ordered admins in results", () => {
  //assuming we've added here two admins
  const allAdmins = getUsers({ adminOnly: true });

  expect(allAdmins)
    .to.include.ordered.members(["admin1", "admin2"])
    .but.not.include.ordered.members(["user1"]);
});
```

</details>

<br/><br/>

## ⚪ ️ 1.4 Придерживайся тестирования чёрного ящика (black-box testing): Пиши тесты только для публичных методов

:white_check_mark: **Делай:** Тестирование внутренних методов принесет больше проблем, чем пользы. Если твой код/API возвращает правильный результат, действительно ли тебе нужно потратить следующие три часа тестируя КАК он работает изнутри, а затем еще и поддерживать эти неустойчивые тесты? Всякий раз, когда проверяется публичная часть, неявно проверяется и приватная, и тесты провалятся, только если есть определенная проблема (например, неправильный вывод). Такой подход также назвают `поведенческое тестирование(behavioral testing)`. С другой стороны, если тестировать приватные методы(тестирование белого ящика) - твое внимание будет смещено с планирования выводных данных в сторону мелких внутренних деталей и твои тесты могут сломаться от любого рефакторинга, несмотря на то, что итоговый результат будет правильный - это резко увеличивает затраты на поддержку.
<br/>

❌ **Иначе:** Твои тесты ведут себя как [мальчик, который кричал волки](https://ru.wikipedia.org/wiki/%D0%9C%D0%B0%D0%BB%D1%8C%D1%87%D0%B8%D0%BA,_%D0%BA%D0%BE%D1%82%D0%BE%D1%80%D1%8B%D0%B9_%D0%BA%D1%80%D0%B8%D1%87%D0%B0%D0%BB:_%C2%AB%D0%92%D0%BE%D0%BB%D0%BA!%C2%BB): постоянно будут ложные срабатывания(например тест провален, потому что сменили имя приватной переменной). Неудивительно, что скоро все начнут игнорировать сообщения от CI, пока в один день не будет проигнорирован настоящий баг...

<br/>
<details><summary>✏ <b>Пример кода</b></summary>

<br/>

### :thumbsdown: Анти-паттерн Пример: Тестирование внутренних компонентов без особой причины

![](https://img.shields.io/badge/🔧%20Example%20using%20Mocha-blue.svg "Примеры с  Mocha & Chai")

```javascript
class ProductService {
  //this method is only used internally
  //Change this name will make the tests fail
  calculateVATAdd(priceWithoutVAT) {
    return { finalPrice: priceWithoutVAT * 1.2 };
    //Change the result format or key name above will make the tests fail
  }
  //public method
  getPrice(productId) {
    const desiredProduct = DB.getProduct(productId);
    finalPrice = this.calculateVATAdd(desiredProduct.price).finalPrice;
    return finalPrice;
  }
}

it("White-box test: When the internal methods get 0 vat, it return 0 response", async () => {
  //There's no requirement to allow users to calculate the VAT, only show the final price. Nevertheless we falsely insist here to test the class internals
  expect(new ProductService().calculateVATAdd(0).finalPrice).to.equal(0);
});
```

</details>

<br/><br/>

## ⚪️  1.5 Выбирай правильных дублеров: Старайся вместо моков использовать заглушки или шпионов(stubs or spies)

✅ **Делай:** Дублеры это необходимое зло, так как несмотря на то, что они связаны с внутренними частями, предоставляют огромную пользу.(<a href="https://martinfowler.com/articles/mocksArentStubs.html" data-href="https://martinfowler.com/articles/mocksArentStubs.html" class="markup--anchor markup--p-anchor" rel="noopener nofollow" target="_blank">[Здесь можно почитать про разницу между дублерами](https://martinfowler.com/articles/mocksArentStubs.html)</a>).

Прежде чем использовать дублера, задай простой вопрос: Я использую его для тестирования функциональности, которая есть или может появиться в требованиях? Если ответ - нет, то это начинает попахивать тестированием белого ящика.

Например, если ты хочешь протестировать как ведет себя приложение, когда отключается сервис оплаты, ты можешь поставить вместо него заглушку которая будет возвращать "Нет ответа", чтобы убедиться, что тестируемая часть вернет правильный результат. Так мы проверяем поведение/ответ/вывод нашего приложения при определенных сценариях. Ты также можешь использовать шпиона, чтобы проверить, что будет отправлено письмо, если сервис не отвечает - это снова проверка поведения, которая скорей всего есть в требованиях("Отправить сообщение, если платеж не получилось сохранить"). С другой стороны, если сделать мок платежного сервиса и убедиться что он вызывает правильные JavaScript типы - тогда твой тест будут построен вокруг внутренних вещей, которые не связаны с функциональностью приложения и скорей всего будут часто изменяться.
<br/>

❌ **Иначе:** Любой рефакторинг кода приведет к необходимости найти и обновить все участки с моками. Таким образом тесты становятся скорее обузой, чем полезным другом.
<br/>

<details><summary>✏️ <b>Пример кода</b></summary>

<br/>

### :thumbsdown: Анти-паттерн Пример: Мок сосредоточен на внутренних методах

![](https://img.shields.io/badge/🔧%20Example%20using%20Sinon-blue.svg "Примеры с Sinon")

```javascript
it("When a valid product is about to be deleted, ensure data access DAL was called once, with the right product and right config", async () => {
  //Assume we already added a product
  const dataAccessMock = sinon.mock(DAL);
  //hmmm BAD: testing the internals is actually our main goal here, not just a side-effect
  dataAccessMock
    .expects("deleteProduct")
    .once()
    .withArgs(DBConfig, theProductWeJustAdded, true, false);
  new ProductService().deletePrice(theProductWeJustAdded);
  dataAccessMock.verify();
});
```
<br/>

### 👏Делай правильно Пример: Шпион сделан для тестирования требований, но неизбежно затрагивает и внутренние методы

```javascript
it("When a valid product is about to be deleted, ensure an email is sent", async () => {
  //Assume we already added here a product
  const spy = sinon.spy(Emailer.prototype, "sendEmail");
  new ProductService().deletePrice(theProductWeJustAdded);
  //hmmm OK: we deal with internals? Yes, but as a side effect of testing the requirements (sending an email)
  expect(spy.calledOnce).to.be.true;
});
```
</details>

<br/><br/>

## 📗 Хочешь узнать про все практики из видео?

### Посети мой онлайн курс [Testing Node.js & JavaScript From A To Z](https://www.testjavascript.com)

<br/><br/>

## ⚪️ 1.6 Не используй "foo", используй реалистичные входные данные

✅ **Делай:** Часто баги, которые появляются на продакшне, связаны с каким то неожиданным вводом - чем более реалистичным будет тестовый ввод, тем больше шансов, что баги удасться поймать пораньше. Используй специальные библиотеки, такие как [Faker](https://www.npmjs.com/package/faker) для генерации псевдо-реалистичных данных, которые могут быть на продакшне. Например, такие библиотеки могут сгенерировать реалистичные номера телефонов, имена пользователей, данные кредитных карт, названия компаний и даже текст "lorem ipsum". Ты также можешь написать несколько тестов (поверх юнит тестов, а не как замену) которые будут рандомизировать тестовые данные, чтобы расширить свои тесты или даже использовать реальные данные с продакшна как тестовые. Хочешь улучшить такие тесты еще сильнее? Смотри следующий пункт(теститрование на основе свойств).

❌ **Иначе:** Все твои тесты во время разработки будут зелеными, с использованием твоих искусственных "Foo", но продакшн засветится красным, когда хакер использует какие-нибудь грязные трюки, типа строки "@3e2ddsf . ##’ 1 fdsfds . fds432 AAAA"

<br/>

<details><summary>✏️ <b>Пример кода</b></summary>

<br/>

### :thumbsdown: Анти-паттерн Пример: Тест проходит с нереалистичными данными

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Примеры с Jest")

```javascript
const addProduct = (name, price) => {
  const productNameRegexNoSpace = /^\S*$/; //no white-space allowed

  if (!productNameRegexNoSpace.test(name)) return false; //this path never reached due to dull input

  //some logic here
  return true;
};

test("Wrong: When adding new product with valid properties, get successful confirmation", async () => {
  //The string "Foo" which is used in all tests never triggers a false result
  const addProductResult = addProduct("Foo", 5);
  expect(addProductResult).toBe(true);
  //Positive-false: the operation succeeded because we never tried with long
  //product name including spaces
});
```
<br/>

### :clap: Делай правильно Пример: Случайный реалистичный ввод

```javascript
it("Better: When adding new valid product, get successful confirmation", async () => {
  const addProductResult = addProduct(faker.commerce.productName(), faker.random.number());
  //Generated random input: {'Sleek Cotton Computer',  85481}
  expect(addProductResult).to.be.true;
  //Test failed, the random input triggered some path we never planned for.
  //We discovered a bug early!
});
```

</details>

<br/><br/>

## ⚪ ️ 1.7 Тестируй большое количество комбинаций ввода используя тестирование на основе свойств(property-based testing)

:white_check_mark: **Делай:** Чаще всего мы используем немного вариантов входных данных для каждого теста. Даже когда мы используем данные, похожие на реальные (смотри пункт Не используй "foo"), мы берем лишь несколько комбинаций (method("", true, 1), method("string", false, 0)). Однако на продакшне, если наш API вызывается с пятью параметрами, это приводит к тысячам возможных вариантов, один из которых вполне может помешать работе приложения [Фаззинг](https://ru.wikipedia.org/wiki/%D0%A4%D0%B0%D0%B7%D0%B7%D0%B8%D0%BD%D0%B3)).Что если бы ты мог написать тест, который автоматически отправит 1000 вариаций разных входных данных и потом отловит те, которые приводят к ошибкам, чтобы вернуть правильный ответ? Тестирование на основе свойств это техника, которая делает именно это: отправляя все возможные комбинации входных данных в свой объект тестирования увеличивается вероятность обнаружить баг. Например, возьмем метод - addNewProduct(id, name, isDiscount) — и вызовем его с большим количеством вариаций (number, string, boolean) например (1, "iPhone", false), (2, "Galaxy", true). Ты можешь запускать тестирование на основе свойств используя свои любимые инструменты (Mocha, Jest и др.) с помощью библиотек типа [js-verify](https://github.com/jsverify/jsverify) или [testcheck](https://github.com/leebyron/testcheck-js) (документация получше). Обновление: Nicolas Dubien в комментариях предложил библиотеку [checkout fast-check](https://github.com/dubzzz/fast-check#readme), которая может предложить несколько дополнительных особенностей и активно поддерживается.
<br/>

❌ **Иначе:** Бессознательно ты выбираешь тестовые входные данные, которые охватывают только правильную работу кода. К сожалению, это снижает эффективность тестирования как средства выявления ошибок.

<br/>

<details><summary>✏ <b>Пример кода</b></summary>

<br/>

### :clap: Делай правильно Пример: Тестирование множества вводных вариантов используя "fast-check"

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Примеры с Jest")

```javascript
import fc from "fast-check";

describe("Product service", () => {
  describe("Adding new", () => {
    //this will run 100 times with different random properties
    it("Add new product with random yet valid properties, always successful", () =>
      fc.assert(
        fc.property(fc.integer(), fc.string(), (id, name) => {
          expect(addNewProduct(id, name).status).toEqual("approved");
        })
      ));
  });
});
```

</details>

<br/><br/>

## ⚪ ️ 1.8 Если необходимо, исполльзуй небольшие снимки(snapshots)

:white_check_mark: **Делай:** Когда необходимо [тестирование при помощи снимков](https://jestjs.io/docs/ru/snapshot-testing), используй небольшие снимки(3-7 строк кода), которые являются частью теста ([Inline Snapshot](https://jestjs.io/docs/ru/snapshot-testing#inline-snapshots)) и не связаны с внешними файлами. Таким образом твои тесты будут понятными и устойчивыми к изменениям.

С другой стороны руководства с "классическими снимками" и их инструменты рекомендуют создавать большие файлы( например разметку отрендеренного компонента или ответ API в формате JSON), хранить их отдельно  и потом при каждом запуске тестов сравнивать их с полученным результатом. Это может, например, неявно связать наши тесты с 1000 строками, содержащих 3000 значений, о которых тестировщик даже не знает. Почему же это неправильно? Таким образом мы получим 1000 причин для провала тестов - достаточно изменений одной строчки чтобы снимок стал неактуальным и это будет происходить часто. Как часто? Каждый пробел,комментарий или незначительное изменение CSS/HTML. Также название теста не содержит и намека о причинах провала, так как оно просто сообщает, что 1000 строк не изменились и вынуждает тестировщика принять длинный документ, который он не может проверить. Всё это симптомы неясного теста,который нацелен на проверку слишком большого количества вещей.

Есть лишь несколько вариантов, когда лучше использовать большие снимки - когда мы проверяем схему без данных(убираем все значения и концентрируемся на полях) или когда документ редко изменяется.

❌ **Иначе:** UI тесты провалятся. С кодом все в порядке, на экране идеальная картинка, что же случилось? Твои тесты при помощи снимков обнаружили разницу между текущим вариантом документа и исходным - одинокий пробел, добавленный в файле markdown...

<br/>

<details><summary>✏ <b>Пример кода</b></summary>

<br/>

### :thumbsdown: Анти-паттерн Пример: Привязываем к тесту 2000 скрытых строк кода

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Примеры с Jest")

```javascript
it("TestJavaScript.com is renderd correctly", () => {
  //Arrange

  //Act
  const receivedPage = renderer
    .create(<DisplayPage page="http://www.testjavascript.com"> Test JavaScript </DisplayPage>)
    .toJSON();

  //Assert
  expect(receivedPage).toMatchSnapshot();
  //We now implicitly maintain a 2000 lines long document
  //every additional line break or comment - will break this test
});
```

<br/>

### :clap: Делай правильно Пример: Ожидания можно увидеть

```javascript
it("When visiting TestJavaScript.com home page, a menu is displayed", () => {
  //Arrange

  //Act
  const receivedPage = renderer
    .create(<DisplayPage page="http://www.testjavascript.com"> Test JavaScript </DisplayPage>)
    .toJSON();

  //Assert

  const menu = receivedPage.content.menu;
  expect(menu).toMatchInlineSnapshot(`
<ul>
<li>Home</li>
<li> About </li>
<li> Contact </li>
</ul>
`);
});
```

</details>

<br/><br/>

## ⚪ ️1.9 Избегай глобальных тестовых конструкций, добавляй данные к каждому тесту отдельно

:white_check_mark: **Делай:** Следуя золотому правилу (Часть 0), каждый тест должен добавлять и работать со своим набором строк в БД, чтобы избежать неявных связей и сохранить понятную последовательность действий. В реальности,  многи тестировщики нарушат это правило, заполняя БД данными перед запуском тестов ([создавая "тестовое устройство"](https://en.wikipedia.org/wiki/Test_fixture)) для улучшения производительности. И хотя производительность это важный показатель - и его можно улучшать(смотри пункт Компонентное тестирование), однако, сложность тестов это тот показатель, который может вызывать головную боль большую часть времени. На практике, в тестах явно создавай записи в БД и работай только с ними. Если производительность становится проблемой - можно найти компромис, сделав общими неизменяемые данные для тестов (напимер, запросы).
<br/>

❌ **Иначе:** Несколько тестов провалено, разработка встала, наша команда потратит драгоценные часы на поиск, но есть ли баг? Давайте выясним, ой, нет - похоже два теста меняли одни и те же тестовые данные

<br/>

<details><summary>✏ <b>Пример кода</b></summary>

<br/>

### :thumbsdown: Анти-паттерн Пример: Тесты не независимы и полагаютмя на глобальный хук для заполнения глобальной БД

![](https://img.shields.io/badge/🔧%20Example%20using%20Mocha-blue.svg "Примеры с Mocha")

```javascript
before(async () => {
  //adding sites and admins data to our DB. Where is the data? outside. At some external json or migration framework
  await DB.AddSeedDataFromJson('seed.json');
});
it("When updating site name, get successful confirmation", async () => {
  //I know that site name "portal" exists - I saw it in the seed files
  const siteToUpdate = await SiteService.getSiteByName("Portal");
  const updateNameResult = await SiteService.changeName(siteToUpdate, "newName");
  expect(updateNameResult).to.be(true);
});
it("When querying by site name, get the right site", async () => {
  //I know that site name "portal" exists - I saw it in the seed files
  const siteToCheck = await SiteService.getSiteByName("Portal");
  expect(siteToCheck.name).to.be.equal("Portal"); //Failure! The previous test change the name :[
});

```

<br/>

### :clap: Делай правильно Пример: Мы можем оставаться внутри тестов, каждый тест работает со своим набором данных

```javascript
it("When updating site name, get successful confirmation", async () => {
  //test is adding a fresh new records and acting on the records only
  const siteUnderTest = await SiteService.addSite({
    name: "siteForUpdateTest"
  });

  const updateNameResult = await SiteService.changeName(siteUnderTest, "newName");

  expect(updateNameResult).to.be(true);
});
```

</details>

<br/>

## ⚪ ️ 1.10 Не отлавливай ошибки, ожидай их

:white_check_mark: **Делай:** Когда пытаешься проверить, что некоторые входные данные вызывают ошибку, может показаться хорошей идеей использовать try-catch-finally и работать с блоком catch. В результате получается неудобный тест (пример ниже), который скрывает назначение теста и ожидаемые результаты.

Лучшим решением будет использование функции expect(method).to.throw в Chai (или expect(method).toThrow() в Jest). Также обязательно убедиться, что исключение сможет определить тип ошибки, а иначе приложение не сможет ее правильно обработать и лишь покажет разочаровывающее сообщение пользователю.
<br/>

❌ **Иначе:** 
Будет сложно сделать вывод из итогов тестирования (например, CI), что пошло не так.

<br/>

<details><summary>✏ <b>Пример кода</b></summary>

<br/>

### :thumbsdown: Анти-паттерн Пример: Длинный тест, который пытается подтвердить наличие ошибки с помощью try-catch

![](https://img.shields.io/badge/🔧%20Example%20using%20Mocha-blue.svg "Примеры с Mocha")

```javascript
it("When no product name, it throws error 400", async () => {
  let errorWeExceptFor = null;
  try {
    const result = await addNewProduct({});
  } catch (error) {
    expect(error.code).to.equal("InvalidInput");
    errorWeExceptFor = error;
  }
  expect(errorWeExceptFor).not.to.be.null;
  //if this assertion fails, the tests results/reports will only show
  //that some value is null, there won't be a word about a missing Exception
});
```

<br/>

### :clap: Делай правильно Пример: Читаемое ожидание, которое легко понять даже QA или проект-менеджеру
```javascript
it("When no product name, it throws error 400", async () => {
  await expect(addNewProduct({}))
    .to.eventually.throw(AppError)
    .with.property("code", "InvalidInput");
});
```

</details>

<br/><br/>

## ⚪ ️ 1.11 Помечай свои тесты

:white_check_mark: **Делай:** Разные тесты должны производиться по разным сценариям: Different tests must run on different scenarios: дымовое, без ввода-вывода, тесты по коммиту разработчика, e2e тесты, которые обычно запускаются после успешного пул-реквеста и т.д. Этого можно достичь, если отмечать тесты при помощи ключевых слов, типа #cold #api #sanity, чтобы при помощи команды grep можно было запустить только опреденные тесты. Например вот так это делается в Mocha: mocha — grep ‘sanity’
<br/>

❌ **Иначе:** Если запускать все тесты, включая те, что выполняют сотни запросов в БД на каждое мелкое изменение, сделанное разработчиком, то они будут работать крайне медленно и вынуждать разработчика запускать их как можно реже.

<br/>

<details><summary>✏ <b>Пример кода</b></summary>

<br/>

### :clap: Делай правильно Пример: Метка "#cold-test" позволяет запускать только быстрые тесты(Cold === quick это тесты, которые не производят операций ввода-вывода и могут выполняться часто, даже когда разработчик печатает)

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Примеры с Jest")

```javascript
//this test is fast (no DB) and we're tagging it correspondigly
//now the user/CI can run it frequently
describe("Order service", function() {
  describe("Add new order #cold-test #sanity", function() {
    test("Scenario - no currency was supplied. Expectation - Use the default currency #sanity", function() {
      //code logic here
    });
  });
});
```

</details>

<br/><br/>

## ⚪ ️ 1.12 Разделяй тесты хотя бы на два под-уровня

:white_check_mark: **Делай:** Создай такую структуру к своим тестам, чтобы случайный посетитель мог легко понять требования (тесты - лучшая документация) и различные сценарии, которые тестируются. Чаще всего это размещать тест в двух блоках 'describe': первый блок это имя тестируемого объекта, а второй это дополнительный уровень для добавления категорий, например сценарий или своя категория (посмотри примеры кода внизу). Эти действия также улучшат тестовые отчеты: читающий сразу определит категорию, углубится в соответствующую секцию и определит проваленные тесты. Кроме того, разработчику станет намного проще ориентироваться в наборах с  множеством тестов. Есть много разных структур для тестовых наборов, например [given-when-then](https://github.com/searls/jasmine-given) или [RITE](https://github.com/ericelliott/riteway)

<br/>

❌ **Иначе:** При просмотре отчета с плоским и длинным списком тестов читатель должен бегло прочитать длинные тексты, чтобы завершить основные сценарии и определить связи провалившихся тестов. Рассмотрим следующий случай: когда тесты 7/100 проваливаются, просмотр плоского списка потребует чтения текста этих тестов, чтобы увидеть, как они соотносятся друг с другом. Однако в иерархическом отчете все они могут относиться к одному потоку или категории, и читатель быстро поймет, что или, по крайней мере, где является первопричиной отказа.

<br/>

<details><summary>✏ <b>Пример кода</b></summary>

<br/>

### :clap: Делай правильно Пример: Структура набора тестов, состоящая из имени тестируемого объекта и сценария приведет к удобному отчету, что и показано ниже

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Примеры с Jest")

```javascript
// Unit under test
describe("Transfer service", () => {
  //Scenario
  describe("When no credit", () => {
    //Expectation
    test("Then the response status should decline", () => {});

    //Expectation
    test("Then it should send email to admin", () => {});
  });
});
```

![alt text](assets/hierarchical-report.png)

<br/>

### :thumbsdown: Анти-паттерн Пример: Плоский список тестов приведет к трудностям у читателя с определением связи действий и проваленных тестов

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Примеры с Mocha")

```javascript
test("Then the response status should decline", () => {});

test("Then it should send email", () => {});

test("Then there should not be a new transfer record", () => {});
```

![alt text](assets/flat-report.png)

<br/>

</details>

<br/><br/>

## ⚪ ️1.13 Другие хорошие практики тестирования

:white_check_mark: **Делай:** Этот пост посвящен советам по тестированию, которые связаны с Node JS или, по крайней мере, могут быть проиллюстрированы им. Однако в этом разделе собраны несколько хорошо известных советов, не связанных с Node.

Изучи и практикуй [принципы TDD](https://www.sm-cloud.com/book-review-test-driven-development-by-example-a-tldr/) - они чрезвычайно ценны для многих, но не пугайся, если они не подходят твоему стилю, ты не одинок. Попробуй писать код в [стиле red-green-refactor](https://blog.cleancoder.com/uncle-bob/2014/12/17/TheCyclesOfTDD.html), убедись что каждый тест проверяет только одну вещь, когда найдешь баг - перед исправлением напиши тест, который обнаружит этот баг в будущем, пусть каждый тест провалится хотя бы раз, перед тем как стать зеленым, начни написание модуля с простого кода, который пройдет тест - затем отрефакторь его до уровня продакшн кода, избегай зависимостей от окружения(пути, ОС и т.д.)
<br/>

❌ **Иначе:** Ты упустишь мудрость, что накапливали десятилетиями

<br/><br/>

# Часть 2️⃣: Backend

## ⚪ ️2.1 Расширь свои методики тестирования: посмотри что еще есть кроме юнит тестов и пирамиды

:white_check_mark: **Делай:** [Пирамида тестирования](https://martinfowler.com/bliki/TestPyramid.html) за более чем десять лет, показала себя отличной моделью, которая предлагает три типа тестирования и которая повлияла на способ написания тестов большинства разработчиков. The В то же время много других техник не могут засиять в полную силу, так как они скрыты в тени этой пирамиды. Учитывая всё, что появилось за последние десять лет(микросервисы, облачные технологии, serverless архитектура), неужели одной достаточно строй модели достаточно чтобы покрыть *все* виды приложений? Не следует ли принять в мир тестирования новые техники?

Не поймите меня неправильно, в 2019 году пирамида тестирования, TDD и юнит тесты все еще отличные техники и наверно лучший вариант для многих приложений. Только вот, несмотря на всю их пользу, [иногда они тоже неправильны](https://en.wikipedia.org/wiki/All_models_are_wrong).Возьмем например приложение из мира IoT, которое загружает большое количество событий в броккер сообщений типа  Kafka/RabbitMQ, затем попадют в какое-нибудь хранилище данных, откуда запрашиваются для вывода в пользовательском интерфейсе для аналитики. Мы действительно должны потратить 50% бюджета наших тестов, чтобы написать юнит тесты для приложения, которое ориентировано на интеграцию и почти не имеет логики? И чем больше приложений разных типов будет появляться(боты, криптовалюта, голосовые помошники типа Alexa), тем больше шансов получить сценарий, когда тестировочная пирамида уже не будет лучшим вариантом.

Пришло время расширить свой инструментарий и познакомится с новыми типами тестирования(следующий пункт как раз об этом), с моделями похожими на пирамиду, но включающие в себя тесты для проблем из рельного мира(Хэй, наше API поломалось, давайте напишем тесты контрактов, основаных на потребителях(consumer-driven contract)!), разделить свои тесты как инвестор, который собирает портфель на основе анализа рисков - оценивая, где могут возникнуть проблемы и принимая меры для снижения потенциальных рисков.

Небольшое предупреждение: Отношение к TDD в мире разработки типично-двойственное, одни проповедуют использовать его повсюду, другие видят в нем Дьявола. Ошибаются те, кто возводят все в абсолют :] 

<br/>

❌ **Иначе:** Ты упустишь множество инструментов и техник вроде фаззинга, линтеров или мутационного тестирования, которые могут принести пользу за 10 минут.

<br/>

<details><summary>✏ <b>Пример кода</b></summary>

<br/>

### :clap: Делай правильно Пример: Cindy Sridharan предлагает богатый выбор для тестирования в ее потрясном посте 'Testing Microservices — the same way'

![alt text](assets/bp-12-rich-testing.jpeg "Cindy Sridharan предлагает богатый выбор для тестирования в ее потрясном посте 'Testing Microservices — the same way'")

<strong class="markup--strong markup--p-strong">Пример: </strong><a href="https://www.youtube.com/watch?v=-2zP494wdUY&amp;feature=youtube" data-href="https://www.youtube.com/watch?v=-2zP494wdUY&amp;feature=youtu.be" class="markup--anchor markup--p-anchor" rel="nofollow noopener" target="_blank">[YouTube: “Beyond Unit Tests: 5 Shiny Node.JS Test Types (2018)” (Yoni Goldberg)](https://www.youtube.com/watch?v=-2zP494wdUY&feature=youtu.be)</a>

<br/>

![alt text](assets/bp-12-Yoni-Goldberg-Testing.jpeg "Имя теста состоит из трех частей")

</details>

<br/><br/>

## ⚪ ️2.2 Компонентное тестирование может быть твоим лучшим занятием 

:white_check_mark: **Делай:** Каждый юнит тест покрывает лишь малую часть приложения и очень дорого покрыть ими всё, а e2e тестирование легко покрывает большие части, но оно многослойное и медленное. Так почему бы выбрать сбалансированный подход и написать тесты, которые больше юнитов, но меньше e2e? Компонентное тестирование это невоспетая песня мира тестов - оно обеспечивает лучшее с двух миров: адекватную производительность и возможность применять паттерны TDD + отличное реалистичное покрытие.

Компонентное тестирование сосредоточено на микросервисном "юните", такие тесты работают вместо API, не используют моки для вещей, которые используются внутри микросервиса(например реальные записи БД или хотя бы их копии из памяти), но создают заглушких для всех внешних вызовов. Таким образом мы тестируем то, что будет размещено, сближаем внутреннюю и внешнюю часть приложения и получаем увернность в результатах за разумные сроки.
<br/>

❌ **Иначе:** Ты будешь писать юнит тесты в течении многих дней, чтобы потом выяснить, что у тебя есть только 20% покрытия

<br/>

<details><summary>✏ <b>Пример кода</b></summary>

<br/>

### :clap: Делай правильно Пример: Supertest  позволяет приблизиться к Express API в процессе (быстрый и покрывает много слоев)

![](https://img.shields.io/badge/🔧%20Example%20using%20Mocha-blue.svg "Примеры с Mocha")

![alt text](assets/bp-13-component-test-yoni-goldberg.png "[Supertest](https://www.npmjs.com/package/supertest) позволяет приблизиться к Express API в процессе (быстрый и покрывает много слоев)")

</details>

<br/><br/>

## ⚪️ 2.3 Убедись, что новые релизы не поломают API - используй контрактное тестирование

✅ **Делай:** Значит у твоих микросервисисов много клиентов и у тебя есть разные версии для поддержания совместимости(чтобы все были счастливы). И вот, ты меняешь какое-нибудь поле и "бум", важный клиент, который использовал это поле теперь зол. Это Уловка-22 из мира интеграций: Очень сложно со стороны сервера учесть все ожидания клиентов, а с другой стороны на клиенте нельзя проводить тестирование, так как сервер контролирует даты релизов. [Контракты, ориентированные на потребителя(consumer-driven contracts) и фреймворк PACT](https://docs.pact.io/) былы созданы для формализации этого процесса с неожиданным подходом - не сервер определяет для себя план тестирования, а клиент определяет тесты для... сервера! PACT может записывать ожидания клиента и помещать их а отдельную область - "брокера", чтобы сервер мог взять эти ожидания, запустить каждую сборку с библиотеками PACT и увидеть, какие из контрактов сломались - не соответствуют ожиданиям клиента. В результате все несоответствия между клиент-серверным API будут отловлены заранее в процессе сборки/CI, что избавляет от лишней головной боли.
<br/>

❌ **Иначе:** Альтернативы - утомительное ручное тестирование или страх перед деплоем
<br/>

<details><summary>✏️ <b>Пример кода</b></summary>

<br/>

### 👏 Делай правильно Пример:

![](https://img.shields.io/badge/🔧%20Example%20using%20PACT-blue.svg "Примеры с PACT")

![alt text](assets/bp-14-testing-best-practices-contract-flow.png)

</details>

<br/><br/>

## ⚪️  2.4 Тестируй middleware отдельно

✅ **Делай:** Многие не тестируют middleware, потому что они представляют лишь малую часть системы и требуют работающего Express сервера. Обе причины неправильные - middlewares небольшие, но через них проходят почти все запросы и их легко тестировать как чистые функции, передавая объект {req, res}. Для тестирования нужно просто вызвать такую функцию, проследить ([используя например Sinon](https://www.npmjs.com/package/sinon) за взаимодействием с {req, res} и убедиться, что она выполняет правильные действия.  Библиотека [node-mock-http](https://www.npmjs.com/package/node-mocks-http) идет еще дальше и учитывает объекты {req, res}, а также отслеживает их поведение. Например, она может сравнить статус http у объекта res с ожидаемым (пример ниже)

<br/>

❌ **Иначе:** Баг в Express middleware === баг во всех или почти во всех запросах

<br/>

<details><summary>✏️ <b>Пример кода</b></summary>

<br/>

### 👏Делай правильно Пример: Тестирование middleware изолированно, не используя сетевых вызовов или запуска всей машины с Express

![](https://img.shields.io/badge/🔧%20Example%20using%20Jest-blue.svg "Примеры с Jest")

```javascript
//the middleware we want to test
const unitUnderTest = require("./middleware");
const httpMocks = require("node-mocks-http");
//Jest syntax, equivelant to describe() & it() in Mocha
test("A request without authentication header, should return http status 403", () => {
  const request = httpMocks.createRequest({
    method: "GET",
    url: "/user/42",
    headers: {
      authentication: ""
    }
  });
  const response = httpMocks.createResponse();
  unitUnderTest(request, response);
  expect(response.statusCode).toBe(403);
});
```

</details>

<br/><br/>

## ⚪️ 2.5 Проверяй и проводи рефакторинг, используя статические анализаторы кода 

✅ **Делай:** Использование статических анализаторов позволяет обнаружить способы улучшить качество кода и сохранить его поддерживаемым. Ты можешь добавить такой инструмент к сборке CI, чтобы сборка останавливалась, если анализатор обнаружит "плохой" код. Основные преимущества таких анализаторов над линтерами в том, что они могут проверять качество в контексте нескольких файлов(например для обнаружения дублирования), выполнять продвинутый анализ(например сложности кода) и следить за историей и изменениями в пробемном коде. Два примера таких инструментов это [SonarQube](https://www.sonarqube.org/) (4,900+ [звёзд](https://github.com/SonarSource/sonarqube)) и [Code Climate](https://codeclimate.com/) (2,000+ [звёзд](https://github.com/codeclimate/codeclimate))

Автор: <a href="https://github.com/TheHollidayInn" data-href="https://github.com/TheHollidayInn" class="markup--anchor markup--p-anchor" rel="noopener nofollow" target="_blank">[Keith Holliday](https://github.com/TheHollidayInn)</a>

<br/>

❌ **Иначе:** При низком качестве кода, баги и производительность всегда будут проблемой, и никакие новые блестящие библиотеки или современные функции этого не исправит.

<br/>

<details><summary>✏️ <b>Пример кода</b></summary>

<br/>

### 👏  Делай правильно Пример: CodeClimate, коммерческий инструмент, который может опрелять сложные методы: 

![](https://img.shields.io/badge/🔧%20Example%20using%20Code%20Climate-blue.svg "Пример с CodeClimate")

![alt text](assets/bp-16-yoni-goldberg-quality.png "CodeClimate, коммерческий инструмент, который может опрелять сложные методы:")

</details>

<br/><br/>

## ⚪️  2.6 Проверь свою готовность к хаосу Node.js

✅ **Делай:** Как ни странно, большинство тестов для программ проверяют логику и данные, но худшие вещи, которые могут произойти (и который очень сложно воссоздать) это проблемы с инфраструктурой. Например, ты когда нибудь тестировал поведение, когда память процесса переполняется, или процесс/сервер отключается, или мониторинг определяет, что API стал работать на 50% медленее? Чтобы проверить и эмулировать такие нехорошие вещи появился продукт Netflix - [Chaos engineering](https://principlesofchaos.org/). В него входят инструменты для тестирования устойчивости нашего приложения к хаотичным проблемам. Например, один из его самых извесных инструментов - [the chaos monkey](https://github.com/Netflix/chaosmonkey) в случайном порядке отключает сервера, чтобы убедиться, что приложение все еще способно работать и не полагается на работу лишь одного сервера, (также есть Kubernetes версия, [kube-monkey](https://github.com/asobti/kube-monkey), она отключает поды). Все эти инструменты работают на уровне хостинга/платформы, но что если ты хочешь протестировать созданный чистый Node хаос, например проверить, как твой Node процесс ведет себя при поялении необрабатываемых ошибок или promise rejection, переполнении памяти V8 с максимально разрешенными 1.7Гб или как UX поведет себя, когда event loop будет часто блокироваться? Для ответов на эти вопросы есть библиотека [node-chaos](https://github.com/i0natan/node-chaos-monkey), которая позволяет создать любой Node хаос.
<br/>

❌ **Иначе:** Выхода нет, закон Мерфи безжалостно сработает в продакшне 

<br/>

<details><summary>✏️ <b>Пример кода</b></summary>

<br/>

### 👏 Делай правильно Пример: Node-chaos может создать все виды Node.js неожиданностей, так что ты сможешь проверить устойчивость своего приложения к хаосу 

![alt text](assets/bp-17-yoni-goldberg-chaos-monkey-nodejs.png "Node-chaos может создать все виды Node.js неожиданностей, так что ты сможешь проверить устойчивость своего приложения к хаосу")

</details>

<br/>

#  Часть3️⃣: Frontend

## ⚪ ️ 3.1 Разделяй UI и функциональность

:white_check_mark: **Делай:** Когда надо сконцентрироваться на логике, UI становится шумом, который нужно убрать, чтобы тесты работали с чистыми данными. На практике, извлеки данные из разметки, чтобы осталось поменьше графической части, проверяй соответсвие только чистых данных(без HTML/CSS) и убирай замедляющие процесс анимации. Может возникнуть желание избежать рендеринга и протестировать только то, что находится за UI(сервисы, actions, store), но это приведет лишь к тому, что получаться тесты, которые не соответствуют реальности и не выявят случаев, когда данные даже не достигают UI.

<br/>

❌ **Иначе:** Результаты тестов с чистыми данными могут быть получены за 10мс, но затем весь тест пройдет только за 500мс (100 тестов = 1 минута), и все из-за какой-то необычной и не относящейся к проверке анимации

<br/>

<details><summary>✏ <b>Пример кода</b></summary>

<br/>

### :clap: Делай правильно Пример: Разделение данных от UI

![](https://img.shields.io/badge/🔧%20Example%20using%20React-blue.svg "Примеры с React") ![](https://img.shields.io/badge/🔧%20Example%20using%20React%20Testing%20Library-blue.svg "Примеры с react-testing-library")

```javascript
test("When users-list is flagged to show only VIP, should display only VIP members", () => {
  // Arrange
  const allUsers = [{ id: 1, name: "Yoni Goldberg", vip: false }, { id: 2, name: "John Doe", vip: true }];

  // Act
  const { getAllByTestId } = render(<UsersList users={allUsers} showOnlyVIP={true} />);

  // Assert - Extract the data from the UI first
  const allRenderedUsers = getAllByTestId("user").map(uiElement => uiElement.textContent);
  const allRealVIPUsers = allUsers.filter(user => user.vip).map(user => user.name);
  expect(allRenderedUsers).toEqual(allRealVIPUsers); //compare data with data, no UI here
});
```

<br/>

### :thumbsdown: Анти-паттерн Пример: Сравнение данных, смешанных с UI 

```javascript
test("When flagging to show only VIP, should display only VIP members", () => {
  // Arrange
  const allUsers = [{ id: 1, name: "Yoni Goldberg", vip: false }, { id: 2, name: "John Doe", vip: true }];

  // Act
  const { getAllByTestId } = render(<UsersList users={allUsers} showOnlyVIP={true} />);

  // Assert - Mix UI & data in assertion
  expect(getAllByTestId("user")).toEqual('[<li data-testid="user">John Doe</li>]');
});
```

</details>

<br/><br/>

## ⚪ ️ 3.2 Ищи элементы HTML по атрибутам, которые вряд ли изменятся

:white_check_mark: **Делай:** Ищи HTML элементы по атрибутам, которые переживут графические изменения, а не по селекторам CSS или лейблам форм. Если у элемента таких атрибутов нет, то добавь свой, тестовый атрибут, например "test-id-submit-button". Так ты не только будешь уверен, что твои тесты логики/функциональности никогда не сломаются из-за смены внешнего вида, это также даст всей команде понять что этот атрибут у элемента нужен для тестирования и его не нужно удалять 

<br/>

❌ **Иначе:** Ты хочешь протестировать процесс логина в систему, который охватывает множество компонентов, логики и сервисов, все настроено идеально - заглушки, шпионы, изолированные Ajax запросы. Все выглядит идеально. А затем тесты проваливаются, потому что дизайнер сменил CSS класс у div элемента с "thick-border" на "thin-border" 

<br/>

<details><summary>✏ <b>Пример кода</b></summary>

<br/>

### :clap: Делай правильно Пример: Поиск элемента, используя выделенный атрибут для тестирования

![](https://img.shields.io/badge/🔧%20Example%20using%20React-blue.svg "Примеры с React")

```html
// the markup code (part of React component)
<h3>
  <Badge pill className="fixed_badge" variant="dark">
    <span data-testid="errorsLabel">{value}</span>
    <!-- note the attribute data-testid -->
  </Badge>
</h3>
```

```javascript
// this example is using react-testing-library
test("Whenever no data is passed to metric, show 0 as default", () => {
  // Arrange
  const metricValue = undefined;

  // Act
  const { getByTestId } = render(<dashboardMetric value={undefined} />);

  expect(getByTestId("errorsLabel").text()).toBe("0");
});
```

<br/>

### :thumbsdown: Анти-паттерн Пример: Полагаться на CSS атрибуты

```html
<!-- the markup code (part of React component) -->
<span id="metric" className="d-flex-column">{value}</span>
<!-- what if the designer changes the classs? -->
```

```javascript
// this exammple is using enzyme
test("Whenever no data is passed, error metric shows zero", () => {
  // ...

  expect(wrapper.find("[className='d-flex-column']").text()).toBe("0");
});
```

</details>

<br/>

## ⚪ ️ 3.3 Если это возможно,тестируй реальный и полностью отрендеренный компонент

:white_check_mark: **Делай:** Везде, где это позволяет размер компонентов, тестируй их в таком виде, в каком их увидит пользователь - полностью отрендери UI, произведи нужные действия и убедись, что полученный UI ведет себя согласно ожиданиям. Старайся избегать моков или частичного рендеринга - эти техники могут привести к неотлавливаемым багам из-за нехватки деталей и итакие тесты станет тяжело поддерживать, так как они начинают работать с внутренними методами(смотри пункт "Придерживайся тестирования чёрного ящика"). Если один из дочерних элементов сильно замедляет процесс(например из-за анимации) или усложняет настройку - можно рассмотреть возможность замены его на поддельный.

Учитывая сказанное выше, стоит сделать предупреждение: Такая техника работает для маленьких/средних компонентов, с разумным числом дочерних элементов. Полностью отрендерить компонент с множеством дочерних может вызвать проблемы с поисками причин провала теста(анализ первопричин), а также может быть просто очень медленно. В подобных случаях следует писать меньше тестов для большого родительского коспонента и больше для для дочерних.

<br/>

❌ **Иначе:** Каждый раз обращаясь к приватным методам и сверяясь с внутренним состоянием тебе придется рефакторить все тесты после рефакторинга компонента. У тебя действительно есть возможности и время на это?

<br/>

<details><summary>✏ <b>Пример кода</b></summary>

<br/>

### :clap: Делай правильно Пример: Реалистичная работа с полностью отрендеренным компонентом

![](https://img.shields.io/badge/🔧%20Example%20using%20React-blue.svg "Examples with React") ![](https://img.shields.io/badge/🔧%20Example%20using%20Enzyme-blue.svg "Примеры с Enzyme")

```javascript
class Calendar extends React.Component {
  static defaultProps = { showFilters: false };

  render() {
    return (
      <div>
        A filters panel with a button to hide/show filters
        <FiltersPanel showFilter={showFilters} title="Choose Filters" />
      </div>
    );
  }
}

//Examples use React & Enzyme
test("Realistic approach: When clicked to show filters, filters are displayed", () => {
  // Arrange
  const wrapper = mount(<Calendar showFilters={false} />);

  // Act
  wrapper.find("button").simulate("click");

  // Assert
  expect(wrapper.text().includes("Choose Filter"));
  // This is how the user will approach this element: by text
});
```

### :thumbsdown: Анти-паттерн Пример: Моки с неполным рендерингом

```javascript
test("Shallow/mocked approach: When clicked to show filters, filters are displayed", () => {
  // Arrange
  const wrapper = shallow(<Calendar showFilters={false} title="Choose Filter" />);

  // Act
  wrapper
    .find("filtersPanel")
    .instance()
    .showFilters();
  // Tap into the internals, bypass the UI and invoke a method. White-box approach

  // Assert
  expect(wrapper.find("Filter").props()).toEqual({ title: "Choose Filter" });
  // what if we change the prop name or don't pass anything relevant?
});
```

</details>

<br/>

## ⚪ ️ 3.4 Не спи, используй поддержку асинхронности в фреймворках. Также пытайся ускоряться

:white_check_mark: **Делай:** In many cases, the unit under test completion time is just unknown (e.g. animation suspends element appearance) - in that case, avoid sleeping (e.g. setTimeOut) and prefer more deterministic methods that most platforms provide. Some libraries allows awaiting on operations (e.g. [Cypress cy.request('url')](https://docs.cypress.io/guides/references/best-practices.html#Unnecessary-Waiting)), other provide API for waiting like [@testing-library/dom method wait(expect(element))](https://testing-library.com/docs/guide-disappearance). Sometimes a more elegant way is to stub the slow resource, like API for example, and then once the response moment becomes deterministic the component can be explicitly re-rendered. When depending upon some external component that sleeps, it might turn useful to [hurry-up the clock](https://jestjs.io/docs/en/timer-mocks). Sleeping is a pattern to avoid because it forces your test to be slow or risky (when waiting for a too short period). Whenever sleeping and polling is inevitable and there's no support from the testing framework, some npm libraries like [wait-for-expect](https://www.npmjs.com/package/wait-for-expect) can help with a semi-deterministic solution
<br/>

❌ **Иначе:** When sleeping for a long time, tests will be an order of magnitude slower. When trying to sleep for small numbers, test will fail when the unit under test didn't respond in a timely fashion. So it boils down to a trade-off between flakiness and bad performance

<br/>

<details><summary>✏ <b>Пример кода</b></summary>

<br/>

### :clap: Делай правильно Пример: E2E API, которое вернет результат только после асинхронной функции (Cypress)

![](https://img.shields.io/badge/🔨%20Example%20using%20Cypress-blue.svg "Использование Cypress для илюстрации идеи")
![](https://img.shields.io/badge/🔧%20Example%20using%20React%20Testing%20Library-blue.svg "Примеры с react-testing-library")

```javascript
// using Cypress
cy.get("#show-products").click(); // navigate
cy.wait("@products"); // wait for route to appear
// this line will get executed only when the route is ready
```

### :clap: Делай правильно Пример: Библиотека для тестирования, которая ожидает DOM элементы

```javascript
// @testing-library/dom
test("movie title appears", async () => {
  // element is initially not present...

  // wait for appearance
  await wait(() => {
    expect(getByText("the lion king")).toBeInTheDocument();
  });

  // wait for appearance and return the element
  const movie = await waitForElement(() => getByText("the lion king"));
});
```

### :thumbsdown: Анти-паттерн Пример: Самописная релизация ожидания 

```javascript
test("movie title appears", async () => {
  // element is initially not present...

  // custom wait logic (caution: simplistic, no timeout)
  const interval = setInterval(() => {
    const found = getByText("the lion king");
    if (found) {
      clearInterval(interval);
      expect(getByText("the lion king")).toBeInTheDocument();
    }
  }, 100);

  // wait for appearance and return the element
  const movie = await waitForElement(() => getByText("the lion king"));
});
```

</details>

<br/>

## ⚪️  3.5 Следи за тем как контент доставляется по сети 

✅ **Делай:** Используй какие-нибудь способы скорости загрузки страницы, чтобы убедиться, что у страницы нет пролем с UX - медленной загрузки или неминифицированной сборки. Список инструментов для таких задач солидный: простые нструменты [pingdom](https://www.pingdom.com/), AWS CloudWatch, [gcp StackDriver](https://cloud.google.com/monitoring/uptime-checks/) можно легко настроить на проверку состояния сервера и времени ответа, соответствующего соглашению об уровне услуг (SLA). Это лишь верхушка айсберга возможных проблем, поэтому лучше использовать инструменты, специализирующиеся на фронтенде (например [lighthouse](https://developers.google.com/web/tools/lighthouse/), [pagespeed](https://developers.google.com/speed/pagespeed/insights/)) и проводить подробный анализ. В первую очередь нужно обращать внимание на метрики, связанные с UX - скорость загрузки страницы, [значимая отрисовка(meaningful paint)](https://scotch.io/courses/10-web-performance-audit-tips-for-your-next-billion-users-in-2018/fmp-first-meaningful-paint), [время до первого возможного взаимодействия(TTI)](https://calibreapp.com/blog/time-to-interactive/). Более того, можно отслеживать технические проблемы, такие как сжатие контента, время до первого байта, оптимизация изображения, размер DOM дерева, SSL и многое другое. Хорошей практикой использовать такой мониторинг и во время разработки, как часть CI, и что более важно - 24x7 на серверах продакшена/CDN

<br/>

❌ **Иначе:** Должно быть неприятно осознать после всей тяжелой работы по созданию UI, 100% проверке функциональными тестами, продуманной сборке проекта - UX ужасный и медленный из-за неправильной конфигурации CDN 

<br/>

<details><summary>✏️ <b>Пример кода</b></summary>

### 👏 Делай правильно Пример: Отчет о загрузке страницы с помощью Lighthouse

![](https://img.shields.io/badge/🔧%20Example%20using%20Google%20LightHouse-blue.svg "Примеры с Lighthouse")

![](/assets/lighthouse2.png "Отчет о загрузке страницы с помощью Lighthouse")

</details>

<br/>

## ⚪️  3.6 Делай заглушки для медленных источников, таких как API бэкенда

✅ **Делай:** Во время написания основных тестов (не E2E), избегай любых источников, за которые ты не отвечаешь и не можешь контролировать, таких как API бэкенда - используй вместо них заглушки (например тестовых дублеров). На практике вместо вызовов API используй библиотеки (например [Sinon](https://sinonjs.org/)),с [тестовыми дублерами](https://www.npmjs.com/package/testdouble) для создания заглушек.  Основное преимущество в таком подходе это отсутствие многослойности - тестирование API само по себе не очень стабильно и периодически будет проваливать тесты, хотя ТВОЙ компонент работает правильно(продакшн обычно не рассчитан на тестирование и просто ограничивает запросы). С помощью этого метода можно симулировать разное поведение API, необходимое для изменений поведения твоего компонента, такие как отсутвие данных или случай, когда API возвращает ошибку. И еще немаловажный пункт - запросы по сети очень сильно замедляют тесты

<br/>

❌ **Иначе:** Средний тест проходит за несколько мс, вызов API занимает больше 100мс, что делает каждый тест примерно в 20 раз медленее

<br/>

<details><summary>✏️ <b>Пример кода</b></summary>

<br/>

### 👏 Делай правильно Пример: Заглушка или перехват вызовов API

![](https://img.shields.io/badge/🔧%20Example%20using%20React-blue.svg "Примеры с React") ![](https://img.shields.io/badge/🔧%20Example%20using%20React%20Testing%20Library-blue.svg "Примеры с react-testing-library")

```javascript
// unit under test
export default function ProductsList() {
  const [products, setProducts] = useState(false);

  const fetchProducts = async () => {
    const products = await axios.get("api/products");
    setProducts(products);
  };

  useEffect(() => {
    fetchProducts();
  }, []);

  return products ? <div>{products}</div> : <div data-testid="no-products-message">No products</div>;
}

// test
test("When no products exist, show the appropriate message", () => {
  // Arrange
  nock("api")
    .get(`/products`)
    .reply(404);
			
  // Act
  const { getByTestId } = render(<ProductsList />);

  // Assert
  expect(getByTestId("no-products-message")).toBeTruthy();
});
```

</details>

<br/>

## ⚪️  3.7 Сделай парочку end-to-end тестов, которые охватывают всю систему целиком 

✅ **Делай:** Хотя E2E (end-to-end) обычно значит тестирования только UI в реальном браузере (смотри пункт 3.6), также так называют тесты, которые охватывают всю систему в целом, включая реальный бэкенд. Такие тесты очень ценны тем, что позволяют обнаружить баги, связанные с интеграцией фронтенда и бэкенда, которые обычно появляются в связи с неправильным пониманием схемы обмена. Также они являются эффективным методом для обнаружения ошибок интеграции бэкенд-бэкенд (например Микросервис А отправляет неправильное сообщение Микросервису Б) и даже обнаружить проблемы с деплоем - нет такого фреймворка для тестирования E2E бэкенда, который был бы таким же дружелюбным и целостным, как UI фреймворки типа [Cypress](https://www.cypress.io/) и [Puppeteer](https://github.com/GoogleChrome/puppeteer). Минусы таких тестов состоят в сложности конфигурации окружения для большого количества компонентов, и в основном их хрупкости - если из 50 микросервисов хотя бы один провалится, то и весь E2E тест тоже провалится. Поэтому мы должны использовать эту технику экономно, имея всего 1-10 таких тестов. Тем не менее, даже несколько E2E тестов отловят те ошибки, для которых и были написаны - ошибки интеграции и деплоя. Их желательно запускать в среде, близкой к продакшену

<br/>

❌ **Иначе:** Можно инвестировать очень много в тестирования функциональности UI, чтобы потом понять, что бэкенд возвращает нагрузку (схема данных, с которой работает UI), которая отличается от ожидаемой

<br/>

## ⚪️  3.8 Ускорь E2E тесты, переиспользуя данные для логина

✅ **Делай:** В E2E тестах, которые используют реальный бэкенд и полагаются на валидный токен для запросов API, не стоит изолировать тесты до уровня, когда нужно создавать пользователя и заходить в систему перед каждым запросом. Вместо этого, залогинься перед началом тестов(например с помощью before-all), сохрани токен где-нибудь в local storage и используй для всех запросов. Это выглядит как нарушение одного из основных принципов тестирования - делать тесты независимые от ресурсов. Хотя это и правильное возмущение, в E2E тестах производительность это один из ключевых параметров и создавая 1-3 API запроса перед каждым отдельным тестом может привезти к ужасному времени исполнения. Переиспользование данных для авторизации не значит, что тесты должны работать с одинаковыми данными пользователя - если необходимо (например проверить пользовательскую историю оплаты) создай такие данные как часть теста и проверь, чтобы они использовались только в этом тесте. Также помни, что бэкенд может быть ненастоящим - если твои тесты сфокусированы на фронтенде, лучше изолировать их и использовать заглушку для API (смотри пункт 3.6)

<br/>

❌ **Иначе:** Если есть 200 тестов и процедура логина для каждого займет около 100мс, то только 20 секунд уйдет лишь на постоянный логин-логаут 

<br/>

<details><summary>✏️ <b>Пример кода</b></summary>

<br/>

### 👏 Делай правильно Пример: Логин используя before-all, а не before-each

![](https://img.shields.io/badge/🔨%20Example%20using%20Cypress-blue.svg "Использование в качестве илюстрации Cypress")

```javascript
let authenticationToken;

// happens before ALL tests run
before(() => {
  cy.request('POST', 'http://localhost:3000/login', {
      username: Cypress.env('username'),
      password: Cypress.env('password'),
  })
  .its('body')
  .then((responseFromLogin) => {
    authenticationToken = responseFromLogin.token;
  })
})

// happens before EACH test
  beforeEach(setUser => () {
    cy.visit('/home', {
      onBeforeLoad (win) {
        win.localStorage.setItem('token', JSON.stringify(authenticationToken))
      },
    })
  })

```

</details>

<br/>

## ⚪️  3.9 Сделай один E2E дымовой тест, который просто проходит по карте сайта 

✅ **Делай:** Для мониторинга продакшена и проверки работоспособности во время разработки, запускай один E2E тест, который посещает все/почти все страницы и проверяет что ничего не сломалось. Такой тип тестов быстро окупается, ведь его просто поддерживать и при этом он может обнаружить множество разных проблем, включая функциональные проблемы, проблемы с сетью или деплоем. Други виды дымового тестирования обычно не так эффективны - некоторые команды просто пингуют главную страницу (продакшен) или разработчики, запускающие кучу интеграционных тестов, которые не могут обнаружить проблем с пакетами или браузером. Само собой дымовое тестирование не заменяет функциональных тестов, а просто является быстрым способом понять что что-то не работает 

<br/>

❌ **Иначе:** Все выглядит идеально, тесты пройдены, проверка продакшена тоже говорит что все хорошо, но у компонента Payment проблема с пакетами и только путь /Payment не рендерится

<br/>

<details><summary>✏️ <b>Пример кода</b></summary>

<br/>

### 👏 Делай правильно Пример: Дымовой тест проходит по всем страницам

![](https://img.shields.io/badge/🔨%20Example%20using%20Cypress-blue.svg "Использование в качестве илюстрации Cypress")

```javascript
it("When doing smoke testing over all page, should load them all successfully", () => {
  // exemplified using Cypress but can be implemented easily
  // using any E2E suite
  cy.visit("https://mysite.com/home");
  cy.contains("Home");
  cy.contains("https://mysite.com/Login");
  cy.contains("Login");
  cy.contains("https://mysite.com/About");
  cy.contains("About");
});
```

</details>

<br/>

## ⚪️  3.10 Используй тесты как совместный документ

✅ **Делай:** Кроме увеличения надежности приложения, тесты приносят еще одну интерсную возможность - их можно использовать как живую документацию к приложению. Так как тесты сами по себе говорят на языке менее техническом и более UX/продуктовом, используя правильные инструменты они могу служить связью между всеми заинтересованными - разработчиками и их клиентами. Например, некоторые фреймворки позволяют описать последовательность и ожидание (например тест план) используя человеко-читаемый язык, так что любой заинтересованный, в том числе продуктовые менеджеры, могут читать, одобрять и совместно принимать решения, так что тесты становятся просто документом с необходимыми требованиями. Эта техника также известна как "приёмочный тест", так как она позволяет заказчику объяснить простым языком свои требования к системе. Это [тестирование на основе поведения(behavior-driven testing, BDD)](https://ru.wikipedia.org/wiki/BDD_(%D0%BF%D1%80%D0%BE%D0%B3%D1%80%D0%B0%D0%BC%D0%BC%D0%B8%D1%80%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5)) в чистом виде. Один из популярных фреймворков для такого подхода это [Cucumber с его JS версией](https://github.com/cucumber/cucumber-js), примеры с ним можно увидеть ниже. Другое интересное решение предлагает , позволяя создавать каталог, состоящий из компонентов в разных состояниях (например отрендерить таблицу с фильтрами или без, с множеством полей или без полей и т.д.), чтобы посмотреть как они выглядят и как происходит переход между состояниями - Storybook могут использовать и проектные ребята, но чаще всего разработчики используют этот инструмент как документацию для используемых элементов.

❌ **Иначе:** После огромных вложений в тестирование, просто жалко не использовать эти инвестиции и не получить выгоду

<br/>

<details><summary>✏️ <b>Пример кода</b></summary>

<br/>

### 👏 Делай правильно Пример: Описание теста человеко-понятным языком используя cucumber-js

![](https://img.shields.io/badge/🔨%20Example%20using%20Cucumber-blue.svg "Примеры с Cucumber")

```javascript
// this is how one can describe tests using cucumber: plain language that allows anyone to understand and collaborate

Feature: Twitter new tweet

  I want to tweet something in Twitter

  @focus
  Scenario: Tweeting from the home page
    Given I open Twitter home
    Given I click on "New tweet" button
    Given I type "Hello followers!" in the textbox
    Given I click on "Submit" button
    Then I see message "Tweet saved"

```

### 👏 Делай правильно Пример: Отображение компонентов, различных состояний и вводов используя Storybook

![](https://img.shields.io/badge/🔨%20Example%20using%20StoryBook-blue.svg "Пример с StoryBook")

![alt text](assets/story-book.jpg "Storybook")

</details>

<br/><br/>

## ⚪️  3.11 Находи ошибки в отображении используя автоматизированные инструменты

✅ **Делай:** Настрой инструменты, которые делают снимки UI при его изменении, чтобы обнаружить визуальные проблемы тип наложения контента или разрывов. Таким образом ты проверишь, что правильные данные не только подготовлены, но и будут показаны пользователю. Такая техника не сильно распространена, наш образ мысли склоняется к функциональным тестам, но визуальное отображение влияет на пользовательский опыт и с таким количеством разных видов устройств очень легко пропустить неприятный UI баг. Некоторые бесплатные инструменты дают основной функционал - создавать и сохранять скриншоты для дальнейшего изучения человеком. Хотя такой подход и подходит для маленьких приложений, он как и любое ручное тестирование плохо себя показывает при любых изменениях. С другой стороны, достаточно сложно обнаружить проблемы с UI аавтоматически из-за отсутствия четких требований - здесь на помощь приходит "Визуальная регрессия", сравнивая старый UI с последними изменениями и показывая различия. Некоторые проекты из open source/бесплатные инструменты могут предложить такую функциональность (например [wraith](https://github.com/BBC-News/wraith), [PhantomCSS](https://github.com/HuddleEng/PhantomCSS)), но они требуют значительного времени для настройки. Платные инструменты (например [Applitools](https://applitools.com/), [Percy.io](https://percy.io/)) идут дальше, делая процес установки проще и добавляя дополнительные функции типа управление UI, уведомления, умный захват,который убирает "визуальный шум" (например рекламу или анимации) и даже определение причин ошибки, анлизируя изменения DOM/CSS

<br/>

❌ **Иначе:** Насколько хороша страница с крутым контентом (100% тестов пройдено), которая загружается мгновенно, но половина контента скрыта?

<br/>

<details><summary>✏️ <b>Пример кода</b></summary>

<br/>

### :thumbsdown: Анти-паттерн Пример: Типичный пример визуальной регрессии - правильный контент неправильно подан

![alt text](assets/amazon-visual-regression.jpeg "Поломанная страничка Amazon")

<br/>

### 👏 Делай правильно: Настройка wraith и сравнение снимков UI

![](https://img.shields.io/badge/🔨%20Example%20using%20Wraith-blue.svg "Использование Wraith")

```
# Add as many domains as necessary. Key will act as a label 

domains:
  english: "http://www.mysite.com" 

# Type screen widths below, here are a couple of examples 

screen_widths:

  - 600 
  - 768 
  - 1024 
  - 1280 

# Type page URL paths below, here are a couple of examples 
  paths:
    about:
      path: /about
      selector: '.about' 
    subscribe:
      selector: '.subscribe' 
      path: /subscribe

```

### 👏 Делай правильно Пример: Использование Applitools для получения сравнения снимков и других полезных функций

![](https://img.shields.io/badge/🔨%20Example%20using%20AppliTools-blue.svg "Использование Applitools") ![](https://img.shields.io/badge/🔨%20Example%20using%20Cypress-blue.svg "Использование в качестве илюстрации Cypress")

```javascript
import * as todoPage from "../page-objects/todo-page";

describe("visual validation", () => {
  before(() => todoPage.navigate());
  beforeEach(() => cy.eyesOpen({ appName: "TAU TodoMVC" }));
  afterEach(() => cy.eyesClose());

  it("should look good", () => {
    cy.eyesCheckWindow("empty todo list");
    todoPage.addTodo("Clean room");
    todoPage.addTodo("Learn javascript");
    cy.eyesCheckWindow("two todos");
    todoPage.toggleTodo(0);
    cy.eyesCheckWindow("mark as completed");
  });
});

```

</details>

<br/><br/>

# Section 4️⃣: Measuring Test Effectiveness

<br/><br/>

## ⚪ ️ 4.1 Get enough coverage for being confident, ~80% seems to be the lucky number

:white_check_mark: **Do:** The purpose of testing is to get enough confidence for moving fast, obviously the more code is tested the more confident the team can be. Coverage is a measure of how many code lines (and branches, statements, etc) are being reached by the tests. So how much is enough? 10–30% is obviously too low to get any sense about the build correctness, on the other side 100% is very expensive and might shift your focus from the critical paths to the exotic corners of the code. The long answer is that it depends on many factors like the type of application — if you’re building the next generation of Airbus A380 than 100% is a must, for a cartoon pictures website 50% might be too much. Although most of the testing enthusiasts claim that the right coverage threshold is contextual, most of them also mention the number 80% as a thumb of a rule ([Fowler: “in the upper 80s or 90s”](https://martinfowler.com/bliki/TestCoverage.html)) that presumably should satisfy most of the applications.

Implementation tips: You may want to configure your continuous integration (CI) to have a coverage threshold ([Jest link](https://jestjs.io/docs/en/configuration.html#collectcoverage-boolean)) and stop a build that doesn’t stand to this standard (it’s also possible to configure threshold per component, see code example below). On top of this, consider detecting build coverage decrease (when a newly committed code has less coverage) — this will push developers raising or at least preserving the amount of tested code. All that said, coverage is only one measure, a quantitative based one, that is not enough to tell the robustness of your testing. And it can also be fooled as illustrated in the next bullets

<br/>

❌ **Otherwise:** Confidence and numbers go hand in hand, without really knowing that you tested most of the system — there will also be some fear and fear will slow you down

<br/>

<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :clap: Example: A typical coverage report

![alt text](assets/bp-18-yoni-goldberg-code-coverage.png "A typical coverage report")

<br/>

### :clap: Doing It Right Example: Setting up coverage per component (using Jest)

![](https://img.shields.io/badge/🔨%20Example%20using%20Jest-blue.svg "Using Jest")

![alt text](assets/bp-18-code-coverage2.jpeg "Setting up coverage per component (using Jest)")

</details>

<br/><br/>

## ⚪ ️ 4.2 Inspect coverage reports to detect untested areas and other oddities

:white_check_mark: **Do:** Some issues sneak just under the radar and are really hard to find using traditional tools. These are not really bugs but more of surprising application behavior that might have a severe impact. For example, often some code areas are never or rarely being invoked — you thought that the ‘PricingCalculator’ class is always setting the product price but it turns out it is actually never invoked although we have 10000 products in DB and many sales… Code coverage reports help you realize whether the application behaves the way you believe it does. Other than that, it can also highlight which types of code is not tested — being informed that 80% of the code is tested doesn’t tell whether the critical parts are covered. Generating reports is easy — just run your app in production or during testing with coverage tracking and then see colorful reports that highlight how frequent each code area is invoked. If you take your time to glimpse into this data — you might find some gotchas
<br/>

❌ **Otherwise:** If you don’t know which parts of your code are left un-tested, you don’t know where the issues might come from

<br/>

<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :thumbsdown: Anti-Pattern Example: What’s wrong with this coverage report?

Based on a real-world scenario where we tracked our application usage in QA and find out interesting login patterns (Hint: the amount of login failures is non-proportional, something is clearly wrong. Finally it turned out that some frontend bug keeps hitting the backend login API)

![alt text](assets/bp-19-coverage-yoni-goldberg-nodejs-consultant.png "What’s wrong with this coverage report?")

</details>

<br/><br/>

## ⚪ ️ 4.3 Measure logical coverage using mutation testing

:white_check_mark: **Do:** The Traditional Coverage metric often lies: It may show you 100% code coverage, but none of your functions, even not one, return the right response. How come? it simply measures over which lines of code the test visited, but it doesn’t check if the tests actually tested anything — asserted for the right response. Like someone who’s traveling for business and showing his passport stamps — this doesn’t prove any work done, only that he visited few airports and hotels.

Mutation-based testing is here to help by measuring the amount of code that was actually TESTED not just VISITED. [Stryker](https://stryker-mutator.io/) is a JavaScript library for mutation testing and the implementation is really neat:

(1) it intentionally changes the code and “plants bugs”. For example the code newOrder.price===0 becomes newOrder.price!=0. This “bugs” are called mutations

(2) it runs the tests, if all succeed then we have a problem — the tests didn’t serve their purpose of discovering bugs, the mutations are so-called survived. If the tests failed, then great, the mutations were killed.

Knowing that all or most of the mutations were killed gives much higher confidence than traditional coverage and the setup time is similar
<br/>

❌ **Otherwise:** You’ll be fooled to believe that 85% coverage means your test will detect bugs in 85% of your code

<br/>

<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :thumbsdown: Anti-Pattern Example: 100% coverage, 0% testing

![](https://img.shields.io/badge/🔨%20Example%20using%20Stryker-blue.svg "Using Stryker")

```javascript
function addNewOrder(newOrder) {
  logger.log(`Adding new order ${newOrder}`);
  DB.save(newOrder);
  Mailer.sendMail(newOrder.assignee, `A new order was places ${newOrder}`);

  return { approved: true };
}

it("Test addNewOrder, don't use such test names", () => {
  addNewOrder({ assignee: "John@mailer.com", price: 120 });
}); //Triggers 100% code coverage, but it doesn't check anything
```

<br/>

### :clap: Doing It Right Example: Stryker reports, a tool for mutation testing, detects and counts the amount of code that is not tested (Mutations)

![alt text](assets/bp-20-yoni-goldberg-mutation-testing.jpeg "Stryker reports, a tool for mutation testing, detects and counts the amount of code that is not tested (Mutations)")

</details>

<br/><br/>

## ⚪ ️4.4 Preventing test code issues with Test linters

:white_check_mark: **Do:** A set of ESLint plugins were built specifically for inspecting the tests code patterns and discover issues. For example, [eslint-plugin-mocha](https://www.npmjs.com/package/eslint-plugin-mocha) will warn when a test is written at the global level (not a son of a describe() statement) or when tests are [skipped](https://mochajs.org/#inclusive-tests) which might lead to a false belief that all tests are passing. Similarly, [eslint-plugin-jest](https://github.com/jest-community/eslint-plugin-jest) can, for example, warn when a test has no assertions at all (not checking anything)

<br/>

❌ **Otherwise:** Seeing 90% code coverage and 100% green tests will make your face wear a big smile only until you realize that many tests aren’t asserting for anything and many test suites were just skipped. Hopefully, you didn’t deploy anything based on this false observation

<br/>
<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :thumbsdown: Anti-Pattern Example: A test case full of errors, luckily all are caught by Linters

```javascript
describe("Too short description", () => {
  const userToken = userService.getDefaultToken() // *error:no-setup-in-describe, use hooks (sparingly) instead
  it("Some description", () => {});//* error: valid-test-description. Must include the word "Should" + at least 5 words
});

it.skip("Test name", () => {// *error:no-skipped-tests, error:error:no-global-tests. Put tests only under describe or suite
  expect("somevalue"); // error:no-assert
});

it("Test name", () => {*//error:no-identical-title. Assign unique titles to tests
});
```

</details>

<br/><br/>

# Section 5️⃣: CI and Other Quality Measures

<br/><br/>

## ⚪ ️ 5.1 Enrich your linters and abort builds that have linting issues

:white_check_mark: **Do:** Linters are a free lunch, with 5 min setup you get for free an auto-pilot guarding your code and catching significant issue as you type. Gone are the days where linting was about cosmetics (no semi-colons!). Nowadays, Linters can catch severe issues like errors that are not thrown correctly and losing information. On top of your basic set of rules (like [ESLint standard](https://www.npmjs.com/package/eslint-plugin-standard) or [Airbnb style](https://www.npmjs.com/package/eslint-config-airbnb)), consider including some specializing Linters like [eslint-plugin-chai-expect](https://www.npmjs.com/package/eslint-plugin-chai-expect) that can discover tests without assertions, [eslint-plugin-promise](https://www.npmjs.com/package/eslint-plugin-promise?activeTab=readme) can discover promises with no resolve (your code will never continue), [eslint-plugin-security](https://www.npmjs.com/package/eslint-plugin-security?activeTab=readme) which can discover eager regex expressions that might get used for DOS attacks, and [eslint-plugin-you-dont-need-lodash-underscore](https://www.npmjs.com/package/eslint-plugin-you-dont-need-lodash-underscore) is capable of alarming when the code uses utility library methods that are part of the V8 core methods like Lodash.\_map(…)
<br/>

❌ **Otherwise:** Consider a rainy day where your production keeps crashing but the logs don’t display the error stack trace. What happened? Your code mistakenly threw a non-error object and the stack trace was lost, a good reason for banging your head against a brick wall. A 5 min linter setup could detect this TYPO and save your day

<br/>

<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :thumbsdown: Anti-Pattern Example: The wrong Error object is thrown mistakenly, no stack-trace will appear for this error. Luckily, ESLint catches the next production bug

![alt text](assets/bp-21-yoni-goldberg-eslint.jpeg "The wrong Error object is thrown mistakenly, no stack-trace will appear for this error. Luckily, ESLint catches the next production bug")

</details>

<br/><br/>

## ⚪ ️ 5.2 Shorten the feedback loop with local developer-CI

:white_check_mark: **Do:** Using a CI with shiny quality inspections like testing, linting, vulnerabilities check, etc? Help developers run this pipeline also locally to solicit instant feedback and shorten the [feedback loop](https://www.gocd.org/2016/03/15/are-you-ready-for-continuous-delivery-part-2-feedback-loops/). Why? an efficient testing process constitutes many and iterative loops: (1) try-outs -> (2) feedback -> (3) refactor. The faster the feedback is, the more improvement iterations a developer can perform per-module and perfect the results. On the flip, when the feedback is late to come fewer improvement iterations could be packed into a single day, the team might already move forward to another topic/task/module and might not be up for refining that module.

Practically, some CI vendors (Example: [CircleCI local CLI](https://circleci.com/docs/2.0/local-cli/)) allow running the pipeline locally. Some commercial tools like [wallaby provide highly-valuable & testing insights](https://wallabyjs.com/) as a developer prototype (no affiliation). Alternatively, you may just add npm script to package.json that runs all the quality commands (e.g. test, lint, vulnerabilities) — use tools like [concurrently](https://www.npmjs.com/package/concurrently) for parallelization and non-zero exit code if one of the tools failed. Now the developer should just invoke one command — e.g. ‘npm run quality’ — to get instant feedback. Consider also aborting a commit if the quality check failed using a githook ([husky can help](https://github.com/typicode/husky))
<br/>

❌ **Otherwise:** When the quality results arrive the day after the code, testing doesn’t become a fluent part of development rather an after the fact formal artifact

<br/>

<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :clap: Doing It Right Example: npm scripts that perform code quality inspection, all are run in parallel on demand or when a developer is trying to push new code

```javascript
"scripts": {
    "inspect:sanity-testing": "mocha **/**--test.js --grep \"sanity\"",
    "inspect:lint": "eslint .",
    "inspect:vulnerabilities": "npm audit",
    "inspect:license": "license-checker --failOn GPLv2",
    "inspect:complexity": "plato .",

    "inspect:all": "concurrently -c \"bgBlue.bold,bgMagenta.bold,yellow\" \"npm:inspect:quick-testing\" \"npm:inspect:lint\" \"npm:inspect:vulnerabilities\" \"npm:inspect:license\""
  },
  "husky": {
    "hooks": {
      "precommit": "npm run inspect:all",
      "prepush": "npm run inspect:all"
    }
}

```

</details>

<br/><br/>

## ⚪ ️5.3 Perform e2e testing over a true production-mirror

:white_check_mark: **Do:** End to end (e2e) testing are the main challenge of every CI pipeline — creating an identical ephemeral production mirror on the fly with all the related cloud services can be tedious and expensive. Finding the best compromise is your game: [Docker-compose](https://serverless.com/) allows crafting isolated dockerized environment with identical containers using a single plain text file but the backing technology (e.g. networking, deployment model) is different from real-world productions. You may combine it with [‘AWS Local’](https://github.com/localstack/localstack) to work with a stub of the real AWS services. If you went [serverless](https://serverless.com/) multiple frameworks like serverless and [AWS SAM](https://docs.aws.amazon.com/lambda/latest/dg/serverless_app.html) allows the local invocation of FaaS code.

The huge Kubernetes ecosystem is yet to formalize a standard convenient tool for local and CI-mirroring though many new tools are launched frequently. One approach is running a ‘minimized-Kubernetes’ using tools like [Minikube](https://kubernetes.io/docs/setup/minikube/) and [MicroK8s](https://microk8s.io/) which resemble the real thing only come with less overhead. Another approach is testing over a remote ‘real-Kubernetes’, some CI providers (e.g. [Codefresh](https://codefresh.io/)) has native integration with Kubernetes environment and make it easy to run the CI pipeline over the real thing, others allow custom scripting against a remote Kubernetes.
<br/>

❌ **Otherwise:** Using different technologies for production and testing demands maintaining two deployment models and keeps the developers and the ops team separated

<br/>

<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :clap: Example: a CI pipeline that generates Kubernetes cluster on the fly <a href="https://container-solutions.com/dynamic-environments-kubernetes/" data-href="https://container-solutions.com/dynamic-environments-kubernetes/" class="markup--anchor markup--p-anchor" rel="noopener nofollow" target="_blank">([Credit: Dynamic-environments Kubernetes](https://container-solutions.com/dynamic-environments-kubernetes/))</a>

<pre name="38d9" id="38d9" class="graf graf--pre graf-after--p">deploy:<br>stage: deploy<br>image: registry.gitlab.com/gitlab-examples/kubernetes-deploy<br>script:<br>- ./configureCluster.sh $KUBE_CA_PEM_FILE $KUBE_URL $KUBE_TOKEN<br>- kubectl create ns $NAMESPACE<br>- kubectl create secret -n $NAMESPACE docker-registry gitlab-registry --docker-server="$CI_REGISTRY" --docker-username="$CI_REGISTRY_USER" --docker-password="$CI_REGISTRY_PASSWORD" --docker-email="$GITLAB_USER_EMAIL"<br>- mkdir .generated<br>- echo "$CI_BUILD_REF_NAME-$CI_BUILD_REF"<br>- sed -e "s/TAG/$CI_BUILD_REF_NAME-$CI_BUILD_REF/g" templates/deals.yaml | tee ".generated/deals.yaml"<br>- kubectl apply --namespace $NAMESPACE -f .generated/deals.yaml<br>- kubectl apply --namespace $NAMESPACE -f templates/my-sock-shop.yaml<br>environment:<br>name: test-for-ci</pre>

</details>

<br/><br/>

## ⚪ ️5.4 Parallelize test execution

:white_check_mark: **Do:** When done right, testing is your 24/7 friend providing almost instant feedback. In practice, executing 500 CPU-bounded unit test on a single thread can take too long. Luckily, modern test runners and CI platforms (like [Jest](https://github.com/facebook/jest), [AVA](https://github.com/avajs/ava) and [Mocha extensions](https://github.com/yandex/mocha-parallel-tests)) can parallelize the test into multiple processes and achieve significant improvement in feedback time. Some CI vendors do also parallelize tests across containers (!) which shortens the feedback loop even further. Whether locally over multiple processes, or over some cloud CLI using multiple machines — parallelizing demand keeping the tests autonomous as each might run on different processes

❌ **Otherwise:** Getting test results 1 hour long after pushing new code, as you already code the next features, is a great recipe for making testing less relevant

<br/>

<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :clap: Doing It Right Example: Mocha parallel & Jest easily outrun the traditional Mocha thanks to testing parallelization ([Credit: JavaScript Test-Runners Benchmark](https://medium.com/dailyjs/javascript-test-runners-benchmark-3a78d4117b4))

![alt text](assets/bp-24-yonigoldberg-jest-parallel.png "Mocha parallel & Jest easily outrun the traditional Mocha thanks to testing parallelization (Credit: JavaScript Test-Runners Benchmark)")

</details>

<br/><br/>

## ⚪ ️5.5 Stay away from legal issues using license and plagiarism check

:white_check_mark: **Do:** Licensing and plagiarism issues are probably not your main concern right now, but why not tick this box as well in 10 minutes? A bunch of npm packages like [license check](https://www.npmjs.com/package/license-checker) and [plagiarism check](https://www.npmjs.com/package/plagiarism-checker) (commercial with free plan) can be easily baked into your CI pipeline and inspect for sorrows like dependencies with restrictive licenses or code that was copy-pasted from Stack Overflow and apparently violates some copyrights

❌ **Otherwise:** Unintentionally, developers might use packages with inappropriate licenses or copy paste commercial code and run into legal issues

<br/>

<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :clap: Doing It Right Example:

```javascript
//install license-checker in your CI environment or also locally
npm install -g license-checker

//ask it to scan all licenses and fail with exit code other than 0 if it found unauthorized license. The CI system should catch this failure and stop the build
license-checker --summary --failOn BSD

```

<br/>

![alt text](assets/bp-25-nodejs-licsense.png)

</details>

<br/><br/>

## ⚪ ️5.6 Constantly inspect for vulnerable dependencies

:white_check_mark: **Do:** Even the most reputable dependencies such as Express have known vulnerabilities. This can get easily tamed using community tools such as [npm audit](https://docs.npmjs.com/getting-started/running-a-security-audit), or commercial tools like [snyk](https://snyk.io/) (offer also a free community version). Both can be invoked from your CI on every build

❌ **Otherwise:** Keeping your code clean from vulnerabilities without dedicated tools will require to constantly follow online publications about new threats. Quite tedious

<br/>

<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :clap: Example: NPM Audit result

![alt text](assets/bp-26-npm-audit-snyk.png "NPM Audit result")

</details>

<br/><br/>

## ⚪ ️5.7 Automate dependency updates

:white_check_mark: **Do:** Yarn and npm latest introduction of package-lock.json introduced a serious challenge (the road to hell is paved with good intentions) — by default now, packages are no longer getting updates. Even a team running many fresh deployments with ‘npm install’ & ‘npm update’ won’t get any new updates. This leads to subpar dependent packages versions at best or to vulnerable code at worst. Teams now rely on developers goodwill and memory to manually update the package.json or use tools [like ncu](https://www.npmjs.com/package/npm-check-updates) manually. A more reliable way could be to automate the process of getting the most reliable dependency versions, though there are no silver bullet solutions yet there are two possible automation roads:

(1) CI can fail builds that have obsolete dependencies — using tools like [‘npm outdated’](https://docs.npmjs.com/cli/outdated) or ‘npm-check-updates (ncu)’ . Doing so will enforce developers to update dependencies.

(2) Use commercial tools that scan the code and automatically send pull requests with updated dependencies. One interesting question remaining is what should be the dependency update policy — updating on every patch generates too many overhead, updating right when a major is released might point to an unstable version (many packages found vulnerable on the very first days after being released, [see the](https://nodesource.com/blog/a-high-level-post-mortem-of-the-eslint-scope-security-incident/) eslint-scope incident).

An efficient update policy may allow some ‘vesting period’ — let the code lag behind the @latest for some time and versions before considering the local copy as obsolete (e.g. local version is 1.3.1 and repository version is 1.3.8)
<br/>

❌ **Otherwise:** Your production will run packages that have been explicitly tagged by their author as risky

<br/>

<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :clap: Example: [ncu](https://www.npmjs.com/package/npm-check-updates) can be used manually or within a CI pipeline to detect to which extent the code lag behind the latest versions

![alt text](assets/bp-27-yoni-goldberg-npm.png "ncu can be used manually or within a CI pipeline to detect to which extent the code lag behind the latest versions")

</details>

<br/><br/>

## ⚪ ️ 5.8 Other, non-Node related, CI tips

:white_check_mark: **Do:** This post is focused on testing advice that is related to, or at least can be exemplified with Node JS. This bullet, however, groups few non-Node related tips that are well-known

 <ol class="postList"><li name="e3e4" id="e3e4" class="graf graf--li graf-after--p">Use a declarative syntax. This is the only option for most vendors but older versions of Jenkins allows using code or UI</li><li name="1fdc" id="1fdc" class="graf graf--li graf-after--li">Opt for a vendor that has native Docker support</li><li name="edcd" id="edcd" class="graf graf--li graf-after--li">Fail early, run your fastest tests first. Create a ‘Smoke testing’ step/milestone that groups multiple fast inspections (e.g. linting, unit tests) and provide snappy feedback to the code committer</li><li name="0375" id="0375" class="graf graf--li graf-after--li">Make it easy to skim-through all build artifacts including test reports, coverage reports, mutation reports, logs, etc</li><li name="df82" id="df82" class="graf graf--li graf-after--li">Create multiple pipelines/jobs for each event, reuse steps between them. For example, configure a job for feature branch commits and a different one for master PR. Let each reuse logic using shared steps (most vendors provide some mechanism for code reuse)</li><li name="19b0" id="19b0" class="graf graf--li graf-after--li">Never embed secrets in a job declaration, grab them from a secret store or from the job’s configuration</li><li name="b70d" id="b70d" class="graf graf--li graf-after--li">Explicitly bump version in a release build or at least ensure the developer did so</li><li name="957c" id="957c" class="graf graf--li graf-after--li">Build only once and perform all the inspections over the single build artifact (e.g. Docker image)</li><li name="339b" id="339b" class="graf graf--li graf-after--li">Test in an ephemeral environment that doesn’t drift state between builds. Caching node_modules might be the only exception</li></ol>
<br/>

❌ **Otherwise:** You‘ll miss years of wisdom

<br/><br/>

## ⚪ ️ 5.9 Build matrix: Run the same CI steps using multiple Node versions

:white_check_mark: **Do:** Quality checking is about serendipity, the more ground you cover the luckier you get in detecting issues early. When developing reusable packages or running a multi-customer production with various configuration and Node versions, the CI must run the pipeline of tests over all the permutations of configurations. For example, assuming we use MySQL for some customers and Postgres for others — some CI vendors support a feature called ‘Matrix’ which allow running the suit of testing against all permutations of MySQL, Postgres and multiple Node version like 8, 9 and 10. This is done using configuration only without any additional effort (assuming you have testing or any other quality checks). Other CIs who doesn’t support Matrix might have extensions or tweaks to allow that
<br/>

❌ **Otherwise:** So after doing all that hard work of writing testing are we going to let bugs sneak in only because of configuration issues?

<br/>

<details><summary>✏ <b>Code Examples</b></summary>

<br/>

### :clap: Example: Using Travis (CI vendor) build definition to run the same test over multiple Node versions

<pre name="f909" id="f909" class="graf graf--pre graf-after--p">language: node_js<br>node_js:<br>  - "7"<br>  - "6"<br>  - "5"<br>  - "4"<br>install:<br>  - npm install<br>script:<br>  - npm run test</pre>
</details>

<br/><br/>

# Team

## Yoni Goldberg

<br/>
<img width="480px" src="assets/yoni-goldberg.jpg"/>
<br/>

**Role:** Writer

**About:** I'm an independent consultant who works with Fortune 500 companies and garage startups on polishing their JS & Node.js applications. More than any other topic I'm fascinated by and aims to master the art of testing. I'm also the author of [Node.js Best Practices](https://github.com/goldbergyoni/nodebestpractices)

**📗 Online Course:** Liked this guide and wish to take your testing skills to the extreme? Consider visiting my comprehensive course [Testing Node.js & JavaScript From A To Z](https://www.testjavascript.com)

<br/>

**Follow:**

- [🐦 Twitter](https://twitter.com/goldbergyoni/)
- [📞 Contact](https://testjavascript.com/contact-2/)
- [✉️ Newsletter](https://testjavascript.com/newsletter//)

<br/>
<hr/>
<br/>

## [Bruno Scheufler](https://github.com/BrunoScheufler)

**Role:** Tech reviewer and advisor

Took care to revise, improve, lint and polish all the texts

**About:** full-stack web engineer, Node.js & GraphQL enthusiast

<hr/>
<br/>

## [Ido Richter](https://github.com/idori)

**Role:** Concept, design and great advice

**About:** A savvy frontend developer, CSS expert and emojis freak

## [Kyle Martin](https://github.com/js-kyle)

**Role:** Helps keep this project running, and reviews security related practices

**About:** Loves working on Node.js projects and web application security.

## Contributors ✨

Thanks goes to these wonderful people who have contributed to this repository!

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a href="http://geospatialscott.blogspot.com/"><img src="https://avatars3.githubusercontent.com/u/1326248?v=4" width="100px;" alt=""/><br /><sub><b>Scott Davis</b></sub></a><br /><a href="#content-stdavis" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/AdrienRedon"><img src="https://avatars2.githubusercontent.com/u/5978436?v=4" width="100px;" alt=""/><br /><sub><b>Adrien REDON</b></sub></a><br /><a href="#content-AdrienRedon" title="Content">🖋</a></td>
    <td align="center"><a href="https://twitter.com/NoriSte"><img src="https://avatars0.githubusercontent.com/u/173663?v=4" width="100px;" alt=""/><br /><sub><b>Stefano Magni</b></sub></a><br /><a href="#content-NoriSte" title="Content">🖋</a></td>
    <td align="center"><a href="https://www.joer.im"><img src="https://avatars2.githubusercontent.com/u/47742486?v=4" width="100px;" alt=""/><br /><sub><b>Yeoh Joer</b></sub></a><br /><a href="#content-yjoer" title="Content">🖋</a></td>
    <td align="center"><a href="http://jhonnymoreira.dev"><img src="https://avatars0.githubusercontent.com/u/2177742?v=4" width="100px;" alt=""/><br /><sub><b>Jhonny Moreira</b></sub></a><br /><a href="#content-jhonnymoreira" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/Germanika"><img src="https://avatars2.githubusercontent.com/u/8846678?v=4" width="100px;" alt=""/><br /><sub><b>Ian Germann</b></sub></a><br /><a href="#content-Germanika" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/AbdelrahmanHafez"><img src="https://avatars3.githubusercontent.com/u/19984935?v=4" width="100px;" alt=""/><br /><sub><b>Hafez</b></sub></a><br /><a href="#content-AbdelrahmanHafez" title="Content">🖋</a></td>
  </tr>
  <tr>
    <td align="center"><a href="http://www.ruxandrafediuc.com"><img src="https://avatars1.githubusercontent.com/u/11021586?v=4" width="100px;" alt=""/><br /><sub><b>Ruxandra Fediuc</b></sub></a><br /><a href="#content-ruxandrafed" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/jacklee814"><img src="https://avatars0.githubusercontent.com/u/9951291?v=4" width="100px;" alt=""/><br /><sub><b>Jack</b></sub></a><br /><a href="#content-jacklee814" title="Content">🖋</a></td>
    <td align="center"><a href="https://www.petercarrero.com"><img src="https://avatars0.githubusercontent.com/u/231727?v=4" width="100px;" alt=""/><br /><sub><b>Peter Carrero</b></sub></a><br /><a href="#content-aloyr" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/huhgawz"><img src="https://avatars3.githubusercontent.com/u/369338?v=4" width="100px;" alt=""/><br /><sub><b>Huhgawz</b></sub></a><br /><a href="#content-huhgawz" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/haakonmb"><img src="https://avatars1.githubusercontent.com/u/7099302?v=4" width="100px;" alt=""/><br /><sub><b>Haakon Borch</b></sub></a><br /><a href="#content-haakonmb" title="Content">🖋</a></td>
    <td align="center"><a href="https://jaimemendoza.com/"><img src="https://avatars3.githubusercontent.com/u/5395811?v=4" width="100px;" alt=""/><br /><sub><b>Jaime Mendoza</b></sub></a><br /><a href="#content-jaimemendozadev" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/camerondunford"><img src="https://avatars0.githubusercontent.com/u/840612?v=4" width="100px;" alt=""/><br /><sub><b>Cameron Dunford</b></sub></a><br /><a href="#content-camerondunford" title="Content">🖋</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/shadowspawn"><img src="https://avatars1.githubusercontent.com/u/15719847?v=4" width="100px;" alt=""/><br /><sub><b>John Gee</b></sub></a><br /><a href="#content-shadowspawn" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/aurelijusrozenas"><img src="https://avatars0.githubusercontent.com/u/3273544?v=4" width="100px;" alt=""/><br /><sub><b>Aurelijus Rožėnas</b></sub></a><br /><a href="#content-aurelijusrozenas" title="Content">🖋</a></td>
    <td align="center"><a href="http://aaronshivers.com"><img src="https://avatars2.githubusercontent.com/u/42848750?v=4" width="100px;" alt=""/><br /><sub><b>Aaron</b></sub></a><br /><a href="#content-aaronshivers" title="Content">🖋</a></td>
    <td align="center"><a href="https://tomdoes.tech/"><img src="https://avatars1.githubusercontent.com/u/8683577?v=4" width="100px;" alt=""/><br /><sub><b>Tom Nagle</b></sub></a><br /><a href="#content-tomanagle" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/yvesyao"><img src="https://avatars0.githubusercontent.com/u/7723729?v=4" width="100px;" alt=""/><br /><sub><b>Yves yao</b></sub></a><br /><a href="#content-yvesyao" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/Userbit"><img src="https://avatars1.githubusercontent.com/u/34487074?v=4" width="100px;" alt=""/><br /><sub><b>Userbit</b></sub></a><br /><a href="#content-Userbit" title="Content">🖋</a></td>
    <td align="center"><a href="https://glaucialemos.netlify.com/"><img src="https://avatars0.githubusercontent.com/u/1631477?v=4" width="100px;" alt=""/><br /><sub><b>Glaucia Lemos</b></sub></a><br /><a href="#maintenance-glaucia86" title="Maintenance">🚧</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://twitter.com/koooge"><img src="https://avatars2.githubusercontent.com/u/7419215?v=4" width="100px;" alt=""/><br /><sub><b>koooge</b></sub></a><br /><a href="#content-koooge" title="Content">🖋</a></td>
    <td align="center"><a href="https://twitter.com/michalbiesiada"><img src="https://avatars0.githubusercontent.com/u/18367606?v=4" width="100px;" alt=""/><br /><sub><b>Michal</b></sub></a><br /><a href="#content-mbiesiad" title="Content">🖋</a></td>
    <td align="center"><a href="http://roywalker.me"><img src="https://avatars0.githubusercontent.com/u/611846?v=4" width="100px;" alt=""/><br /><sub><b>roywalker</b></sub></a><br /><a href="#content-roywalker" title="Content">🖋</a></td>
    <td align="center"><a href="https://dangen-effy.github.io/"><img src="https://avatars3.githubusercontent.com/u/23185799?v=4" width="100px;" alt=""/><br /><sub><b>dangen</b></sub></a><br /><a href="#content-dangen-effy" title="Content">🖋</a></td>
    <td align="center"><a href="https://dev.to/mbiesiad"><img src="https://avatars1.githubusercontent.com/u/60202305?v=4" width="100px;" alt=""/><br /><sub><b>biesiadamich</b></sub></a><br /><a href="#content-biesiadamich" title="Content">🖋</a></td>
    <td align="center"><a href="https://tarojsx.github.io"><img src="https://avatars3.githubusercontent.com/u/127009?v=4" width="100px;" alt=""/><br /><sub><b>Yanlin Jiang</b></sub></a><br /><a href="#content-cncolder" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/sanguino"><img src="https://avatars2.githubusercontent.com/u/2077168?v=4" width="100px;" alt=""/><br /><sub><b>sanguino</b></sub></a><br /><a href="#content-sanguino" title="Content">🖋</a></td>
  </tr>
  <tr>
    <td align="center"><a href="https://github.com/MorganGeek"><img src="https://avatars0.githubusercontent.com/u/3721240?v=4" width="100px;" alt=""/><br /><sub><b>Morgan</b></sub></a><br /><a href="#content-MorganGeek" title="Content">🖋</a></td>
    <td align="center"><a href="https://luk4s.dev"><img src="https://avatars0.githubusercontent.com/u/8350985?v=4" width="100px;" alt=""/><br /><sub><b>Lukas Bischof</b></sub></a><br /><a href="https://github.com/goldbergyoni/javascript-testing-best-practices/commits?author=lukasbischof" title="Tests">⚠️</a> <a href="#content-lukasbischof" title="Content">🖋</a></td>
    <td align="center"><a href="https://juanmaruiz.surge.sh"><img src="https://avatars2.githubusercontent.com/u/1837650?v=4" width="100px;" alt=""/><br /><sub><b>JuanMa Ruiz</b></sub></a><br /><a href="#content-JuanMaRuiz" title="Content">🖋</a></td>
    <td align="center"><a href="https://luisangelorjr.com.br"><img src="https://avatars3.githubusercontent.com/u/22268900?v=4" width="100px;" alt=""/><br /><sub><b>Luís Ângelo Rodrigues Jr.</b></sub></a><br /><a href="#content-luisangelorjr" title="Content">🖋</a></td>
    <td align="center"><a href="https://jfernandezpe.wordpress.com/"><img src="https://avatars0.githubusercontent.com/u/12046620?v=4" width="100px;" alt=""/><br /><sub><b>José Fernández</b></sub></a><br /><a href="#content-jfernandezpe" title="Content">🖋</a></td>
    <td align="center"><a href="http://www.linkedin.com/in/AlejandroGutierrezB"><img src="https://avatars3.githubusercontent.com/u/56408597?v=4" width="100px;" alt=""/><br /><sub><b>Alejandro Gutierrez Barcenilla</b></sub></a><br /><a href="#content-AlejandroGutierrezB" title="Content">🖋</a></td>
    <td align="center"><a href="https://github.com/jasonandmonte"><img src="https://avatars1.githubusercontent.com/u/30088000?v=4" width="100px;" alt=""/><br /><sub><b>Jason</b></sub></a><br /><a href="#content-jasonandmonte" title="Content">🖋</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->
<!-- ALL-CONTRIBUTORS-LIST:END -->
