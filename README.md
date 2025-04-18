
# 📊 Observabilidade Prometheus

Projeto desenvolvido para demonstrar a implementação de observabilidade utilizando **Prometheus**, **Grafana**, **cAdvisor** e uma aplicação em **Go** com métricas customizadas.

---

## 🔍 Visão Geral

A observabilidade é um pilar fundamental em arquiteturas modernas, permitindo que desenvolvedores e operadores tenham visibilidade sobre o comportamento e a saúde de sistemas em produção.

Este projeto simula uma aplicação escrita em Go com métricas expostas no padrão Prometheus, coletadas e monitoradas por um stack com Prometheus e Grafana, além do cAdvisor para métricas de containers Docker.

---

## 📁 Estrutura do Projeto

```
.
├── docker-compose.yml          # Orquestra os serviços com Prometheus, Grafana, cAdvisor, Redis e o app Go
├── Dockerfile                  # Dockerfile da aplicação Go
├── go.mod / go.sum             # Gerenciamento de dependências Go
├── main.go                     # Aplicação principal com métricas registradas
└── prometheus.yml              # Configuração de scrape do Prometheus
```

---

## 🚀 Serviços

| Serviço      | Porta | Descrição |
|--------------|-------|-----------|
| Prometheus   | `9090`| Responsável por coletar e armazenar as métricas da aplicação |
| Grafana      | `3000`| Interface visual para análise e dashboards |
| Go App       | `8181`| Aplicação de exemplo que expõe métricas no endpoint `/metrics` |
| cAdvisor     | `8080`| Monitoramento de containers Docker |
| Redis        | `6379`| Serviço auxiliar para simulação de carga |

---

## 🧪 Métricas Registradas

As métricas estão implementadas em `main.go` usando a biblioteca `prometheus/client_golang`:

- `goapp_online_users`: Quantidade aleatória de usuários online (gauge)
- `goapp_http_requests_total`: Total de requisições HTTP recebidas (counter)
- `goapp_http_request_duration`: Tempo de resposta das requisições por rota (histogram)

Endpoints disponíveis:

- `/` → Página inicial
- `/contact` → Página de contato
- `/metrics` → Métricas expostas para Prometheus

---

## 🐳 Como subir o ambiente

```bash
docker-compose up --build
```

Acesse:

- [http://localhost:9090](http://localhost:9090) → Prometheus
- [http://localhost:3000](http://localhost:3000) → Grafana (usuário/senha padrão: `admin/admin`)
- [http://localhost:8181](http://localhost:8181) → Aplicação Go

---

## 📈 Dashboard no Grafana

- Adicione o **Prometheus** como fonte de dados.
- Importe um dashboard existente ou crie um personalizado utilizando as métricas disponíveis.

---

## 📦 Tecnologias Utilizadas

- [Go](https://golang.org/)
- [Prometheus](https://prometheus.io/)
- [Grafana](https://grafana.com/)
- [Docker](https://www.docker.com/)
- [cAdvisor](https://github.com/google/cadvisor)

