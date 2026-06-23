# Market Data Service

## 📌 Descrição
O **Market Data Service** é responsável por coletar dados de mercado em tempo real, integrar com APIs externas e disponibilizar informações para os demais microsserviços via Kafka e REST API.

## 🎯 Objetivos
- Consumir dados de mercado de fontes externas.
- Normalizar e armazenar informações em banco de dados.
- Publicar eventos no Kafka para outros microsserviços.
- Expor endpoints RESTful para consulta de dados históricos e atuais.

## 🏗️ Arquitetura
- Implementado em **Spring Boot**.
- Banco de dados: **PostgreSQL (AWS RDS)**.
- Mensageria: **Kafka**.
- Integração com APIs externas: Yahoo Finance, Alpha Vantage, Polygon.io, B3.

## 📡 Endpoints RESTful
- `GET /marketdata/{symbol}` → retorna dados atuais de um ativo.
- `GET /marketdata/{symbol}/history` → retorna histórico de preços.
- `POST /marketdata/sync` → força sincronização com APIs externas.

## 🔄 Fluxo de Dados
1. O serviço consome dados das APIs externas.
2. Normaliza e armazena no banco de dados.
3. Publica evento “preco-atualizado” no Kafka.
4. Outros microsserviços consomem os eventos.

## ⚙️ Configuração
Variáveis de ambiente:
- `API_KEY_YAHOO`
- `API_KEY_ALPHA_VANTAGE`
- `API_KEY_POLYGON`
- `DB_URL`, `DB_USER`, `DB_PASS`
- `KAFKA_BROKER`

## 🧪 Testes
- Testes unitários com JUnit.
- Testes de integração simulando chamadas às APIs externas.
- Testes de carga para validar performance.

## 📊 Observabilidade
- Logs enviados para **CloudWatch**.
- Métricas expostas via Actuator.
- Integração com **Datadog** para dashboards.
