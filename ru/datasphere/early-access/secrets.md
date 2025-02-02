# Хранение приватных данных

{{ ml-platform-name }} предоставляет специальный инструмент _Секретница_ для безопасной работы с приватными данными (ключами, паролями и т.д.). Секретница расположена во вкладке ![Secrets](../../_assets/datasphere/jupyterlab/secret.svg).

_Секрет_ — это пара ключ-значение, в которой значение хранится в зашифрованном виде. После создания секрета вместо значения будут видны символы `***`. 

Секреты создаются в проекте и закрепляются за ним. Созданные секреты можно использовать в коде ячейки как переменные окружения.

{% note tip %}

Преимущество секретницы в том, что значения секретов хранятся и передаются только в зашифрованном виде. Не выводите значение секрета на экран и не перезаписывайте их в обычную переменную.

{% endnote %}

## Область видимости секретов {#scope}

_Область видимости_ секрета определяет, где будет доступен созданный секрет. Она может принимать значения:
* project — секрет доступен только в [проекте](../concepts/project.md), в котором он создан;
* folder — секрет доступен во всех проектах каталога, в которой расположен проект;
* cloud — секрет доступен во всех проектах облака.

Секрет, который создан в другом проекте, нельзя изменить, но можно изменить его [копию](#copy). Скопированный секрет не связан с исходным: копию можно изменять и удалять, и это не затронет оригинал. 

Нельзя в одном проекте создавать секреты с одинаковым названием. Если секрет был создан в другом проекте, нельзя создать секрет с таким же названием в той же области видимости. Если в проекте видны секреты с одинаковым названием из разных областей видимости, то в коде будет доступен секрет, который <q>ближе</q> к проекту. Секрет из области folder перекрывает одноименный секрет из области cloud, секрет из области project перекрывает одноименные секреты из областей folder и cloud.

## Работа с секретами

### Создание секрета {#create}

1. Откройте проект, в котором нужно создать секрет.
1. Убедитесь, что включен [режим раннего доступа](index.md).
1. Чтобы создать секрет, перейдите во вкладку ![Secrets](../../_assets/datasphere/jupyterlab/secret.svg) и нажмите значок ![plus](../../_assets/datasphere/jupyterlab/add.svg). 
1. В диалоговом окне заполните поля:
    * **Name** — задайте имя секрета. 
      Имя может содержать только латинские символы в любом регистре, цифры и нижнее подчеркивание и не должно начинаться с цифры;
    * **Content** — введите значение, которое будет храниться в зашифрованном виде;
    * **Scope** — выберите область видимости секрета.
1. После ввода всех значений сохраните секрет кнопкой Save. Новый секрет появится в списке доступных.
1. Чтобы секрет был доступен для использования, перезапустите ядро системы. Для этого выберите **Kernel ⟶ Restart kernel** в меню интерфейса {{ ml-platform-name }}.

### Изменение секрета {#edit}

1. В списке видимых секретов выберите тот, который вы хотите изменить, и нажмите значок ![pencil](../../_assets/pencil.svg).
1. В диалоговом окне задайте новое значение необходимого поля.
    * Чтобы изменить значение секрета, впишите новое вместо `***`.
    * Чтобы переименовать секрет, введите новое име в поле **Name**. 
    * Чтобы изменить область видимости, выберите нужное значение из списка. 
      Вводить значение секрета заново не нужно, если его не требуется изменить.
1. После ввода всех значений сохраните секрет кнопкой **Save**.

### Копирование секрета {#copy}

1. В списке видимых секретов выберите тот, который вы хотите скопировать в свой проект, и нажмите значок ![copy](../../_assets/copy.svg).
1. В диалоговом окне выберите область видимости нового секрета и нажмите **Clone**. Область видимости копии должна отличаться от области видимости оригинального секрета.

### Удаление секрета {#delete}

1. В списке видимых секретов выберите тот, который вы хотите удалить, и нажмите значок ![pencil](../../_assets/pencil.svg).
1. В диалоговом окне нажмите кнопку **Delete**. Секрет удален. 

