# My Vote AWS

Материалы для самостоятельной работы  AWS Slurm (база). Приложение уже написано, и вам осталось лишь развернуть его, используя изученные технологии! Система вам уже знакома по модулю Infrastructure as a Code, это демонстрационное приложение для голосования, но в этот раз оно переработано, чтобы использовать возможности AWS напрямую: она состоит из двух фронтенд-компонент (JS Single-Page Application) и трёх бэкенд-компонент (Python). 

Мы предлагаем такую схему: опубликовать статические файлы в бакетах S3 (по одному для каждого фронтенда), разместить бэкенды как функции Lambda и предоставить к ним досту при помощи API Gateway. Обработчик голосов предлагаем запустить на мощностях EC2, хотя вы можете предпочесть чистый серверлесс.

![image](https://user-images.githubusercontent.com/1742301/106404317-b9022500-6432-11eb-94ed-602d2b27b8fb.png)

Обратите внимание, что, хотя весь код уже написан, вам предстоит немало работы по созданию ресурсов (очередей, таблиц DynamoDB) и назначению к ним доступа. По необходимости используйте подсказки, расположенные в соответствующих папках.

## Используемые Технологии

* ✅ EC2
* ✅ S3
* ✅ CloudFront
* ✅ Базы Данных (DynamoDB)
* ✅ VPC
* ✅ Очереди SQS
* ✅ Уведомления SNS
* ✅ Serverless (API Gateway, Lambda)
* ✅ IAM

По желанию:
* ⚠️ IaaC (Terraform, CloudFormation, Cloud Development Kit)
* ⚠️ Billing и Costs

## Компоненты

* [API Gateway](./gateway)
* [Фронтенд голосования, Javascript](./voting-frontend)
* [Бэкенд голосования, Python](./voting-backend)
* [Обработчик голосов, Python](./vote-processor)
* [База Данных, DynamoDB](./dynamodb)
* [Бэкенд результатов, Python](./result-backend)
* [Фронтенд результатов, Javascript](./result-frontend)

## Архитектура

**Заменить на картинку**

voting-frontend (S3) --> API Gateway --> voting-backend (Lambda) --> SNS --> SQS --> vote-processor (EC2) --> DynamoDB <-- result-backend (lambda) <-- API Gateway <-- result-frontend (S3)
