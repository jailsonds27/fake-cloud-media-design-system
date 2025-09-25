# 🚀 FakeCloudMedia - System Design Challenge

<div align="center">
  
[![System Design](https://img.shields.io/badge/Type-System%20Design-blue.svg)](https://github.com/jailsonds27/fake-cloud-media-design-system)
[![Cloud Architecture](https://img.shields.io/badge/Focus-Cloud%20Architecture-green.svg)](https://github.com/jailsonds27/fake-cloud-media-design-system)
[![Scalability](https://img.shields.io/badge/Priority-Scalability-orange.svg)](https://github.com/jailsonds27/fake-cloud-media-design-system)

_Uma plataforma moderna de gestão de conteúdo multimídia com processamento assíncrono e arquitetura em nuvem_

</div>

---

## 📋 Visão Geral

A **FakeCloudMedia** precisa de uma arquitetura em nuvem para uma plataforma de gestão de conteúdo multimídia. O sistema deve processar uploads de arquivos, executar transformações assíncronas e fornecer APIs para consulta de conteúdo.

### 🎯 Objetivo Principal

**Desenhar uma arquitetura em nuvem** que resolva os seguintes desafios técnicos através da seleção adequada de serviços cloud-native, considerando escalabilidade, custos e performance.

---

## ⚡ Requisitos Arquiteturais

### 📤 **Ingestão de Arquivos**

- **Volume**: 10.000+ uploads/dia com picos de 500 uploads/minuto
- **Formatos**: Imagens (JPEG, PNG, WEBP) e documentos (PDF, DOCX)
- **Tamanhos**: Até 100MB por arquivo
- **Feedback**: Status em tempo real do upload e processamento

### 🔄 **Processamento Assíncrono**

- **Operações**: Validação, conversão de formato, extração de metadados, geração de thumbnails
- **SLA**: 95% dos arquivos processados em até 5 minutos
- **Escalabilidade**: Auto-scaling baseado no tamanho da fila
- **Resiliência**: Retry automático e dead letter queue

### 💾 **Armazenamento de Dados**

| Tipo de Dado               | Características                         | Requisitos                 |
| -------------------------- | --------------------------------------- | -------------------------- |
| **Arquivos Originais**     | 100MB max, acesso esporádico            | Durabilidade 99.999999999% |
| **Metadados Estruturados** | Relacional, consultas complexas         | Consistência ACID          |
| **Logs e Analytics**       | Escrita intensiva, consultas analíticas | Particionamento temporal   |
| **Cache de Thumbnails**    | Acesso frequente, TTL variável          | Baixa latência (<10ms)     |

### 🛡️ **Exposição e Segurança**

- **API Gateway**: Rate limiting (1000 req/min/user), autenticação JWT
- **CDN**: Cache global com TTL de 1 hora para assets estáticos
- **Domínio**: SSL/TLS, CORS configurado
- **Monitoramento**: Métricas de negócio e infraestrutura em tempo real

---

## 🎯 Desafio de Arquitetura

> **Projete uma arquitetura em nuvem que atenda aos requisitos acima, especificando:**

### 🏗️ **Componentes Arquiteturais Necessários:**

1. **Camada de Ingestão**

   - Como receber e validar uploads de arquivos grandes?
   - Qual estratégia para feedback em tempo real?

2. **Armazenamento de Arquivos**

   - Qual serviço de object storage utilizar?
   - Como otimizar custos com diferentes classes de armazenamento?

3. **Orquestração de Processamento**

   - Serverless vs Container-based processing?
   - Como gerenciar filas de processamento e retry policies?

4. **Persistência de Metadados**

   - Qual banco relacional escolher e por quê?
   - Como estruturar dados analíticos para consultas eficientes?

5. **Cache e CDN**

   - Onde implementar cache para thumbnails e metadados?
   - Como configurar CDN para distribuição global?

6. **API Gateway e Segurança**

   - Qual solução para autenticação/autorização?
   - Como implementar rate limiting e versionamento?

7. **Monitoramento e Observabilidade**
   - Quais métricas são críticas para o negócio?
   - Como implementar alertas proativos?

### 📊 **Critérios de Avaliação:**

- **Escalabilidade**: Suporta crescimento de 10x sem refatoração?
- **Custo-efetividade**: Otimização para diferentes padrões de uso
- **Resiliência**: Tolerância a falhas de componentes individuais
- **Performance**: Latência adequada para experiência do usuário
- **Operabilidade**: Facilidade de monitoramento e manutenção

### 🤔 **Pontos de Decisão Arquitetural:**

- Multi-cloud vs Single cloud provider?
- Microserviços vs Arquitetura orientada a eventos?
- Processamento síncrono vs assíncrono para diferentes operações?
- Estratégias de backup e disaster recovery?

---

## 🏗️ Entregáveis Esperados

### 📐 **Diagrama de Arquitetura**

- Componentes de infraestrutura e suas integrações
- Fluxo de dados entre serviços
- Pontos de falha e estratégias de recuperação

### 📋 **Especificação de Serviços**

- Justificativa para cada serviço cloud escolhido
- Configurações de scaling e dimensionamento
- Estimativas de custo por componente

### 🔧 **Considerações Operacionais**

- Estratégias de deployment e CI/CD
- Planos de backup e disaster recovery
- Métricas de SLA e monitoramento

---

<div align="center">

**🎯 Foque na arquitetura, não na implementação!**

_Este é um exercício de system design que avalia suas decisões arquiteturais e conhecimento de serviços cloud_

</div>
