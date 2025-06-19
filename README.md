# 📊 Desafio de Monitoramento e Manutenção no Azure (AZ-104) - DIO

Este repositório é um guia prático que consolida resumos, anotações e dicas sobre o **monitoramento e a manutenção de recursos no Microsoft Azure**, com foco especial em Máquinas Virtuais (VMs). Ele serve como material de apoio para estudos e futuras implementações, demonstrando como manter a visibilidade, o controle e a resposta proativa a eventos críticos em um ambiente de nuvem.

---

## 🎯 Objetivos de Aprendizagem

Ao longo desse desafio, pude:

* **Aplicar** conceitos de monitoramento em um ambiente prático do Azure.
* **Documentar** processos técnicos de forma clara e estruturada.
* **Utilizar o GitHub** como ferramenta para compartilhar documentação técnica.

---

## 📚 Conceitos Abordados e Anotações

Aqui estão os principais tópicos que explorei, com resumos e anotações essenciais:

### 1. 🔍 Azure Monitor: O Coração da Observabilidade

* **Função Principal:** O que é o Azure Monitor e qual seu propósito central? (Ex: coletar, analisar e agir sobre telemetria).
* **Dados Coletados:**
    * **Métricas:** Dados **quantitativos** (ex: porcentagem de CPU, memória disponível). Ideais para alertas em tempo real e gráficos de desempenho.
    * **Logs:** Mensagens **descritivas** sobre eventos (ex: logs de erro, logs do sistema operacional). Essenciais para diagnóstico e auditoria.
* **Fontes de Dados:** Como o Azure Monitor coleta dados de VMs (Windows/Linux), recursos Azure e outras fontes personalizadas.
* **Serviços Complementares:** Relação com **Microsoft Defender for Cloud** (segurança) e **Microsoft Sentinel** (SIEM).

#### Dica Rápida:

> Aprender **KQL (Kusto Query Language)** é fundamental, pois é a linguagem usada para consultar seus logs no Log Analytics. Existem muitas queries prontas pra te ajudar a começar!

---

### 2. 📊 Log Analytics Workspace: O Repositório de Logs

* **Propósito:** O que é e por que é o repositório central para seus logs no Azure? (Ex: coletar, agregar, analisar).
* **Organização dos Dados:** Como os logs são armazenados em **tabelas** (ex: `Heartbeat`, `Syslog`, `Event`).
* **Consultas:** Como usar o portal (`Monitor > Logs`) pra acessar o Log Analytics e executar queries KQL.

#### Exemplo de Query KQL (adicione seu próprio exemplo de lab aqui):

```kusto
// Exemplo: Buscar logs de CPU alta para VMs Linux
Syslog
| where Computer contains "LinuxVM" // Filtra por nome da VM Linux
| where SyslogMessage contains "CPU usage is high" // Busca mensagem de erro específica
| project TimeGenerated, Computer, SyslogMessage
| order by TimeGenerated desc
