# Relatório Técnico de Conclusão de Curso de Pós-Graduação

## Análise e Modelagem Preditiva da Evasão em Cursos de Graduação

**Autores:**
Erick Dias
Werbert Wilson Severiano Chaves da Conceição
Alexsander Prates
Luciano Deschamps

---

## Resumo

Este relatório técnico descreve a aplicação de técnicas de análise de dados e aprendizado de máquina para investigar e predizer a evasão em cursos de graduação. O estudo utilizou um *dataset* com **5.817 registros** e **68 variáveis**, seguindo a metodologia **CRISP-DM**. Foram realizados o agrupamento dos motivos de saída em categorias analíticas e a criação de variáveis de desempenho acadêmico, como o percentual de Unidades Curriculares (UCs) aprovadas.

A análise descritiva mostrou que as maiores causas de evasão concentram-se em **Abandono/Desistência (55,34%)** e **motivos Institucionais (SENAI/SESI) (18,00%)**. O modelo preditivo baseado em **Árvore de Decisão** atingiu **Acurácia de 93,63%** e **F1-Score de 0,9312**, com destaque para o **Recall de 98,70%**, indicando elevada capacidade de identificação de alunos evadidos.

A variável mais relevante foi o **Tempo no curso em meses** (importância de 0,4314), evidenciando que a evasão ocorre de forma muito precoce: **98% dos casos acontecem nos primeiros 0 a 3 meses**. Como resultado, o relatório propõe uma estratégia de *deployment* e intervenção baseada em níveis de risco, possibilitando ações proativas de retenção.

---

## 1. Introdução

### 1.1 Contextualização e Problema

A evasão no ensino superior é um desafio crítico, pois afeta tanto a sustentabilidade financeira das instituições quanto o desenvolvimento acadêmico e profissional dos estudantes. Identificar fatores associados à evasão e prever alunos em risco é essencial para orientar políticas institucionais de retenção.

### 1.2 Objetivos do Estudo

Os objetivos principais deste trabalho são:

* Quantificar a distribuição das situações de matrícula e dos principais motivos de evasão;
* Desenvolver e avaliar um modelo de *Machine Learning* para predizer a probabilidade de evasão;
* Propor um plano de ação e *deployment* para utilização prática dos resultados.

### 1.3 Estrutura do Relatório

O relatório está organizado da seguinte forma:

* **Seção 2:** Metodologia e descrição dos dados;
* **Seção 3:** Resultados da análise descritiva;
* **Seção 4:** Modelagem e avaliação do modelo preditivo;
* **Seção 5:** Conclusões e recomendações;
* **Apêndice:** Tabelas de suporte.

---

## 2. Metodologia e Dados

### 2.1 Metodologia de Trabalho

O estudo seguiu o modelo **CRISP-DM**, contemplando as etapas de:

1. Entendimento do Negócio;
2. Entendimento dos Dados;
3. Preparação dos Dados;
4. Modelagem;
5. Avaliação;
6. Sugestões de *Deployment*.

### 2.2 Conjunto de Dados

O *dataset* analisado possui:

* **5.817 registros (linhas)**;
* **68 variáveis (colunas)**.

As variáveis incluem informações demográficas, acadêmicas (UCs aprovadas, reprovadas, cursando) e dados de situação de matrícula e motivo de saída.

### 2.3 Pré-processamento e Classificação dos Motivos de Saída

A variável `motivo_saida` foi reclassificada em categorias analíticas, visando reduzir complexidade e facilitar a interpretação:

* Abandono/Desistência
* Acadêmico
* Financeiro
* Saúde
* Trabalho/Profissional
* Transferência
* Institucional (SENAI/SESI)
* Infraestrutura/Logística
* Indústria/Empresa

Valores ausentes foram imputados como **Abandono/Desistência**, pois, na prática institucional, registros sem motivo formal tendem a representar evasão não declarada.

---

## 3. Resultados e Análise

### 3.1 Distribuição da Situação de Matrícula

| Situação de Matrícula | Quantidade | Percentual |
| --------------------- | ---------- | ---------- |
| Matriculado / Regular | 1.919      | 32,99%     |
| Evadido / Eliminado   | 1.864      | 32,05%     |
| Evadido / Desistente  | 1.335      | 22,95%     |
| Trancado              | 543        | 9,33%      |
| Transferido de Curso  | 156        | 2,68%      |
| **Total**             | **5.817**  | **100%**   |

Os registros classificados como **Evadido / Eliminado** e **Evadido / Desistente** somam **55%** do total, evidenciando a magnitude do problema.

### 3.2 Análise dos Motivos de Evasão

| Categoria do Motivo        | Quantidade | Percentual |
| -------------------------- | ---------- | ---------- |
| Abandono/Desistência       | 3.219      | 55,34%     |
| Institucional (SENAI/SESI) | 1.047      | 18,00%     |
| Transferência              | 474        | 8,15%      |
| Acadêmico                  | 432        | 7,43%      |
| Financeiro                 | 324        | 5,57%      |
| Infraestrutura/Logística   | 163        | 2,80%      |
| Trabalho/Profissional      | 86         | 1,48%      |
| Saúde                      | 70         | 1,20%      |
| Indústria/Empresa          | 2          | 0,03%      |

Os resultados mostram forte predominância de **Abandono/Desistência**, seguida por **motivos Institucionais**.

> **Achado crítico:** alunos classificados como *Evadido / Eliminado* apresentam associação majoritária com motivos **Institucionais (50,48%)**.

### 3.3 Variáveis Acadêmicas e Demográficas

Variáveis de desempenho acadêmico e tempo de permanência no curso mostraram elevada relevância para a evasão. Observou-se também alta taxa de evasão em grupos específicos, como alunos com **Transtorno do Espectro Autista (TEA)**, ainda que com baixa representatividade amostral.

### 3.4 Fator Crítico: Tempo de Evasão

* **98% das evasões ocorrem nos primeiros 0 a 3 meses**;
* Correlação do tempo no curso com evasão: **0,4314**.

Esse resultado indica que a decisão de evadir ocorre muito cedo, reforçando a necessidade de ações preventivas imediatas.

---

## 4. Modelagem Preditiva

### 4.1 Seleção e Treinamento do Modelo

Foi utilizado um modelo de **Árvore de Decisão**, escolhido por sua interpretabilidade.

**Configurações principais:**

* `max_depth = 10`
* `min_samples_split = 10`
* Variável alvo: `evadido` (0 = não evadido, 1 = evadido)

### 4.2 Avaliação de Desempenho

| Métrica           | Valor  | Interpretação                          |
| ----------------- | ------ | -------------------------------------- |
| Acurácia          | 93,63% | Previsões corretas globais             |
| F1-Score          | 0,9312 | Equilíbrio entre Precisão e Recall     |
| Recall (Evasão)   | 98,70% | Capacidade de identificar evadidos     |
| Precisão (Evasão) | 88,46% | Confiabilidade das previsões de evasão |

O **Recall elevado** demonstra que o modelo minimiza falsos negativos, sendo adequado para sistemas de alerta precoce.

### 4.3 Importância das Variáveis

| Variável                     | Importância |
| ---------------------------- | ----------- |
| Tempo no curso em meses      | 0,4314      |
| Percentual de UCs aprovadas  | 0,1764      |
| UC reprovada ou não cursada  | 0,1477      |
| Quantidade de UCs reprovadas | 0,0478      |
| Quantidade de UCs aprovadas  | 0,0454      |

O **Tempo no curso** é o principal preditor, validando os achados da análise descritiva.

---

## 5. Conclusões e Recomendações

### 5.1 Principais Achados

* **Alta concentração de evasão:** 55% dos registros analisados;
* **Evasão precoce:** 98% nos primeiros 3 meses;
* **Modelo preditivo robusto:** Acurácia de 93,63% e Recall de 98,70%.

### 5.2 Estratégia de Deployment e Intervenção

| Nível de Risco | Probabilidade | Ação Recomendada                       |
| -------------- | ------------- | -------------------------------------- |
| Iminente       | > 70%         | Contato imediato e suporte direcionado |
| Alta           | 50–70%        | Acompanhamento ativo                   |
| Média          | 30–50%        | Comunicação preventiva                 |
| Baixa          | 10–30%        | Monitoramento passivo                  |
| Muito Baixa    | < 10%         | Sem ação necessária                    |

**Frequência de Monitoramento:**

* Novatos (0–3 meses): semanal;
* Alunos em risco: mensal.

### 5.3 Ações Proativas Recomendadas

* Programas de ambientação intensiva;
* Suporte acadêmico nas primeiras UCs;
* Resolução rápida de problemas institucionais e logísticos.

---

## Apêndice

### A.1 Matriz de Confusão

|        | Previsto 0 | Previsto 1 |
| ------ | ---------- | ---------- |
| Real 0 | 1.007      | 157        |
| Real 1 | 40         | 3.034      |

### A.2 Situação de Matrícula vs Motivo de Evasão (Percentual)

* **Evadido / Eliminado:** predominância de motivos Institucionais (50,48%);
* **Evadido / Desistente:** maior dispersão entre Abandono e motivos Acadêmicos.
