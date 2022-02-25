# Це демо СI/CD процесу доставки контейнеризованого додатку в Kubernetes Cluster

# Вимоги :
1) AWS Elastic Kubernetes Service (деталі в папці terraform files)
2) Jenkins
3) Docker

# Налаштування Jenkins
1) Створити новий пайплайн
2) Вибрати як джерело коду репрозиторій з цим кодом
3) Створити Credentials: Dockerhub, AWS: Secret access key, AWS Access key ID
4) Для доставки контенера натиснути Deploy або налаштувати Webhook
