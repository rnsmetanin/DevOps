Домашнее задание к занятию "4.3. Языки разметки JSON и YAML"
Обязательная задача 1
Мы выгрузили JSON, который получили через API запрос к нашему сервису:

    { "info" : "Sample JSON output from our service\t",
        "elements" :[
            { "name" : "first",
            "type" : "server",
            "ip" : 7175 
            }
            { "name" : "second",
            "type" : "proxy",
            "ip : 71.78.22.43
            }
        ]
    }
Нужно найти и исправить все ошибки, которые допускает наш сервис

Первое что непонятно - назначение \t в значении ключа info. По идее его там быть не должно.
Второе - это значение IP адреса в 5-й строке. Он вообще неправильно написан и должен быть в кавычках.
Третья ошибка в 9-й строке - сам ключ ip и его значение ключа опять без кавычек. Должен получиться примерно такой вариант:
{ "info" : "Sample JSON output from our service",
        "elements" :[
            { "name" : "first",
            "type" : "server",
            "ip" : "7.1.75" 
            }
            { "name" : "second",
            "type" : "proxy",
            "ip" : "71.78.22.43"
            }
        ]
    }
Обязательная задача 2
В прошлый рабочий день мы создавали скрипт, позволяющий опрашивать веб-сервисы и получать их IP. К уже реализованному функционалу нам нужно добавить возможность записи JSON и YAML файлов, описывающих наши сервисы. Формат записи JSON по одному сервису: { "имя сервиса" : "его IP"}. Формат записи YAML по одному сервису: - имя сервиса: его IP. Если в момент исполнения скрипта меняется IP у сервиса - он должен так же поменяться в yml и json файле.

Ваш скрипт:
#!/usr/bin/env python3

import json
import yaml
import socket

jconf="ip.json"
yconf="ip.yaml"

with open(jconf) as j_data:
    conf = json.load(j_data)

for host, ip in conf.items():
    new_ip=socket.gethostbyname(host)

    if (ip != new_ip):
        print ('[ERROR] {} IP mismatch: {} {}'.format(host,ip,new_ip))
        conf[host]=new_ip

for host, ip in conf.items():
    print('{} - {}'.format(host,ip))

with open(jconf, "w") as j_data:
    json.dump(conf, j_data, indent=2)

with open(yconf, "w") as y_data:
    y_data.write(yaml.dump(conf,explicit_start=True, explicit_end=True))
Вывод скрипта при запуске при тестировании:
C:\Users\y.kozlov\PycharmProjects\pythonProject\venv\Scripts\python.exe C:/Users/y.kozlov/PycharmProjects/pythonProject/hw/8.py
drive.google.com - 142.251.1.194
mail.google.com - 173.194.221.17
google.com - 64.233.162.113

Process finished with exit code 0
json-файл(ы), который(е) записал ваш скрипт:
{
  "drive.google.com": "142.251.1.194",
  "mail.google.com": "173.194.221.17",
  "google.com": "64.233.162.113"
}
yml-файл(ы), который(е) записал ваш скрипт:
---
drive.google.com: 142.251.1.194
google.com: 64.233.162.113
mail.google.com: 173.194.221.17
...
Дополнительное задание (со звездочкой*) - необязательно к выполнению
Так как команды в нашей компании никак не могут прийти к единому мнению о том, какой формат разметки данных использовать: JSON или YAML, нам нужно реализовать парсер из одного формата в другой. Он должен уметь:

Принимать на вход имя файла
Проверять формат исходного файла. Если файл не json или yml - скрипт должен остановить свою работу
Распознавать какой формат данных в файле. Считается, что файлы *.json и *.yml могут быть перепутаны
Перекодировать данные из исходного формата во второй доступный (из JSON в YAML, из YAML в JSON)
При обнаружении ошибки в исходном файле - указать в стандартном выводе строку с ошибкой синтаксиса и её номер
Полученный файл должен иметь имя исходного файла, разница в наименовании обеспечивается разницей расширения файлов
Ваш скрипт:
???
Пример работы скрипта:
???
