# 📊 Projeto de Análise de Dados - Rede de Postos

## 🧠 Documento de Raciocínio

---

## 📌 1. Visão Geral da Solução

A solução desenvolvida tem como objetivo automatizar o processo de ingestão, tratamento e análise dos dados enviados pelas filiais, integrando informações estruturadas (CSV) e não estruturadas (e-mails).

O fluxo foi projetado para rodar de ponta a ponta sem intervenção manual, contemplando:

* Coleta automática de preços via web scraping
* Normalização dos dados de vendas
* Consolidação das informações
* Uso de IA para estruturação dos e-mails
* Geração de outputs finais prontos para análise

---

## ⚙️ 2. Decisões Técnicas

### 🔄 Automação do fluxo

Foi utilizada leitura dinâmica de múltiplos arquivos (CSV e TXT), permitindo escalabilidade para novos meses ou filiais sem necessidade de alteração manual.

### 🧹 Normalização dos dados

Devido à inconsistência nos nomes dos produtos entre filiais, foi implementado um dicionário de mapeamento para padronização em três categorias canônicas:

* Gasolina Comum
* Etanol
* Diesel S10

Essa etapa foi essencial para viabilizar análises comparativas entre filiais.

### 🤖 Enriquecimento dos dados (RPA)

Os preços médios foram extraídos automaticamente de uma página HTML via requisição HTTP, garantindo que o processo não dependa de intervenção manual.

A partir disso, foi criada a métrica:

```
Volume estimado (litros) = faturamento / preço médio
```

Essa abordagem permite análises mais completas do desempenho operacional.

### 🧠 Uso de IA nos e-mails

Foi utilizada uma API de IA para transformar textos não estruturados em dados estruturados (JSON), contendo:

* Resumo
* Destaques
* Alertas
* Sentimento

O prompt foi desenhado para garantir consistência e facilitar o parsing da resposta.

---

## 🚧 3. Principais Desafios

* Inconsistência nos dados de entrada, especialmente nos nomes dos produtos
* Garantir parsing confiável da resposta da IA, tratando possíveis erros de formatação
* Integração de múltiplas fontes de dados (CSV, HTML, TXT) em um fluxo único

---

## ⚠️ 4. Limitações da Solução

* O mapeamento de produtos é estático e depende de manutenção manual
* A estimativa de volume considera preços médios nacionais, podendo divergir da realidade local
* A análise de e-mails depende da qualidade da resposta da IA e pode apresentar variações
* Não há camada de visualização (dashboard), apenas outputs em CSV

---

## 🚀 5. Próximos Passos

* Implementar um pipeline automatizado (ex: execução agendada mensalmente)
* Criar um dashboard interativo para visualização dos dados
* Melhorar a normalização com técnicas mais robustas (ex: fuzzy matching)
* Armazenar os dados em banco para histórico e análises temporais
* Evoluir o uso de IA para identificação automática de padrões e anomalias

---

## 🎯 6. Senso de Produto

A solução foi pensada para a equipe da sede da rede de postos, que precisa:

* Comparar o desempenho entre filiais
* Identificar problemas operacionais rapidamente
* Tomar decisões baseadas em dados consolidados

Os outputs gerados permitem:

* 📈 Visão quantitativa (vendas e volume)
* 🧩 Visão qualitativa (insights dos gerentes)

---
