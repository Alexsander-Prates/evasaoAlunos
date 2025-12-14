# Análise e Modelagem Preditiva da Evasão em Cursos de Graduação

Este repositório contém um **notebook Google Colab (.ipynb)** desenvolvido como parte de um trabalho de pós-graduação, com o objetivo de analisar dados acadêmicos e construir um modelo preditivo para identificação de alunos com risco de evasão em cursos de graduação.

O notebook implementa todas as etapas do processo analítico, desde o tratamento dos dados até a avaliação de um modelo de *Machine Learning*.

---

## Objetivo do Projeto

* Analisar o fenômeno da evasão acadêmica a partir de dados reais;
* Identificar padrões e fatores críticos associados à evasão;
* Construir um modelo supervisionado capaz de predizer a evasão de alunos;
* Gerar subsídios para ações proativas de retenção acadêmica.

---

## Estrutura do Notebook

O arquivo `Trabalho_Evasão_Graduação.ipynb` está organizado nas seguintes etapas:

1. **Importação de bibliotecas**
   Carregamento das principais bibliotecas de análise de dados e aprendizado de máquina.

2. **Carregamento e entendimento dos dados**
   Leitura do dataset, inspeção inicial e análise da estrutura das variáveis.

3. **Tratamento e limpeza dos dados**

   * Remoção ou tratamento de valores nulos em colunas críticas;
   * Padronização de variáveis categóricas;
   * Criação de variáveis derivadas (features).

4. **Classificação dos motivos de evasão**
   Agrupamento dos motivos originais em categorias analíticas (abandono, acadêmico, financeiro, institucional, entre outras).

5. **Análise exploratória dos dados (EDA)**
   Geração de estatísticas descritivas e visualizações para compreensão dos padrões de evasão.

6. **Preparação dos dados para modelagem**

   * Definição da variável alvo;
   * Separação dos dados em treino e teste;
   * Seleção das variáveis preditoras.

7. **Modelagem preditiva**
   Treinamento de um modelo de **Árvore de Decisão**, priorizando interpretabilidade.

8. **Avaliação do modelo**
   Cálculo de métricas como acurácia, precisão, recall, F1-score e matriz de confusão.

9. **Análise de importância das variáveis**
   Identificação das *features* mais relevantes para a predição da evasão.

---

## Requisitos

Para executar o notebook, são necessárias as seguintes bibliotecas Python:

* pandas
* numpy
* matplotlib
* seaborn
* scikit-learn

No Google Colab, todas as dependências já estão disponíveis por padrão.

---

## Como Executar no Google Colab

1. Acesse o Google Colab: [https://colab.research.google.com/](https://colab.research.google.com/)
2. Clique em **Arquivo > Abrir notebook**;
3. Selecione a aba **Upload** e envie o arquivo `Trabalho_Evasão_Graduação.ipynb`;
4. Execute as células do notebook **em ordem sequencial**, do início ao fim;
5. Caso necessário, ajuste o caminho do dataset conforme indicado nas células de carregamento de dados.

---

## Entrada de Dados

O notebook espera um dataset estruturado contendo informações acadêmicas e administrativas dos alunos, incluindo:

* Situação de matrícula;
* Motivo de saída;
* Dados de desempenho acadêmico (UCs aprovadas, reprovadas, cursadas);
* Informações temporais (tempo no curso);
* Variáveis demográficas relevantes.

O formato esperado é tabular (CSV ou XLSX), conforme indicado no próprio notebook.

---

## Saídas e Resultados

Ao final da execução, o notebook produz:

* Estatísticas descritivas da evasão;
* Gráficos de distribuição e análise exploratória;
* Métricas de desempenho do modelo preditivo;
* Matriz de confusão;
* Ranking de importância das variáveis;
* Interpretação dos resultados para apoio à tomada de decisão.

---

## Observações Importantes

* O modelo foi desenvolvido com foco em **alta sensibilidade (recall)** para a classe de evasão;
* A principal variável preditora identificada é o **tempo no curso**, indicando evasão precoce;
* O notebook pode ser adaptado para outros contextos institucionais com ajustes no dataset e nas regras de categorização.

---

## Licença e Uso

Este projeto possui caráter **acadêmico e educacional**. O uso dos códigos e da metodologia é livre para fins de estudo, desde que citada a fonte e respeitadas as diretrizes institucionais relacionadas à privacidade dos dados.

---

## Autores

* Erick Dias
* Werbert Wilson Severiano Chaves da Conceição
* Alexsander Prates
* Luciano Deschamps
