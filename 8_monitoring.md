### Задание 1
Панель мониторинга создана
![grafana_1](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/grafana/grafana_1.png)
### Задание 2
Я использовал утилиту sysbench для создания нагрузки, которая почему то нагружала только одно ядро, это видно в htop  
![htop](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/grafana/htop.png)  
Также я попробовал скачать образ centos, чтобы создать нагрузку на сеть и занять немного места на диске.   
По итогу на дашборде виден    
- пик нагрузки на ядро CPU(красная пиковая линия на графике CPU)  
- пик загрузки сети(фиолетовый пик на графике Net_adapter)   
![grafana_2](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/grafana/grafana_2.png)   
### Задание 3
Метрика указывающая на статус сервера:      
`up{instance="192.168.31.247:9100", job="External servers"}`   
Я добавил дашборд, на котором видно, как я выключил сервер.  
График = 1 -- сервер работает   
График = 0 -- сервер не работает   
На скриншоте реакция дашборда на выключение сервера, график упал  
![grafana_3](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/grafana/grafana_3.png)  
А вот тут я включил сервер обратно, график поднялся  
![grafana_3.2](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/grafana/grafana_3.2.png)  
### Задание 4
Для создания alert rule была использована метрика из задания 3  
При активном состоянии сервера видим такую картину   
![grafana_4.1](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/grafana/grafana_ok.2.png)  
![grafana_4.2](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/grafana/grafana_ok.1.png)  
А теперь выключим сервера и посмотрим на реакцию  
![grafana_4.4](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/grafana/grafana_fire.1.png)
![grafana_4.5](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/grafana/grafana_fire.2.png)