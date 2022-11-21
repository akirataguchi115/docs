---
title: Hello World
intro: 'Следуйте инструкциям в этом упражнении Hello World, чтобы приступить к работе с {% data variables.product.product_name %}.'
versions:
  fpt: '*'
  ghes: '*'
  ghae: '*'
  ghec: '*'
type: quick_start
topics:
  - Pull requests
  - Fundamentals
miniTocMaxHeadingLevel: 3
ms.openlocfilehash: 71278b720bcbfaabc892c396ab7fb558f5309173
ms.sourcegitcommit: fb047f9450b41b24afc43d9512a5db2a2b750a2a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/11/2022
ms.locfileid: '145125864'
---
## Введение

{% data variables.product.product_name %} — это платформа размещения кода для управления версиями и совместной работы. Она позволяет вам и другим пользователям работать над проектами вместе из любого места.

В этом руководстве вы ознакомитесь с основными понятиями {% data variables.product.product_name %}, такими как репозитории, ветви, фиксации и запросы на вытягивание. Вы создадите собственный репозиторий Hello World и ознакомитесь с рабочим процессом запроса на вытягивание в {% data variables.product.product_name %} — популярного способа создания и проверки кода.

В этом кратком руководстве вы выполните следующие действия:

* создадите и используете репозиторий;
* создадите ветвь и будете управлять ею;
* внесете изменения в файл и отправите их в {% data variables.product.product_name %} как фиксации;
* откроете запрос на вытягивание и выполните его слияние.

Для работы с этим руководством вам потребуются [учетная запись {% data variables.product.product_name %}](http://github.com) и доступ к Интернету. Вам не нужно знать, как писать код, использовать командную строку или устанавливать GIT (программное обеспечение для управления версиями, на котором основывается {% data variables.product.product_name %}). Если у вас возникнет вопрос касательно любого из выражений, используемых в руководстве, перейдите к [глоссарию](/get-started/quickstart/github-glossary), чтобы узнать больше о нашей терминологии.

## Создание репозитория

Репозиторий обычно используется для упорядочения одного проекта. Репозитории могут содержать папки и файлы, изображения, видео, электронные таблицы и наборы данных — все, что нужно вашему проекту. Репозитории часто включают файл _сведений_ о проекте. Файлы _сведений_ создаются на языке Markdown в виде обычного текста. Эта [памятка](https://www.markdownguide.org/cheat-sheet/) поможет вам приступить к работе с синтаксисом Markdown. {% data variables.product.product_name %} позволяет добавить файл _сведений_ одновременно с созданием репозитория. {% data variables.product.product_name %} также предлагает другие распространенные компоненты, такие как файл лицензии, но пока вам выбирать их не нужно.

В репозитории `hello-world` можно хранить идеи и ресурсы, а также делиться ими и обсуждать их с другими пользователями.

{% data reusables.repositories.create_new %}
1. В поле **Имя репозитория** введите `hello-world`.
2. В поле **Описание** напишите краткое описание.
3. Выберите параметр **Добавить файл сведений**.
4. Выберите, будет ли репозиторий **общедоступным** или **частным**.
5. Щелкните **Создать репозиторий**.

   ![Создание репозитория Hello World](/assets/images/help/repository/hello-world-repo.png)

## Создание ветви

Ветвление позволяет одновременно иметь разные версии репозитория.

По умолчанию репозиторий имеет одну ветвь с именем `main`, которая считается главной. В репозитории можно создать дополнительные ветви на основе `main`. Ветви можно использовать для одновременного использования разных версий проекта. Это полезно, если нужно добавить в проект новые функции, не изменяя основной источник кода. Работа, выполняемая в других ветвях, не будет отражаться в главной ветви, пока вы не выполните ее слияние (этот процесс будет рассмотрен далее в руководстве). Ветви можно использовать для проведения экспериментов и внесения изменений перед их фиксацией в `main`.

Когда вы создаете ветвь на основе ветви `main`, создается копия или моментальный снимок `main` на этот момент времени. Если кто-то другой внес изменения в ветвь `main`, пока вы работали со своей ветвью, вы можете вытянуть эти изменения.

На этой схеме показано следующее:

* ветвь `main`;
* новая ветвь с именем `feature`;
* путь, который проходит `feature` до слияния с `main`.

![Схема ветвления](/assets/images/help/repository/branching.png)

Приходилось ли вам сохранять разные версии файла? Например, так:

* `story.txt`
* `story-edit.txt`
* `story-edit-reviewed.txt`

Ветви в репозиториях {% data variables.product.product_name %} служат аналогичным целям.

На {% data variables.product.product_name %} разработчики, авторы и дизайнеры используют ветви для хранения исправлений ошибок и результатов работы над функциями отдельно от ветви `main` (рабочей ветви). Когда изменение готово, производится слияние ветви с `main`.

### Создание ветви

1. В репозитории `hello-world` перейдите на вкладку **Код**.
2. Откройте раскрывающийся список в верхней части списка файлов, где указано **main**.
   ![Меню ветвей](/assets/images/help/branch/branch-selection-dropdown.png)
4. В текстовом поле введите имя ветви `readme-edits`.
5. Нажмите кнопку **Создать ветвь readme-edits на основе main**.

![Меню ветвей](/assets/images/help/repository/new-branch.png)

Теперь у вас две ветви: `main` и `readme-edits`. Сейчас они выглядят совершенно одинаково. Далее вы добавите изменения в новую ветвь.

## Внесение и фиксация изменений

После создания ветви на предыдущем шаге в {% data variables.product.product_name %} открылась страница кода для новой ветви `readme-edits`, которая является копией ветви `main`.

Вы можете вносить изменения в файлы в репозитории и сохранять их. В {% data variables.product.product_name %} сохраненные изменения называются фиксациями. С каждой фиксацией связано сообщение о фиксации, в котором объясняется, почему было внесено данное изменение. В сообщениях о фиксациях ведется история изменений, чтобы другие участники могли понять, что вы сделали и почему.

1. В созданной ветви `readme-edits` щелкните файл _README.md_.
2. Щелкните {% octicon "pencil" aria-label="The edit icon" %}, чтобы изменить файл.
3. В редакторе напишите немного о себе. Попробуйте использовать различные элементы Markdown.
4. В поле **Фиксация изменений** напишите сообщение о фиксации с описанием изменений.
5. Щелкните **Зафиксировать изменения**.

   ![Пример фиксации](/assets/images/help/repository/first-commit.png)

Эти изменения будут внесены только в файл сведений в вашей ветви `readme-edits`, поэтому теперь ее содержимое отличается от `main`.

## Открытие запроса на вытягивание

Теперь, когда у вас есть изменения в ветви, созданной на основе `main`, можно открыть запрос на вытягивание.

Запросы на вытягивание — это основа совместной работы на {% data variables.product.product_name %}. Когда вы открываете запрос на вытягивание, вы предлагаете свои изменения и просите, чтобы кто-нибудь проверил результаты вашей работы, извлек их и выполнил слияние со своей ветвью. В запросах на вытягивание показаны различия в содержимом двух ветвей. Изменения, дополнения и исключения отображаются разными цветами.

Сразу после фиксации вы можете открыть запрос на вытягивание и начать обсуждение, даже если код еще не завершен.

Используя функцию {% data variables.product.product_name %} `@mention` в сообщении с запросом на вытягивание, вы можете запросить отзывы от конкретных пользователей или команд независимо от того, где они находятся физически — этажом ниже или на другом конце света.

Вы даже можете открывать запросы на вытягивание в собственном репозитории и выполнять их слияние самостоятельно. Это отличный способ ознакомиться с процессом работы на {% data variables.product.product_name %} перед работой над крупными проектами.

1. В репозитории `hello-world` перейдите на вкладку **Запросы на вытягивание**.
2. Щелкните **Новый запрос на вытягивание**.
3. В поле **Примеры сравнения** выберите созданную вами ветвь `readme-edits`, чтобы сравнить ее с `main` (исходной ветвью).
4. Просмотрите различия на странице сравнения и убедитесь в том, что они готовы к отправке.

   ![Пример различия](/assets/images/help/repository/diffs.png)

5. Щелкните **Создать запрос на вытягивание**.
6. Укажите заголовок запроса на вытягивание и напишите краткое описание изменений. Вы можете добавлять эмодзи и перетаскивать изображения и GIF-файлы.
7. При необходимости справа от названия и описания щелкните {% octicon "gear" aria-label="The Gear icon" %} рядом с элементом **Рецензенты**, **Уполномоченные**, **Метки**, **Проекты** или **Веха**, чтобы добавить любые из этих элементов в запрос на вытягивание. Пока их добавлять не нужно, но эти параметры обеспечивают различные способы совместной работы с помощью запросов на вытягивание. Дополнительные сведения см. в разделе [Сведения о запросах на вытягивание](/pull-requests/collaborating-with-pull-requests/proposing-changes-to-your-work-with-pull-requests/about-pull-requests).
7. Щелкните **Создать запрос на вытягивание**.

Теперь участники совместной работы могут просматривать ваши изменения и вносить предложения.

## Слияние запроса на вытягивание

На этом последнем шаге вы выполните слияние ветви `readme-edits` с ветвью `main`.  После слияния запроса на вытягивание изменения в вашей ветви `readme-edits` будут включены в `main`.

Иногда запрос на вытягивание может вносить изменения в код, конфликтующие с существующим кодом в `main`. Если есть конфликты, {% data variables.product.product_name %} оповещает вас об этом и блокирует слияние до их устранения. Вы можете выполнить фиксацию, которая устраняет конфликты, или использовать комментарии в запросе на вытягивание, чтобы обсудить конфликты с участниками команды.

При выполнении этого пошагового руководства конфликтов не должно быть, поэтому ваша ветвь готова к слиянию с главной.

1. Нажмите кнопку **Слияние запроса на вытягивание**, чтобы объединить изменения с `main`.
  ![Снимок экрана: кнопка слияния.](/assets/images/help/pull_requests/pullrequest-mergebutton.png)
2. Щелкните **Подтвердить слияние**. Вы получите сообщение о том, что запрос был успешно объединен и закрыт.
3. Щелкните **Удалить ветвь**. Теперь, когда запрос на вытягивание объединен и изменения включены в `main`, вы можете спокойно удалить ветвь `readme-edits`. Чтобы внести дополнительные изменения в проект, вы всегда можете создать новую ветвь и повторить этот процесс.

## Дальнейшие действия

В этом руководстве вы узнали, как создать проект и отправить запрос на вытягивание на {% data variables.product.product_name %}.

Вы выполнили следующие задачи:

* создали репозиторий с открытым кодом;
* создали ветвь и управляли ею;
* изменили файл и зафиксировали изменения в {% data variables.product.product_name %};
* открыли запрос на вытягивание и выполнили его слияние.

Откройте свой профиль {% data variables.product.product_name %}, и вы увидите, что на графике участия отразились результаты вашей работы.

Дополнительные сведения о возможностях ветвей и запросов на вытягивание см. в разделе [Процесс работы в GitHub](/get-started/quickstart/github-flow). Дополнительные сведения о начале работы с {% data variables.product.product_name %} см. в других [кратких руководствах](/get-started/quickstart).