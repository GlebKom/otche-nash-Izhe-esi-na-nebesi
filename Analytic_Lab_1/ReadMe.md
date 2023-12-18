# Аналитическая лабораторная работа №1

## Цель работы:

Знакомство с облачными сервисами. Понимание уровней абстракции над инфраструктурой в облаке. Формирование понимания типов потребления сервисов в сервисной-модели.


## Дано:

1. Слепок данных биллинга от провайдера после небольшой обработки в виде SQL-параметров. Символ % в начале/конце означает, что перед/после него может стоять любой набор символов.
2. Google с документациями провайдера.

## Исходные данные
![image](https://github.com/GlebKom/otche-nash-Izhe-esi-na-nebesi/assets/57949970/de48e42b-d1bf-4694-894b-104efecbb99e)



## Описание сервисов:

### Amazon ElastiCache
Amazon ElastiCache - Полностью управляемое хранилище данных в памяти и служба кэширования. Сервис повышает производительность веб-приложений за счет извлечения информации из управляемых кэшей в памяти, вместо того чтобы полностью полагаться на более медленные дисковые базы данных. ElastiCache поддерживает два механизма кэширования в памяти с открытым исходным кодом: Memcached и Redis.


### Amazon ES
Amazon ES - это распределенный поисковый и аналитический движок на базе Apache Lucene. С его помощью можно эффективно хранить и анализировать большие объемы данных.

### Amazon QLDB
Amazon QLDB - это полностью управляемая база данных реестров, обеспечивающая прозрачный, неизменяемый и проверяемый криптографическими методами журнал транзакций.

### AWS KMS
AWS KMS - Сервис AWS Key Management Service (KMS) обеспечивает централизованный управление криптографическими ключами, используемыми для защиты данных. Этот сервис интегрирован с другими сервисами AWS, что упрощает шифрование данных, хранимых в этих сервисах, и управление доступом к ключам для их дешифрования.

### AWS CloudHSM
AWS CloudHSM - обеспечивает полный контроль управления доступом и защиту ваших ключей шифрования с помощью надежных и совместимых аппаратных модулей безопасности.

### Amazon Rekognition
Amazon Rekognition - Облачная платформа компьютерного зрения. Позволяет встраивать в приложения аналитику изображений и видео, созданную алгоритмами на базе глубокого обучения.

### Amazon Textract
Amazon Textract - это сервис машинного обучения (ML), который извлекает текст, рукописный ввод и данные из отсканированных документов, таких как PDF-файлы, с помощью оптического распознавания символов.

### Amazon Lex
Amazon Lex – сервис по созданию голосовых и текстовых диалоговых интерфейсов в любых приложениях. Amazon Lex предоставляет расширенные функциональные возможности глубокого обучения, такие как автоматическое распознавание речи (ASR), предназначенное для преобразования речи в текст, и понимание естественных языков (NLU), предназначенное для определения смысла текста.

### AWS Code Pipeline
AWS Code Pipeline - это полностью управляемый сервис непрерывной доставки, который помогает автоматизировать работу конвейеров выпуска для быстрого и надежного обновления приложений и инфраструктуры. Схема демонстрирует, как AWS CodePipeline использует настроенную клиентом модель выпуска ПО и автоматически запускает в рамках этой модели этапы сборки, тестирования и развертывания при каждом изменении кода.

### Amazon SES
Amazon SES - экономичный, гибкий и масштабируемый поставщик сервисов электронной почты, с помощью которого разработчики могут отправлять электронные письма из любого приложения.

### Amazon SNS
Amazon SNS - это управляемый сервис отправки сообщений для установления связи, который обеспечивает обмен сообщениями между изолированными приложениями на базе микросервисов или непосредственно с пользователями через SMS, мобильные push-уведомления и электронную почту

| IT Tower           | Service Family        | Service Type           | Service Usage Type       | Product Code          | Usage Type                   | [lineItem/Operation]          | lineItem/LineItemDescription         |
|--------------------|-----------------------|------------------------|--------------------------|-----------------------|------------------------------|-------------------------------|-------------------------------------|
| Storage            | Database              | ElastiCache            | Tax                      | AmazonElastiCache     |                              | Tax%                          |                                   |
| Storage            | Database              | ElastiCache            | Usage per Gb              | AmazonElastiCache     | %NodeUsage:cache%            |                               |                                   |
| Storage            | Database              | ElastiCache            | Create Backup             | AmazonElastiCache     | %CreateCacheSnapshot%       |                               |                                   |
| Storage            | Database              | ElastiCache            | Backup Storage            | AmazonElastiCache     | %ElastiCache:BackupUsage     |                               |                                   |
| Storage            | Analytics             | OpenSearch Service      | Tax                      | AmazonES              |                              | Tax%                          |                                   |
| Storage            | Analytics             | OpenSearch Service      | Data Transfer charges     | AmazonES              | %DataTransfer%Bytes          |                               |                                   |
| Storage            | Analytics             | OpenSearch Service      | Bytes                    | AmazonES              | %AWS%Bytes                   |                               |                                   |
| Storage            | Analytics             | OpenSearch Service      | General Purpose SSD       | AmazonES              | %ES:GP2-Storage%             |                               |                                   |
| Storage            | Analytics             | OpenSearch Service      | Magnetic Storage          | AmazonES              | %ES:Magnetic-Storage         |                               |                                   |
| Storage            | Analytics             | OpenSearch Service      | Instance Usage            | AmazonES              | %ESInstance%                 |                               |                                   |
| Storage            | Analytics             | OpenSearch Service      | Provisioned IOPS           | AmazonES              | %PIOPS%                      |                               |                                   |
| Storage            | Analytics             | OpenSearch Service      | Cloudfront Usage          | AmazonES              | %CloudFront%                 |                               |                                   |
| Storage            | Database              | QLDB                   | Storage Rate              | AmazonQLDB            | %Storage                     |                               |                                   |
| Storage            | Database              | QLDB                   | IO requests per second    | AmazonQLDB            | %IO-Request                  |                               |                                   |
| Storage            | Security              | kms                    | Tax                      | awskms                |                              | Tax%                          |                                   |
| Storage            | Security              | kms                    | Requests per month        | awskms                | %KMS-Requests                |                               |                                   |
| Storage            | Security              | kms                    | Keys count                | awskms                | %KMS-Keys                    |                               |                                   |
| Storage            | Security              | CloudHSM                | Price of HSM per hour     | CloudHSM              | %CloudHSM%                   |                               |                                   |
| Output             | Machine Learning      | Rekognition            | Analysis                 | AmazonRekognition     |                              |                               |                                   |
| Output             | Machine Learning      | Textract                | Froms Count               | AmazonTextract        | %FormsPagesProcessed         |                               |                                   |
| Output             | Machine Learning      | Textract                | Tables Count              | AmazonTextract        | %TablesPagesProcessed        |                               |                                   |
| Output             | Machine Learning      | Textract                | Text Count                | AmazonTextract        | %TextPagesProcessed          |                               |                                   |
| EndUser            | Machine Learning      | Lex                    | Tax                      | AmazonLex             |                              | Tax%                          |                                   |
| EndUser            | Machine Learning      | Lex                    | Requests count            | AmazonLex             | %Req%                        |                               |                                   |
| Delivery           | Developer Tools       | Pipeline               | Tax                      | AWSCodePipeline       |                              | Tax%                          |                                   |
| Delivery           | Developer Tools       | Pipeline               | Trial Piplines            | AWSCodePipeline       | %trialPipeline%              |                               |                                   |
| Delivery           | Developer Tools       | Pipeline               | Active Pipline            | AWSCodePipeline       | %activePipeline%             |                               |                                   |
| EndUser            | Business App          | SES                    | Tax                      | AmazonSES             |                              | Tax%                          |                                   |
| EndUser            | Business App          | SES                    | Recipients count          | AmazonSES             | %Recipients%                 |                               |                                   |
| EndUser            | Business App          | SES                    | Attachments Size          | AmazonSES             | %AttachmentsSize-Bytes        |                               |                                   |
| EndUser            | Business App          | SES                    | Incoming mail chunks      | AmazonSES             | %ReceivedChunk%              |                               |                                   |
| EndUser            | Business App          | SES                    | Message Charges           | AmazonSES             | %Message%                    |                               |                                   |
| EndUser            | App Integration       | SNS                    | Tax                      | AmazonSNS             |                              | Tax%                          |                                   |
| EndUser            | App Integration       | SNS                    | Type FIFO                 | AmazonSNS             | %Requests-Tier1              |                               |                                   |
| EndUser            | App Integration       | SNS                    | Type Standard             | AmazonSNS             | %Requests-Tier2              |                               |                                   |
| EndUser            | App Integration       | SNS                    | Delivery via GCM          | AmazonSNS             | %DeliveryAttempts-GCM        |                               |                                   |
| EndUser            | App Integration       | SNS                    | Delivery via SMTP          | AmazonSNS             | %DeliveryAttempts-SMTP       |                               |                                   |
| EndUser            | App Integration       | SNS                    | Delivery via HTTP          | AmazonSNS             | %DeliveryAttempts-HTTP       |                               |                                   |
| EndUser            | App Integration       | SNS                    | Delivery via SQS           | AmazonSNS             | %DeliveryAttempts-SQS        |                               |                                   |
| EndUser            | App Integration       | SNS                    | Price of SMS               | AmazonSNS             | %SMS-Price%                  |                               |                                   |
| EndUser            | App Integration       | SNS                    | Sent SMS count            | AmazonSNS             | %SMS-Sent%                   |                               |                                   |
| EndUser            | App Integration       | SNS                    | Delivety via APN          | AmazonSNS             | %DeliveryAttempts-APNS%      |                               |                                   |
| EndUser            | App Integration       | SNS                    | Delivery via LAMBDA        | AmazonSNS             | %DeliveryAttempts-LAMBDA     |                               |                                   |
