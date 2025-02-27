# Управление организациями в {{ tracker-name }}

В {{ tracker-name }} для управления пользователями используются организации. Доступны два вида организаций: [{{ org-full-name }}](../organization/) и [{{ ya-360 }}]({{ link-ya-360 }}). В дальнейшем появится возможность использовать одновременно оба сервиса.

## Сравнение {{ ya-360 }} и {{ org-full-name }} {#features}

Чтобы вам было проще выбрать подходящий сервис, мы подготовили сравнение возможностей {{ ya-360 }} и {{ org-full-name }}.

#|
|| | **{{ ya-360 }}** | **{{ org-full-name }}** ||
|| **Тарификация** | 

С 17 апреля 2023 года бесплатная версия {{ ya-360 }} будет отключена: сервисы станут [платными]({{ link-ya-360-notfree }}).
Использование {{ tracker-name }} оплачивается [отдельно](./pricing.md).

|

Сервис {{ org-full-name }} полностью бесплатный. 
Использование {{ tracker-name }} оплачивается [отдельно](./pricing.md).

||
|| **Аккаунты сотрудников** | Аккаунты на Яндексе или на вашем корпоративном домене. | Аккаунты на Яндексе и на доменах, делегированных в {{ ya-360 }}. ||
|| **Единый вход (SSO)** | Поддерживается. [Узнать больше]({{ link-ya-360-sso }}) | Поддерживается. [Узнать больше](../organization/concepts/add-federation.md) ||
|| **Количество организаций у одного пользователя на домене {{ ya-360 }}** | Пользователи с аккаунтами на домене могут состоять только в организации, для которой этот домен подключен. | Пользователи с аккаунтами на домене могут состоять в любых организациях. ||
|| **Подключение домена** | Можно [подключить](https://yandex.ru/support/business/domains/add-domain.html) домен для организации. | Подключение домена недоступно. ||
|| **Группы** | Поддерживаются [иерархические подразделения]({{ link-ya-360-units }}) и [одноуровневые группы]({{ link-ya-360-groups }}). | Можно настраивать только [одноуровневые группы](../organization/operations/manage-groups.md) пользователей. ||
|| **Права администратора организации** | Администратор {{ ya-360 }} становится администратором {{ tracker-name }}. | В марте администратор {{ org-full-name }} будет считаться также администратором в {{ tracker-name }}. Также можно будет назначать администраторов, [выдавая](../organization/security/index.md) им роль `tracker.admin`. ||
|| **Дополнительные возможности** | [Сервисы {{ ya-360 }}]({{ link-ya-360-services }}) | [Сервисы {{ yandex-cloud }}]({{ link-cloud-services }}) ||
|#

## Выбрать организацию для {{ tracker-name }} {#connect}

С 17 апреля 2023 года вы сможете выбирать, какой сервис использовать:

* Чтобы продолжить работать в обоих сервисах, потребуется оплатить использование {{ ya-360 }} в соответствии с [выбранным тарифом]({{ link-ya-360-tariffs }}). Использование {{ tracker-name }} оплачивается [отдельно](./pricing.md). 

   {% note info %}

   Если оплата за использование {{ ya-360 }} не внесена, {{ tracker-name }} продолжит работать, однако вы не сможете редактировать состав участников организации.

   {% endnote %}

* Чтобы выбрать для работы только {{ org-full-name }}, в интерфейсе {{ tracker-name }} потребуется отключить организацию {{ ya-360 }}.

   {% note info %}

   Если ваша организация работает только в сервисе {{ ya-360 }}, вы сможете также подключить {{ org-full-name }}.

   {% endnote %}

* Чтобы выбрать для работы только {{ ya-360 }}, в интерфейсе {{ tracker-name }} потребуется отключить организацию {{ org-full-name }}.

## Сменить {{ ya-360 }} на {{ org-full-name }} {#reconnect}

Администратор организации {{ ya-360 }} может сменить организацию для {{ tracker-name }} и перейти на {{ org-full-name }}.

* Если у вас уже подключена организация {{ org-full-name }}, переход на нее будет выполнен автоматически, никаких дополнительных действий не требуется. Проверить подключение можно на странице ![](../_assets/tracker/svg/admin.svg) **Администрирование** → ![](../_assets/tracker/svg/organizations.svg) [**{{ ui-key.startrek.ui_Common_smart-components_page-admin_PageAdmin.menu-item-orgs }}**]({{ link-tracker }}admin/orgs).

* Если у вас есть организация {{ org-full-name }}, на которую вы хотите перейти, но которая подключена к другому {{ tracker-name }}, {{ wiki-name }} или {{ forms-name }}, обратитесь в [службу поддержки](troubleshooting.md). Это связано с тем, что все данные при переключении будут удалены.

Инструкцию ниже может выполнить только администратор организации {{ ya-360 }}, и он же станет администратором организации {{ org-full-name }}.

1. Если у вас еще нет организации в {{ org-full-name }}, создайте ее по [инструкции](../organization/operations/enable-org.md). Если организация у вас уже есть, пропустите этот шаг.

1. В {{ tracker-name }}, на панели слева, нажмите ![](../_assets/tracker/svg/admin.svg) **Администрирование** → ![](../_assets/tracker/svg/organizations.svg) [**{{ ui-key.startrek.ui_Common_smart-components_page-admin_PageAdmin.menu-item-orgs }}**]({{ link-tracker }}admin/orgs). В блоке организаций {{ org-full-name }} нажмите **{{ ui-key.startrek.ui_Common_smart-components_page-admin_OrgPanes_DirectoryOrgPane.domain-task-action }}** и выберите организацию. Дождитесь синхронизации пользователей и групп из {{ org-full-name }} в {{ tracker-name }} — она занимает до 30 минут.

1. В сервисе {{ org-full-name }} добавьте [пользователей](../organization/operations/manage-users.md) и [группы](../organization/operations/manage-groups.md) — как в {{ ya-360 }}. Название группы в {{ tracker-name }} формируется из поля **Описание**, а если оно не задано, то из поля **Название**.

   {% note info %}

   Пользователи, которые зарегистрированы в обеих организациях с одними и теми же учетными данными, после переключения смогут продолжить работу в {{ tracker-name }} без изменений. Для остальных пользователей в новой организации потребуется заново настроить права доступа к {{ tracker-name }}, очередям, фильтрам и дашбордам, а также к страницам {{ wiki-name }} и формам в {{ forms-name }}.

   {% endnote %}

1. В сервисе {{ org-full-name }} настройте роли: если в организации были и другие администраторы, [выдайте им роли](../organization/security/index.md#add-role) `admin` или `tracker.admin`.

1. В {{ tracker-name }} [настройте доступы](./access.md) для пользователей или групп.

   {% note info %}

   В настройках доступа для групп ![](../_assets/tracker/svg/admin.svg) **Администрирование** → [**{{ ui-key.startrek.ui_Common_smart-components_page-admin_PageAdmin.menu-item-groups }}**]({{ link-tracker }}admin/groups) вы увидите 2 группы **Все сотрудники**: одна из них с сотрудниками из организации {{ ya-360 }}, а другая — с сотрудниками из обеих организаций.

   {% endnote %}

Если организация {{ ya-360 }} вам не нужна, пока не удаляйте ее — о такой необходимости мы сообщим вам отдельно. Описанных выше действий достаточно для того, чтобы не переходить на платный тариф {{ ya-360 }}.


Если у вас остались вопросы, пожалуйста, напишите в нашу [службу поддержки](troubleshooting.md).