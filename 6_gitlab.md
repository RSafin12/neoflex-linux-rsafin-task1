### Задание 1 
Токен сделать конечно можно, однако это не очень удобно. Проще настроить работу через SSH-ключи, как это настроено у меня.   
![1st_task](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/gitlab/1st_task.png)  

### Задание 2 
Before  
![before](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/gitlab/2nd_before.png)  

After  
![after](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/gitlab/2nd_after.png)

### Задание 3
Runner запущен    
![runner](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/gitlab/runner.png)    
Скриншот с добавленными переменными   
![vars](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/gitlab/vars.png)  
Pipeline работает     
![pipe_is_working](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/gitlab/pipe2_is_running.png)    
и успешно отработал    
![pipe_finished](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/gitlab/pipe_passed.png)    
В результате есть приложение  
![app2_works](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/gitlab/app2_is_working.png)  
![app2_works2](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/gitlab/app2_works2.png)  

### Задание 4
Pipeline состоит из 2 этапов, первым идет Build  
![build](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/gitlab/kaniko_build.png)  

Вторым этапом идет деплой
![deploy](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/gitlab/deploy_with_helm.png) 

Приложение успешно развернулось в кластере
![kubectl](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/gitlab/kubectl_helm.png)   
и доступно в браузере 
![app3](https://github.com/RSafin12/neoflex-linux-rsafin-task1/blob/main/Screenshots/gitlab/app3.2.png)   

Мой репозиторий с pipeline доступен по [ссылке](https://gitlab.com/rsafin2/neo-app-3)
Текст pipeline также доступен по [ссылке](https://github.com/RSafin12/neoflex-linux-rsafin-task1/app3_pipeline.yaml)





