# Arquitetura Orientada a Eventos em Nuvem AWS — Projeto de Iniciação Científica

Repositório oficial do projeto de Iniciação Científica desenvolvido ao longo do semestre, consolidando a proposta de uma **Arquitetura Orientada a Eventos (Event-Driven Architecture — EDA)** construída sobre serviços gerenciados da **Amazon Web Services (AWS)**.

---

## Descrição da Proposta

Sistemas monolíticos tradicionais enfrentam limitações relevantes ao serem submetidos a cargas elevadas, ciclos curtos de entrega e demandas de alta disponibilidade. Este projeto propõe uma alternativa baseada em **mensageria assíncrona**, **microsserviços serverless** e **serviços gerenciados em nuvem**, integrando padrões modernos de escalabilidade, segurança e observabilidade.

A solução final apoia-se no paradigma **Event-Driven Architecture**, no qual componentes comunicam-se por meio de eventos publicados em tópicos pub/sub. Isso reduz acoplamento, eleva a resiliência e permite escalabilidade horizontal nativa.

---

## Objetivos

- Consolidar uma proposta científica de arquitetura escalável em nuvem.
- Descrever os componentes da arquitetura proposta e seus respectivos papéis.
- Discutir mecanismos de segurança e escalabilidade aplicáveis a aplicações modernas.
- Demonstrar o uso de serviços gerenciados AWS para reduzir esforço operacional.
- Produzir documentação técnica reaproveitável em projetos futuros.

---

## Tecnologias Utilizadas

### Plataforma de Nuvem
- **AWS** — provedor de nuvem pública adotado como base da proposta.

### Serviços AWS principais
- **Front-end / Borda:** Amazon S3, Amazon CloudFront, AWS WAF
- **Entrada e Autenticação:** Amazon API Gateway, Amazon Cognito
- **Mensageria:** Amazon SNS, Amazon SQS (com Dead Letter Queues)
- **Processamento:** AWS Lambda
- **Persistência:** Amazon DynamoDB (NoSQL), Amazon RDS (relacional)
- **Integrações:** Amazon SES, webhooks via Lambda
- **Observabilidade e Segurança:** Amazon CloudWatch, AWS X-Ray, AWS CloudTrail, AWS KMS, AWS IAM

### Stack do front-end
- **React** ou **Next.js** (TypeScript)

---

## Arquitetura da Solução

A arquitetura segue o estilo **Event-Driven**, organizada em cinco camadas: apresentação, entrada, mensageria, processamento e persistência/observabilidade.

**Fluxo resumido:**

```
Usuário → CloudFront → API Gateway (JWT/Cognito)
   ├─ Síncrono:  Lambda → DynamoDB / RDS
   └─ Assíncrono: SNS → SQS → Lambda → DynamoDB / RDS / S3 / SES
                                          │
                                          ▼
                                    CloudWatch (métricas + logs)
```

- **Descrição completa:** [`arquitetura/descricao-arquitetura.docx`](arquitetura/descricao-arquitetura.docx)
- **Diagrama visual:** [`arquitetura/diagrama.png`](arquitetura/diagrama.png)

---

## Diagramas e Imagens

- [`arquitetura/diagrama.png`](arquitetura/diagrama.png) — diagrama arquitetural principal.
- [`diagramas/arquitetura/`](diagramas/arquitetura/) — diagramas complementares de arquitetura.
- [`diagramas/modelagem/`](diagramas/modelagem/) — diagramas de modelagem de dados, eventos e sequência.

---

## Organização do Repositório

```text
IniciacaoCientifica-main/
├── arquitetura/                    # Descrição e diagrama da arquitetura proposta
│   ├── descricao-arquitetura.docx
│   └── diagrama.png
├── data/                           # Conjuntos de dados
│   ├── bruto/
│   └── tratado/
├── diagramas/                      # Diagramas auxiliares
│   ├── arquitetura/
│   └── modelagem/
├── docs/                           # Documentação técnico-científica
│   ├── apresentacoes/
│   ├── artigos/
│   │   └── Atividade05-ArtigoFinal.docx # ARTIGO FINAL INTEGRADOR
│   └── relatorios/
├── referencias/                    # Levantamento bibliográfico
│   ├── bibtex/
│   │   └── ReferenciasBibliograficas.md
│   ├── pdfs/
│   └── tarefa04-referencias.md
├── src/                            # Código de protótipo e experimentos
│   ├── experimentos/
│   └── prototipo/
└── README.md                       # Este arquivo
```

---

## Entrega da Atividade 05 — Projeto Final Integrador

| Item                                       | Localização |
|--------------------------------------------|-------------|
| Artigo técnico-científico (4–8 páginas)    | [`docs/artigos/Atividade05-ArtigoFinal.docx`](docs/artigos/Atividade05-ArtigoFinal.docx) |
| Arquitetura consolidada (descrição)        | [`arquitetura/descricao-arquitetura.docx`](arquitetura/descricao-arquitetura.docx) |
| Diagrama arquitetural                       | [`arquitetura/diagrama.png`](arquitetura/diagrama.png) |
| Referências bibliográficas                  | [`referencias/bibtex/ReferenciasBibliograficas.md`](referencias/bibtex/ReferenciasBibliograficas.md) |

---

## Referências Principais

- ALMEIDA, J. A. et al. **Guia interativo de boas práticas em Engenharia de Software**. Revista Principia, 2018.
- CORDEIRO, A. F. R. et al. **Arquitetura de microsserviços: uma revisão multivocal**. ERES, 2024.
- DEPRÁ, T. G. B. et al. **Estudo exploratório sobre o uso da arquitetura de microsserviços na indústria de software**. REIC, 2021.
- ESCOLA REGIONAL DE INFORMÁTICA DE MATO GROSSO. **Modernização de arquitetura de sistemas: uma abordagem baseada em microsserviços**. ERI-MT, 2024.
- GARCIA, V. C. **Padrões de arquitetura para escalabilidade: uma perspectiva prática**, 2023.
- IMPACTOS da computação em nuvem na arquitetura de software. **Revista Tópicos**, 2024.
- PRESTES, A. N. et al. **Uma arquitetura de microsserviços para análise de dados de mobilidade urbana**. SBRC, 2021.
- SILVA, I. P. A. **Padrões e diretrizes arquiteturais para escalabilidade**. UFU, 2013.
- VILLAÇA, L.; AZEVEDO, L. **Uma arquitetura de microsserviços orientada a eventos para integração de dados**. SBSI, 2018.

> A lista completa de referências (mais de 15 trabalhos) encontra-se em [`referencias/bibtex/ReferenciasBibliograficas.md`](referencias/bibtex/ReferenciasBibliograficas.md) e na seção *Referências* do [artigo final](docs/artigos/Atividade05-ArtigoFinal.docx).

---

## Autor

**Pedro** — Disciplina de Iniciação Científica.
