---
title: Как подключиться к кластеру {{ k8s }} в {{ managed-k8s-full-name }}
description: Следуя данной инструкции, вы сможете подключиться к кластеру {{ managed-k8s-name }}.
---

# Обзор способов подключения

К [кластеру {{ managed-k8s-name }}](../../concepts/index.md#kubernetes-cluster) можно подключиться следующими способами:
* Через интернет, если вы настроили публичный доступ к кластеру [при его создании](../kubernetes-cluster/kubernetes-cluster-create.md).
* С виртуальных машин {{ yandex-cloud }}, расположенных в той же [облачной сети](../../../vpc/concepts/network.md).

Для подключения к кластеру вы можете использовать:
* [kubectl](#kubectl-connect);
* [статический файл конфигурации](#static-conf-connect).

Для подключения к узлам кластера воспользуйтесь инструкцией [{#T}](../node-connect-ssh.md).

## Настройка групп безопасности {#configuring-security-groups}

[Группы безопасности](security-groups.md) могут препятствовать подключению к кластеру. Для управления кластером с помощью `kubectl` в группах безопасности должны быть настроены правила, разрешающие доступ к API {{ k8s }}. Пошаговые инструкции по настройке правил приведены в разделе [Правила для доступа к API {{ k8s }}](security-groups.md#rules-master).

## Подключение к кластеру {#kubectl-connect}

При подключении к кластеру {{ k8s }} пользователь [авторизуется в {{ iam-full-name }}](../../../iam/concepts/authorization/index.md) и получает доступ согласно [присвоенной ему роли](../../security/index.md#yc-api). Для авторизации требуется установка [интерфейса командной строки {{ yandex-cloud }} (CLI)](../../../cli/quickstart.md).

{% include [cli-install](../../../_includes/cli-install.md) %}

{% include [default-catalogue](../../../_includes/default-catalogue.md) %}

Чтобы подключиться к кластеру:

1. [Установите kubectl]({{ k8s-docs }}/tasks/tools/#kubectl).

1. Добавьте учетные данные в конфигурационный файл `kubectl` с учетом типа IP-адреса кластера, к которому вы подключаетесь:

   {% list tabs %}

   - Публичный IP-адрес

      Чтобы получить учетные данные для подключения к публичному IP-адресу кластера через интернет, выполните команду:

      ```bash
      {{ yc-k8s }} cluster \
         get-credentials <имя_или_идентификатор_кластера> \
         --external
      ```
 
      {% include [note-connect-button](../../../_includes/managed-kubernetes/note-connect-button.md) %}

      Если вы [создали кластер](../kubernetes-cluster/kubernetes-cluster-create.md#kubernetes-cluster-create) без публичного адреса, к кластеру можно подключиться только по внутреннему IP-адресу.

   - Внутренний IP-адрес

      Чтобы получить учетные данные для подключения к внутреннему IP-адресу кластера с ВМ, находящейся в той же сети, выполните команду:

      ```bash
      {{ yc-k8s }} cluster \
         get-credentials <имя_или_идентификатор_кластера> \
         --internal
      ```
      
      {% include [note-connect-button](../../../_includes/managed-kubernetes/note-connect-button.md) %}

   {% endlist %}

   {% note info %}

   {% include [note-about-conf](../../../_includes/managed-kubernetes/note-about-conf.md) %}

   {% endnote %}

1. Убедитесь, что кластер доступен:

   ```bash
   kubectl cluster-info
   ```

   Если конфигурация `kubectl` настроена верно, команда вернет информацию о кластере.

## Подключение с помощью статической конфигурации {#static-conf-connect}

Если по каким-либо причинам использование {{ yandex-cloud }} CLI невозможно, [подключитесь к кластеру с помощью статических файлов конфигурации](./create-static-conf.md).