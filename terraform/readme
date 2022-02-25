# Інструкція з розгортання Кластера з іфраструктурою та встановлення моніторингу

# Вимоги:
1)  Встановлений Kubectl
2)  Аккаунт AWS з ІАМ користувачем 
3)  Знати AWS Access Key ID, Secret Access Key користувача
4)  Встановлений AWS CLI та сконфігурований за допомогою команди aws configure
5)  Встановлений Terraform
6)  Встановлений Helm

# Порядок розгортання
1) Перейти в терміналі в папку з тераформ файлами та ініціалізувати Терраформ командою terraform init
2) Команда terraform plan виведе в термінал список ресурсів, які будуть створені. terraform apply - запустить процес створення
3) Після створення інфраструктури, необхідно надати компоненту Kubectl можливість з кластером за допомогою команди:
   aws eks --region $(terraform output -raw region) update-kubeconfig --name $(terraform output -raw cluster_name)

# Встановлення моніторингу
Для монітрингу буде використовуватися стек Prometheus-Grafana. Установка стеку відбувається за допомогою комади:     
   helm install prometheus stable/prometheus-operator   
   Оскільки тип сервісу для моніторингу ClusterIP, його трафік доступний тільки в середині кластеру.              
   Щоб отримати доступ з браузеру необхідно виконати команду:    
   kubectl port-forward deployment/prometheus-grafana 3000  
   ця команда перенаправить трафік на localhost:3000

   Login: admin    
   Password: prom-operator
