# Аналитическая лабораторная работа №1

## Цель работы:

Знакомство с облачными сервисами. Понимание уровней абстракции над инфраструктурой в облаке. Формирование понимания типов потребления сервисов в сервисной-модели.


## Дано:

1. Слепок данных биллинга от провайдера после небольшой обработки в виде SQL-параметров. Символ % в начале/конце означает, что перед/после него может стоять любой набор символов.
2. Google с документациями провайдера


## Описание сервисов:

### Amazon ElastiCache
Amazon ElastiCache - Полностью управляемое хранилище данных в памяти и служба кэширования. Сервис повышает производительность веб-приложений за счет извлечения информации из управляемых кэшей в памяти, вместо того чтобы полностью полагаться на более медленные дисковые базы данных. ElastiCache поддерживает два механизма кэширования в памяти с открытым исходным кодом: Memcached и Redis.


### Amazon ES
Amazon ES - это распределенный поисковый и аналитический движок на базе Apache Lucene. С его помощью можно эффективно хранить и анализировать большие объемы данных.

### Amazon ES


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
