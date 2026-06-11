# Diagramas de Arquitetura

Este diretório contém os diagramas arquiteturais da proposta **Event-Driven Architecture (EDA) na AWS**.

## Conteúdo

- O diagrama principal está em [`../../arquitetura/diagrama.png`](../../arquitetura/diagrama.png).
- A descrição textual completa da arquitetura está em [`../../arquitetura/descricao-arquitetura.docx`](../../arquitetura/descricao-arquitetura.docx).

## Componentes representados

- **Front-end:** React/Next.js em S3 + CloudFront
- **Entrada:** API Gateway com Cognito (JWT)
- **Mensageria:** SNS (pub) + SQS (sub) com DLQ
- **Processamento:** AWS Lambda (serverless)
- **Persistência:** DynamoDB (NoSQL) e RDS (relacional)
- **Arquivos:** S3 com presigned URLs
- **Observabilidade:** CloudWatch, X-Ray, CloudTrail
- **Integrações:** SES, SNS (SMS), Webhooks

## Fluxo resumido

```
Usuário → CloudFront → API Gateway (Cognito) →
  ├─ Síncrono:  Lambda → DynamoDB/RDS
  └─ Assíncrono: SNS → SQS → Lambda → DynamoDB/RDS/S3/SES
```

Todos os componentes alimentam o CloudWatch (métricas/logs) e o dashboard administrativo.
