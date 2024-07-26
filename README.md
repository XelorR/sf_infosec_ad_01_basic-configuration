# Active Directory configuration

Homework for sf/mifi infosec courses

## Что нужно сделать

### Даны два устройства, находящиеся в домене:

1. **SF-AD с Active Directory + OpenVPN Server**

- Подключение по RDP
- User: Administrator
- **Active Directory**
- Domain: sfcourse.local
     
2. **SF-CLIENT**
- Подключение по RDP
- User: Administrator
- **OpenVPN Client**

### Вам необходимо произвести настройку Active Directory по следующему ТЗ:

1. Создайте 4 пользователя с двумя функциональными ролями: «пользователь» и
«оператор». Функциональные роли выражены в групповых объектах Active Directory (итого — 4 пользователя, по 2 в каждой группе).

2. Для каждой группы создайте групповую политику.
3. Для всех ролей в групповую политику включите следующие правила:

- [x] Минимальное количество символов в пароле — 8;
- [x] Необходимость спецсимволов в пароле — да;
- [x] Максимальное время жизни пароля — 45 дней.

4. Для роли «пользователь»:

- [x] Через групповую политику поставьте задний фон рабочего стола на ваш выбор.
- [x] Отключите возможность смены пароля.
- [x] Запретите редактирование реестра Windows.

5. Для роли «оператор»:

- [x] Через групповую политику поставьте задний фон рабочего стола на ваш выбор. Фон должен отличаться от изображения на рабочем столе «пользователя».
- [x] При входе «оператора» должен открываться PowerShell.

6. Включите KDC Armoring и поставьте значение TheMachineAccountQuota на «5».

### Условия реализации

В качестве результата предоставьте (загрузите на GitHub и пришлите ссылку на репозиторий):

- [x] скриншоты наличия объектов в Active Directory;

![](./assets/1_users-exists.png)

![](./assets/1_ops-exists.png)

- [x] скриншоты входа на SF_CLIENT под доменными пользователями с разными ролями;

![](./assets/2_allow-remote-login.png)

![](./assets/2_logging-in.png)

![](./assets/2_user-login-successful.png)

![](./assets/2_operator-login-successful.png)

- [x] созданные политики в текстовом виде (как вариант: вывод команд gpresult /scope computer и gpresult /scope user для каждой роли);

![](./assets/3_getting-data.png)

  - [operator](./assets/operator1.html)
  - [user](./assets/user1.html)
  - [computer](./assets/comp.html)

- [x] скриншот пользователя с SF_CLIENT (скрин рабочего стола);

![](./assets/2_user-login-successful.png)

- [x] скриншот оператора с SF_CLIENT (скрин рабочего стола);

![](./assets/4_operator-powershell-autostarted.png)

![](./assets/2_operator-login-successful.png)

![](./assets/4_operator-no-regedit-restrictions.png)

- [x] скриншот предупреждения после попытки «пользователя» запустить regedit.

![](./assets/4_user-regedit-forbidden.png)

> Важно! После выполнения задания удалите созданные политики и объекты AD, а также верните атрибуты в исходное состояние.

- [x] удалил

> В качестве альтернативы вы можете развернуть собственный домен с двумя и более устройствами и выполнить задание на локальном устройстве.

Для того, чтобы не ждать отведённое время для применения политики на SF_CLIENT, можно через PowerShell ввести команду:

```cmd
gpupdate /force
```

- [x] сделал
