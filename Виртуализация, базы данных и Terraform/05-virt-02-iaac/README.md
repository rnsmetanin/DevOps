## Задача 1

##### - Опишите своими словами основные преимущества применения на практике IaaC паттернов.
    Приемущества IaaC паттернов (CI (Continuous Integration), CD (Continuous Delivery), CD (Continuous Deployment)):

    Continuous Integration - непрерывная интеграция позволяет сократить время и трудозатраты на обнаружение ошибок 
    в коде за счет частых слияний кода в репозиторий, что позволяет запускать частые автотесты и автоматические сбороки.

    CD (Continuous Delivery) - Непрерываная доставка сокращает трудозатраты, за счет автоматизации рутинной 
    ручной публикации приложения(выпуск выполняется по нажатию). Что позволяет чаще делать выпуски, 
    оперативно исправлять баги(выпуская хотфиксы), а в случае обнаружения проблем с продовой версией - быстро 
    откатываться до стабильной версии.
    
    CD (Continuous Deployment) - непрерываное развертывание имеет все те же приемущества что и непрерывная доставка, 
    Но в данном паттерне публикация приложения происходит без участия ответственного лица (в случае успешного выполнения 
    всех автотестов и сборок). Применение непрерывного развертывания не рекомендуется для prod среды. 

##### - Какой из принципов IaaC является основополагающим?
    выделить один принцип как главный сложно. Перечислю основные как равнозначные:
    Ускорение производства и вывода продукта на рынок.
    Стабильность среды, устранение дрейфа конфигураций.
    Более быстрая и эффективная разработка
    
    
## Задача 2

##### - Чем Ansible выгодно отличается от других систем управление конфигурациями?
        
    Отличие Ansible от других подобных систем в том, что он использует существующую SSH инфраструктуру, 
    в то время как другие (Saltstack, Chef, Puppet, и пр.) требуют установки специального PKI-окружения.
    Преимущества:
    Скорость – быстрый старт на текущей SSH инфраструктуре.
    Простота – декларативный метод описания конфигураций.
    Расширяемость — лёгкое подключение кастомных ролей и модулей.
##### - Какой, на ваш взгляд, метод работы систем конфигурации более надёжный push или pull?
    Метод push надежнее, в том плане что инфраструктура более защищена
    нужно внести правки в управляющий сервер и после уже направить эти изменения на управляемые сервера. 
	В случае с pull управляемые сервера сами инициируют получение конфирурации.

## Задача 3

##### Установить на личный компьютер:

##### - VirtualBox
##### - Vagrant
##### - Ansible

##### Приложить вывод команд установленных версий каждой из программ, оформленный в markdown.

VirtualBox:

    C:\Program Files\Oracle\VirtualBox>VBoxManage.exe --version
    6.1.28r147628

Vagrant:

    PS C:\Users\netology_devops\vagrant> vagrant --version
    Vagrant 2.2.19

Ansible:

    user@DESKTOP-WEGH1N4:~$ ansible --version
    ansible [core 2.12.1]

