## Пререквизиты:
* поднимаем кубер кластер (можно в облаке)
* устанавливаем helm

## Настройка проекта:
#### Устанавливаем Airflow:
```
kubectl create namespace airflow
helm repo add apache-airflow https://airflow.apache.org
helm install airflow apache-airflow/airflow --namespace airflow
```


#### Проброс портов
```
Airflow Webserver:     kubectl port-forward svc/airflow-webserver 8080:8080 --namespace airflow
Flower dashboard:      kubectl port-forward svc/airflow-flower 5555:5555 --namespace airflow
```

####
```
Default Webserver (Airflow UI) Login credentials:
    username: admin
    password: admin
Default Postgres connection credentials:
    username: postgres
    password: postgres
    port: 5432
    
/opt/airflow/airflow.cfg
```

#### Переключение контекста на определенный нейспейс
```
kubectl config set-context --current --namespace=airflow
```

#### Запуск bash в определенном поде
```
kubectl exec --stdin --tty airflow-webserver-5df6b7d4bc-l9rcg -- /bin/bash
```