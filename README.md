# Задание 1

Правила алертов и настройки prometheus, alermanager находятся в папках alermanager/prometheus

Установим alertmanager и добавим правила в прометуес:

![Иллюстрация к проекту](https://github.com/randnull/sre-hw-9/blob/main/pods.png)

![Иллюстрация к проекту](https://github.com/randnull/sre-hw-9/blob/main/photos/prom1.png)

Демострация получения алерта в alertmanager:

![Иллюстрация к проекту](https://github.com/randnull/sre-hw-9/blob/main/photos/alertmanager.png)


Демострация получения алерта в telegram:

![Иллюстрация к проекту](https://github.com/randnull/sre-hw-9/blob/main/photos/telegram_warning.png)


# Задание 2 

Разделим алерты на critical и warning. 

![Иллюстрация к проекту](https://github.com/randnull/sre-hw-9/blob/main/photos/prom2.png)

![Иллюстрация к проекту](https://github.com/randnull/sre-hw-9/blob/main/photos/alert2.png)

Критический алерт:

![Иллюстрация к проекту](https://github.com/randnull/sre-hw-9/blob/main/photos/telegram_critical.png)

Warning алерт:

![Иллюстрация к проекту](https://github.com/randnull/sre-hw-9/blob/main/photos/telegram_warning.png)

Добавим время получения алерта:
```
- receiver: 'telegram-warning'
    match:
      severity: 'warning'
    active_time_intervals:
      - worktime
    continue: true

...
        
- name: 'telegram-warning'
   telegram_configs:
      - bot_token: '7870061232:AAElvx9xla8_0Rj3_PwXpymxkj0anjIA3A'
        api_url: 'https://api.telegram.org'
        chat_id: 506645542
        parse_mode: 'HTML'

...
time_intervals:
  - name: worktime
    time_intervals:
    - times:
      - start_time: 08:00
        end_time: 18:00
```
