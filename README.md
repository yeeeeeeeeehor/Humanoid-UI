# Введение

**Готовая для сборки Candy Machine UI отзывчивый пользовательский интерфейс, который можно легко настроить за 5 мин.**

**Актуальный с последними улучшениями Metaplex**

Все функциональные возможности Candy Machine V2 реализованы, автоматически определяются и поддерживаются в актуальном состоянии:

 - Публичный монетный двор (с обратным отсчетом, когда дата в будущем)
 - Поддержка Civic
 - Белый список
 - Предпродажа
 - Дата конца / Номер окончания (endSettings)
 - SPL-токен для монетного двора
 - последнее обновление MCC от Metaplex от 01.06.2022

<a href="https://ibb.co/wrk92z6"><img src="https://i.ibb.co/LhFLsZp/Screenshot-from-2022-06-01-19-38-15.png" alt="Screenshot-from-2022-06-01-19-38-15" border="0"></a>

### Поддерживаемые кошельки

![Supported Wallets](https://i.ibb.co/DC6Wt66/wallets.png)

Инструкции по настройке Candy Machine V2 см. в документации Metaplex [here](https://docs.metaplex.com/candy-machine-v2/Introduction)

## Сборка Vercel в один клик 

Это решение позволяет одним щелчком мыши клонировать данный проект на GitHub и развернуть prod-пакет на Vercel.
Вашей единственной задачей будет настройка вашего форка этого проекта на GitHub и фиксация обновлений.
Vercel будет автоматически развертывать новые prod-пакеты для каждого нового коммита.

[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2FFulgurus%2Fcandy-machine-v2-responsive-ui&env=REACT_APP_CANDY_MACHINE_ID,REACT_APP_SOLANA_NETWORK,REACT_APP_SOLANA_RPC_HOST&envDescription=Populate%20REACT_APP_CANDY_MACHINE_ID%20with%20your%20candy%20machine%20public%20key%2C%20REACT_APP_SOLANA_NETWORK%20with%20the%20solana%20network%20(devnet%2Fmainnet-beta)%20and%20REACT_APP_SOLANA_RPC_HOST%20with%20the%20RPC%20URL%20(example%20for%20devnet%20%3A%20https%3A%2F%2Fapi.devnet.solana.com)&envLink=https%3A%2F%2Fdocs.solana.com%2Fcluster%2Frpc-endpoints%23mainnet-beta&demo-title=My%20Demo%20Mint%20Page&demo-description=A%20one-click%20generated%20solana%20minting%20responsive%20website.&demo-url=https%3A%2F%2Fwww.mintgatsbyclub.net%2F&demo-image=https%3A%2F%2Fi.ibb.co%2FyPrdrrF%2Fcmv2.png)

## Подготовка к работе

### Предварительные условия

**Необходим NODEJS Версии <= 16 (версия 17 не поддерживается)**.

* Загрузите редактор кода, например Visual Studio Code.

* Убедитесь, что у вас установлены `nodejs` и `yarn`. Рекомендуемая версия `nodejs` - 16.

* Следуйте инструкциям [here](https://docs.solana.com/cli/install-solana-cli-tools) Для установки набора инструментов командной строки Solana.

* Установка пакета командной строки в настоящее время является сложной задачей, которая со временем будет упрощена.

### Установка

#### 1. Сделайте Форк данного репозитория и клонируйте его. Пример:

```
git clone https://github.com/yeeeeeeeeehor/Humanoid-UI.git
```

#### 2. Определите переменные окружения (.env файл)

Переименуйте этот `.env.example` file в главной директории в `.env` и обновите следующие переменные в `.env` файле:

```
REACT_APP_CANDY_MACHINE_ID=__PLACEHOLDER__
```
Установите __PLACEHOLDER__ в качестве публичного ключа вашей Candy Machine, который вы получите после загрузки и создания Candy Machine в проекте Metaplex. 
Вы можете узнать это значение из файла `.cache/temp.json` вашего проекта Metaplex. 
Этот файл создается при выполнении команды `ts-node candy-machine-v2-cli.ts upload ...`.
```
REACT_APP_SOLANA_NETWORK=devnet
```

Определяет сеть Solana, к которой вы хотите подключиться. Варианты: `devnet`, `testnet` и `mainnet`.

```
REACT_APP_SOLANA_RPC_HOST=https://api.devnet.solana.com
```

Этот параметр определяет RPC-сервер, через который ваше веб-приложение будет получать доступ к сети Solana.


Если вы используете пользовательский SPL-токен для MINT, вам нужно установить два дополнительных параметра среды:


```
REACT_APP_SPL_TOKEN_TO_MINT_NAME=
```

Имя SPL-токена для отображения рядом с ценой.

```
REACT_APP_SPL_TOKEN_TO_MINT_DECIMALS=9
```

Десятичные числа Spl-токена были определены при его создании с помощью параметра --decimals. 
Если вы не использовали этот параметр, то по умолчанию ваш SPL-токен будет иметь 9 десятичных знаков.

Больше информации о SPL-токене вы можете найти тут : https://spl.solana.com/token

#### 3. Сборка проекта и тестирование. Перейдите в корневой каталог проекта и введите команды :

Установка зависимостей :

```
yarn install
```

Чтобы протестировать приложение в локальном режиме разработки (localhost:3000) :

```
yarn start
```

И собираем рабочий пакет (созданный в папке build проекта) :

```
yarn build
```

#### 4. Настройка пользовательского интерфейса сайта UI :

##### 4.1 `App.css` : обновите 5 основных переменных CSS с помощью ваших пользовательских цветов:

```
:root {
  --main-background-color: #343A50;
  --card-background-color: #804980;
  --countdown-background-color: #433765;
  --main-text-color:#F7F6F4;
  --title-text-color:#3CBA8B;
}
```

Затем обновите фоновое изображение, перезаписав свой собственный фоновый PNG-файл в папке src/img.

##### 4.2 `public` folder :

- Обновите существующие изображения демо-версии preview (preview.gif, logo.png) своими собственными изображениями в папке проекта `public`. Убедитесь, что они имеют одинаковые названия.
- 
- Добавьте ваш собственный заголовок сайта в `index.html` : `<title>Humanoid</title>`.

##### 4.3 `Home.tsx` :

Прокрутите вниз до строки 703 (`return <main> [...]`) и начните обновлять все заголовки/меню/текст/изображения/текст... по желанию во всем блоке React HTML.

Вот и все! Наслаждайтесь вашей прекрасной конфетной машиной :)


