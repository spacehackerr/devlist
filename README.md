# devlist
Useful packages, links and materials

## Содержание
- [**PHP:**](#PHP)
    - [ ] [Packages](#Packages-)
    - [ ] [Static analysis tools](#Static-analysis-tools-)

- [**Common useful links:**](#Common-useful-links-)
    - [ ] [Алгоритмы](#Алгоритмы-)

## PHP [&uarr;](#Содержание)

#### Articles [&uarr;](#Содержание)
- https://phptherightway.com/
- https://riptutorial.com/php/example/5441/reading-a-large-file-with-a-generator

#### Packages [&uarr;](#Содержание)
Пакеты, с которыми я столкнулся в ходе разработки

- markrogoyski/math-php (Powerful Modern Math Library for PHP)
- zircote/swagger-php
- php-di/php-di
- guzzlehttp/guzzle
- monolog/monolog
- twig/twig
- webmozart/assert
- swiftmailer/swiftmailer
- ramsey/uuid (uuid generator)

##### For require-dev
- phpunit/phpunit
- fzaninotto/faker

##### Static analysis tools
- sensiolabs-de/deptrac ( static code analysis tool that helps to enforce rules for dependencies between software layers)
- phpstan - PHPStan finds bugs in your code without writing tests
- psalm - static analysis tool for PHP that helps you identify both obvious and hard-to-spot bugs in your code.

##### Profiling tools

- first, collect app metrics for monitoring important buisness hotspots

- pinba - (for all prod req) сервис для получения realtime
-статистики от работающих приложений без накладных расходов на её сбор
    - https://github.com/tony2001/pinba_engine
    - https://github.com/badoo/pinba2
    - https://habr.com/ru/company/badoo/blog/319934/
    - https://habr.com/ru/company/badoo/blog/149695/
    
- xhprof (for small 0.1 % of requests)  (hpprofiler, xshprof, lifeprof)
- https://github.com/NoiseByNorthwest/php-spx
- https://github.com/blackfireio/php-sdk

##### PSR
- php-fig/fig-standards
- psr/log

#####  Template engines etc 
- cebe/markdown
- twig
- ezyang/htmlpurifier

##### For math
- brick/math A PHP library to work with arbitrary precision numbers.

##### Algorithms libs
- bandwidth-throttle/token-bucket - Implementation of the Token Bucket algorithm in PHP.

##### For phpstorm
- brendt/phpstorm-photon-theme

----
## Symfony

### Статьи

- http://ocramius.github.io/doctrine-best-practices/#/10 
- https://medium.com/phpyh/правильная-регистрация-консольных-команд-в-symfony-di-f7536c254926
 правильная регистрация консольных команд (lazy)

### Примеры (репозитории):

- https://github.com/symfony/demo

- рейтинг в гитхабе по языку php (можно много интересного найти)
  https://github.com/search?q=stars%3A%3E1000+language%3APHP+state%3Aopen+language%3APHP&type=Repositories

- Шаблон апи на симфони 4 (регистрация/авторизация/профиль юзера):
  https://github.com/tarlepp/symfony-flex-backend
  
- Простенький сайтик для шаринга фото на симфони 5 пхп 7.4 с попыткой отказаться от геттеров и сеттеров:
  https://github.com/svbackend/cropofil
  
- Апи на симфе 4, позволяет получить список фиььмов и рекомендации к понравившимся:
  https://github.com/svbackend/my-art-lib


Полезные курсы:

- от елисеева
- https://symfonycasts.com/  (или Knpuniversity)

Топ компоненты, бандлы и пакеты:

- symfony/notifier
- symfony/messenger
 - Symfony/mailer
 - https://github.com/lexik/LexikJWTAuthenticationBundle
- EasyAdminBundle
- https://gist.github.com/fesor/fb1d53e8e4e427c59b930559da83d9a3 - RequestObjectResolver, для валидации DTO
 из реквеста (до попадания в контроллер)
- https://github.com/nelmio/NelmioCorsBundle - Adds CORS (Cross-Origin Resource Sharing) headers support
(статья про CORS в symfony https://blog.liplex.de/symfony-cors-listener/)

Bundles for dev:
- dmaicher/doctrine-test-bundle -  bundle to isolate your app's doctrine database tests and improve the test performance
- https://github.com/paratestphp/paratest -  Parallel testing for PHPUnit
- https://github.com/lchrusciel/ApiTestCase - решение по интеграционному тестированию внешних апи

## Архитектуры (DDD, Clean Architecture, Hexagonal)

Предметно-ориентированное проектирование (Domain-driven design, DDD
) — это набор принципов и схем, направленных на создание оптимальных  систем объектов. 
Сводится к созданию программных абстракций, которые называются моделями предметных областей. 
В эти модели входит бизнес-логика, устанавливающая связь между реальными условиями области применения продукта и кодом.

Книги:
- Domain-Driven Design in PHP
- Domain-Driven Design (Eric Evans) - основная книга

Статьи по Hexagonal
- https://www.thinktocode.com/2018/07/19/ports-and-adapters-architecture/

Статьи по DDD
- https://matthiasnoback.nl/2018/06/doctrine-orm-and-ddd-aggregates/
- https://matthiasnoback.nl/2018/03/ormless-a-memento-like-pattern-for-object-persistence
/ интересная статья о сохранении моделей без орм (через снепшоты внутреннего состояния)

Видео:
- https://www.youtube.com/watch?v=fWU8ZK0Dmxs - Уди рассказывает про race condition
довольно часто важные бизнес правила будут в перемешку с правилами, нарушения которых не приводят к проблемам (типа лайкнуть архивные баннер).
Нужно быть аккуратным с защитными условиями бизнес правил в сущностях, для которой может быть гонка.
Есть важные правила которые нельзя нарушать. Которые например на тебя налагает не менеджер или там продукт оунер а законодательство страны в которой твой продукт работает
Если "а что будет, если я выключил промокод, а в это время его применили" - это не критично.



Проектирование без учета ORM
Когда вы узнаете, как проектировать доменные объекты с использованием шаблонов, управляемых доменом, 
вам сначала нужно избавиться от идеи, что проектируемые объекты когда-либо будут сохраняться

When to use - if you have complicated and everchanging business rules

BUT - if you have  simple not-null checks  and a couple of sums to calculate, a Transaction script is better bet


#### Модель
Модель – это всеохватывающее определение для всего доменного кода.
Как "модель солнечной системы" и "модель киоска с шаурмой". С кучей сущностей, расчётов и правил внутри. А не какой-то один класс Model.
"Доменная модель" подразумевает, что ты разбираешься с доменом, а не просто объектики лепишь. Основная суть в том что бы понять какие у тебя есть важные правила и как реагировать на них. 

Во многих фреймворках в отличие от этого класс Model определяет "модель данных БД",  "модель ввода" или что-то ещё мелкое.
В Eloquent это "модель данных БД". В Yii это "модель ввода с валидацией".

#### Entities 
Cодержат бизнес-правила, независимые от приложения. И они не просто объекты с данными.
Entities могут содержать ссылки на объекты с данными, но основное их назначение в том, чтобы реализовать методы бизнес-логики, которые могут использоваться в различных приложениях.

An object model of the domain that incorporates both behavior and data.
You’ll find objects that mimic  the data in  the business  and objects  that  capture  the  rules  the businessuses.

Анемик модели это хорошо и норм, просто это не модели а структуры
если вам надо сохранить и считать данные  (CRUD) а логики не надо то структура самое то

О анемик модель vs reach models
- https://thevaluable.dev/anemic-domain-model/
- http://ocramius.github.io/doctrine-best-practices/#/26
- https://habr.com/ru/company/mobileup/blog/335382/ - статья по clean architecture 

-------------

#### Clean Architecture 

- https://softwareengineering.stackexchange.com/questions/357052/clean-architecture-use-case-containing-the-presenter-or-returning-data

About communication Use case adn  presenter?

- https://softwareengineering.stackexchange.com/questions/303478/uncle-bobs-clean-architecture-an-entity-model-class-for-each-layer/303480#303480
 
- An entity/model class for each layer https://habr.com/ru/company/mobileup/blog/335382 
(пункт Заблуждение: Обязательность маппинга между слоями).
 Если у вас сложное приложение с логикой бизнеса и логикой приложения, и/или разные люди работают над разными слоями, то лучше разделять данные между слоями (и маппить их). 
 Также это стоит делать, если серверное API корявое. Но если вы работаете над проектом один, и это простое приложение, то не усложняйте лишним маппингом.


-------------
#### CQRS

Материал:
- https://martinfowler.com/bliki/CQRS.html
- https://www.youtube.com/watch?v=RfnySciLUhc&feature=youtu.be

Read and write models

- Write models - Domain models (ak DDD) domain models (агрегаты, сущности, vo) держим логику. Данные группируем по сущностям так, как удобно для логики
- Read models. Используются для фронта например (списков, форм и тп)
Для чтения юзаем отдельные простые структуры данных. Заполняем их напрямую из результатов запросов (без использования write models)


Агрегаты строишь вокруг инвариантов, а не вокруг "групп" данных. 
На агрегатах у тебя только "командные" методы с :void
В самом простом случае на чтение ты данные забираешь при помощи DBAL (ReadModel) из таблицы напрямую, 
минуя сам агрегат. В сложном — EventSourcing и проекции, тогда можно +- любые данные на чтение
собирать на базе событий. Но EventSourcing лучше пробовать не в перую очередь и только когда поймёшь, 
что он реально нужен проекту и что ты понимаешь, что ты делаешь.

в dto вместо геттеров и сеттеров публичные свойства с @psalm-immutable.
в модель тоже геттеры/сеттеры не нужны никогда. 
в value object-ах лучше делать toString`/`to*. ну и всё)

доменные события — это внешний контракт агрегата. его API. 
вместо геттеров ты получаегшь куда более мощную информацию об изменениях


- https://github.com/prooph/event-sourcing - Provides basic functionality for event sourced aggregates
 (чтобы самому не реализовывать. Однако, добавляет зависимость в доменный слой)
 
Пример
- https://github.com/dmitrymendelson/cqrs_es_example (dirty example of cqrs)

#### Про DTO

Dto
 нужны только для того, чтобы передавать данные между уровнями. Например:
  - передача данных с уровня инфраструктуры в уровень сервиса (или домена).
  - возврат данных с read model. Для того, чтобы отобразить данные, не нужно подымать сложные domain
   модели с поведением.
   
Чтобы данные не передавать массивом, создается объект с public полями (ide
 подскажет поля объекта при использовании и тип, при наличии phpdoc).

- это грубо говоря массив, который мы перекидываем из внешнего слоя инфраструктуры в слой приложения (или домена).
- объект с заранее известными полями без какого-либо поведения
- в dto вместо геттеров и сеттеров публичные свойства с @psalm-immutable.
- без валидации и контроля типов (кроме psalm).
Необходимые проверки на типы и корректность данных должна выполнять использующая сторона - сервисы, репозитории, ентити.

- как правило, для dto
 справедливо, что он должен инстанцироваться с заполнением определенных полей. Нужно добавить конструктор и принимать эти обязательные поля, 
а остальные поля заполнять из реквеста (формы в контроллере) путем присваивания публичных полей (или автоматически из валидатора форм).
Но в общем, dto после создания не надо модифицировать, это что-то вроде сообщения


Best way to write DTO - constructor + public properties + Psalm @immutable to control for access.
then you do an optimal class and check immutability in ci instead of runtime
​just write once from constructor, that's it
all modifications with "with" methods + cloned return to keep immutability
but DTO generally should not be modified, it's like a message


Иммутабельность Это св-во VO
Например, есть class UrlValueObject = при своении в конструкторе можем чекать все что надо, дальше мы уже можем преедавать
урл не как строку, а как VO. И он immutable. Для изменения нужно создать новый инстанс объекта с нужным значением


------
## OOP

- https://oopru.github.io/

Статьи:
- https://martinfowler.com/bliki/TellDontAsk.html


## SOLID

### L - LSP -
LSP - Функции, которые используют базовый тип, должны иметь возможность использовать подтипы базового типа, не зная об этом. (c) вики (с) Роберт С. Мартин

- https://wiki.php.net/rfc/covariant-returns-and-contravariant-parameters
- https://php.watch/articles/php-lsp
- https://madewithlove.com/liskov-substitution-principle-explained/
- https://dev-gang.ru/article/solid-%C2%ABl%C2%BB-princip-podstanovki-barbary-liskov-zbmdty8bnw/

Основные моменты
- Глвные моменты: Пред и пост условия. Пред условия не могут быть усилены, пост условия не могут быть ослаблены 
    - 1 Ковариантность возвращаемого значение
    - 2 Контрвариантность принимаемого значения
    - 3 
    No new exceptions should be thrown by methods of the subtype, except where those exceptions are
 themselves subtypes of exceptions thrown by the methods of the supertype.
"Никакие новые исключения не должны создаваться методами подтипа, за исключением тех случаев, когда сами эти исключения являются подтипами исключений, создаваемых методами супертипа"
The overriden methods in child classes should throw the same or more specialized exceptions that can be thrown in the parent class.

- (для php) Сигнатуры методов должны совпадать: можно расширить список параметров необязательным аргументов
- (для php) инвариантность типа параметра в наследнике
- (для php) хотя аргументы методов в подтипах всегда должны быть контравариантными, аргументы в методах подтипов __construct
 () не обязательно должны быть контравариантными в php.

Ковариантность - сужение типов (более специфичный тип). Для возвращаемого типа метода в дочернем классе

    class Image {}
     class JpgImage extends Image {}
     
     class Renderer {
          public function render(): Image;
     }
     
     class PhotoRenderer {
         public function render(): JpgImage;
     }
 
 Еще пример (сразу ковариантонсть по возврат типу и контрвариантности по принимаемому аргументу)
 
     class Foo {
         public function process(int|float $value): string|int;
     }
     
     class Bar extends Foo {
         public function process(int|float|string $value): int;
     }


Контрвариантность - расширение типов (более абстрактный тип) в методе наследника. Он должен принять все параметры, которые может принять родитель

Про нарушение в конструкторе

    abstract class CustomFieldDefinition
    {
        public function __construct(AccountId $accountId) { ... }
    }
    
    // Example of a Liskov Substitution Principle violation but allowed by PHP:
    final class MultipleChoiceFieldDefinition extends CustomFieldDefinition
    {
        public function __construct(
            AccountId $accountId,
            array $choices
        ) {
            // By adding an extra required argument, we just broke the method calls 
            // of any code trying to construct instances of CustomFieldDefinition.
        }
    }

So to prevent this from becoming an issue, we closed off the __construct method from being modified by making it final.
    
    abstract class CustomFieldDefinition
    {
        final public function __construct(AccountId $accountId) { ... }
    }
    
Another alternative would be making it private and having a static create(...): CustomFieldDefinition method on CustomFieldDefinition instead.

    abstract class CustomFieldDefinition
    {
        private function __construct(AccountId $accountId) { ... }
    
        public static function create(
            AccountId $accountId, 
        ): CustomFieldDefinition {
            // We can still use the constructor here because we have access to any private
            // methods and properties defined in this class, including __construct().
            return new static($accountId, $variableName);
        }
    }

##


## Common useful links

- zualex/devmap - Карта развития веб-разработчика
- jlevy/the-art-of-command-line - The Art of Command Line
- tlbootcamp/tlroadmap - Карта навыков и модель развития тимлидов
- https://habr.com/ru/search/?target_type=posts&q=тимлид&order_by=relevance - статьи на хабре по тимлидству

## Полезные инструменты

- https://github.com/centrifugal/centrifugo - Scalable real-time messaging server in language-agnostic way.

Можно юзать для чатов, как микросервис доставки сообщений на клиент.

- https://github.com/walkor/Workerman - An asynchronous event driven PHP socket framework. Supports HTTP, Websocket, SSL and other custom protocols
- https://github.com/php-enqueue/enqueue-dev (если не юзать messanger symfony) - Предоставляет общий способ для программ создавать, отправлять, читать сообщения.


------
## СУБД

Основные положения Vertica 
https://docs.google.com/document/d/1gSRmERjHqVBRIU6OpmvAPWOYBZlGHxsrWg4CXLiq5U0/edit

#### Партицирование

- Партицирование (секционирование) - разделение таблиц (и тд) на отдельные логические части по определенными критериям (с раздельными параметрами физического хранения). В рамках одной ноды.

Используется в целях повышения управляемости, производительности и доступности для больших баз данных.
Возможные критерии разделения данных, используемые при секционировании — по предопределённым диапазонам значений, по спискам значений, при помощи значений хеш-функций; в некоторых случаях используются другие варианты. Под композитными (составными) критериями разделения понимают последовательно применённые критерии разных типов.

В отличие от Шардинга (сегментирования), где каждый сегмент управляется отдельным экземпляром СУБД, и используются средства координации между ними (что позволяет распределить базу данных на несколько вычислительных узлов),
при секционировании доступ ко всем секциям осуществляется из единого экземпляра СУБД (или симметрично из любого экземпляра кластерной СУБД, такого, как Oracle RAC).

   - вертикальное партицирование - поколоночно режем большую таблицу
   - горизонтальное - режим построчно в отдельные таблицы (проекции и т.д.) в рамках одной и тойже схемы (сервера, ноды). Если на разных нодах, то это уже шардинг
    

Файл с данными таблицы разрезается по какому-то условию на несколько не больших файлов — партиций.
Для случая с логами разумно партиционировать таблицы по полю, содержащему даты события. 
Часто бывает разумно резать таблицу на partition по году по месяцу или по дням месяца/недели.

- Шардинг (Сегментирование) (горизонтальное партиционирование) - разделение (партиционирование) базы данных на отдельные части так,
 чтобы каждую из них можно было вынести на отдельный сервер. Этот процесс зависит от структуры Вашей базы данных и выполняется прямо в приложении в отличие от репликации:
 
    - вертикальный - это выделение таблицы или группы таблиц на отдельный сервер
    - горизонтальный - это разделение одной таблицы на разные сервера. Это необходимо использовать для огромных таблиц, которые не умещаются на одном сервере.
    
    https://ruhighload.com/Шардинг+и+репликация
    
- Репликация - полная копия хранимых объектов (таблицы, представления либо все бд)


-----

## REST, SOAP ...


