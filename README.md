# Marketing Analytics | Power BI

## Sobre o projeto

Este projeto foi desenvolvido com o objetivo de analisar o desempenho de campanhas de marketing digital por meio de indicadores e visualizações no Power BI.

O dashboard reúne uma visão executiva dos resultados, permitindo acompanhar investimentos, comparar o desempenho entre plataformas e identificar oportunidades de melhoria.
## Visualização dos Dashboards

### 1. Visão Geral — Marketing Analytics

![Dashboard Visão Geral](Marketing_Analytics_Visao_Exec.png)

### 2. Análise de Pacing

![Dashboard de Pacing](marketing-analytics-pacing.png?versao=2)
## Objetivos

- Centralizar os principais indicadores de marketing em um único dashboard.
- Analisar a distribuição dos investimentos entre plataformas.
- Comparar investimentos e resultados das campanhas.
- Acompanhar o Pacing, identificando diferenças entre valores planejados e realizados.
- Facilitar a interpretação dos dados e apoiar a tomada de decisões.

## Indicadores analisados

- **Investimento:** Valores destinados às campanhas de marketing.
- **Impressões:** Quantidade de vezes que os anúncios foram exibidos.
- **Cliques:** Interações dos usuários com os anúncios.
- **CPC:** Custo médio por clique.
- **CPM:** Custo por mil impressões.
- **CTR:** Taxa de cliques em relação às impressões.
- **Pacing:** Acompanhamento dos investimentos em relação ao planejamento.

## Plataformas analisadas

- Meta Ads
- TikTok Ads
- YouTube Ads

## Ferramentas utilizadas

**Power BI:** Desenvolvimento dos dashboards e visualizações.

**Power Query:** Preparação, transformação e tratamento dos dados.

**DAX:** Criação de medidas e indicadores para análise dos resultados.

## Principais análises e insights

### Escopo das análises

A Visão Geral apresenta os investimentos e indicadores de desempenho das campanhas disponíveis na base analisada, totalizando aproximadamente R$ 17,09 milhões.

Já a análise de Pacing possui um recorte específico de campanhas com planejamento orçamentário, acompanhando aproximadamente R$ 1,01 milhão em investimentos planejados e R$ 1,06 milhão realizados.

Por isso, os valores apresentados nas duas páginas possuem abrangências diferentes e não devem ser comparados diretamente.

### 1. Visão Geral — Marketing Analytics

A análise apresenta um investimento total de aproximadamente R$ 17,09 milhões em campanhas de marketing, distribuídos entre Meta Ads, TikTok Ads e YouTube Ads.

**Principais observações:**

- **Meta Ads:** Concentrou aproximadamente 61% dos investimentos e apresentou o maior volume de impressões, com cerca de 1,67 bilhão.
- **TikTok Ads:** Mesmo com uma participação menor nos investimentos, apresentou o menor CPC (R$ 1,18), menor CPM (R$ 5,80) e maior CTR (0,49%), destacando-se nos indicadores de custo e interação.
- **YouTube Ads:** Apresentou os maiores custos por clique (R$ 3,62) e por mil impressões (R$ 12,16), indicando a importância de avaliar os resultados em relação aos objetivos das campanhas.

### 2. Análise de Pacing

Na análise de acompanhamento orçamentário, o investimento planejado foi de aproximadamente R$ 1,01 milhão, enquanto o realizado atingiu R$ 1,06 milhão.

O resultado representa um Pacing de 105%, ou seja, uma execução aproximadamente 5% acima do valor esperado, com desvio de cerca de R$ 50 mil.

Das 40 campanhas analisadas, 29 estavam no ritmo esperado, 6 abaixo e 5 acima, conforme os critérios de classificação adotados no dashboard.

### Conclusão

O projeto permitiu comparar o desempenho das plataformas de marketing e acompanhar a execução dos investimentos em relação ao planejamento.

Os resultados mostram a importância de analisar diferentes indicadores em conjunto, pois um maior investimento nem sempre representa maior eficiência em todos os critérios avaliados.

Além disso, o acompanhamento do Pacing ajuda a identificar desvios e direcionar a atenção às campanhas que precisam de uma análise mais detalhada.

  ## Desenvolvimento Técnico

### 1. Tratamento e transformação de dados — Power Query

Utilizei o Power Query para preparar e organizar as bases de dados antes da construção dos dashboards.

Entre as transformações realizadas, destacam-se:

- Tratamento e padronização de campos, incluindo nomes de campanhas.
- Criação de colunas personalizadas e índices auxiliares.
- Filtragem de registros e remoção de duplicidades.
- Mesclagem de consultas para integrar informações das campanhas.
- Organização dos tipos de dados e das colunas utilizadas nas análises.

### 2. Modelagem de Dados

O modelo foi estruturado utilizando quatro tabelas principais: `Planejado`, `Realizado`, `Realizado_Pacing` e `Calendario`.

Foram criados relacionamentos do tipo um para muitos (1:N), utilizando chaves de identificação dos planos e campos de data.

A tabela Calendario permite realizar análises temporais, enquanto os relacionamentos entre Planejado e Realizado_Pacing possibilitam associar os registros de execução aos respectivos planejamentos.

### 3. Medidas e cálculos DAX

Foram desenvolvidas medidas para calcular indicadores de investimento e acompanhar a execução orçamentária.

**Percentual do Orçamento Consumido**

```dax
% Orçamento Consumido =
DIVIDE(
    [Investimento Realizado Acumulado],
    [Investimento Planejado]
)
```

**Pacing**

```dax
Pacing % =
DIVIDE(
    [Investimento Realizado Acumulado],
    [Investimento Esperado Até Data]
)
```

O investimento esperado até a data é calculado considerando o orçamento de cada campanha e a proporção de seu período de veiculação transcorrido, utilizando uma distribuição linear do investimento planejado.

### Critérios de classificação do Pacing

Para facilitar o acompanhamento da execução orçamentária, desenvolvi uma medida DAX utilizando `SWITCH(TRUE())`, classificando as campanhas conforme o percentual de investimento realizado em relação ao esperado.

Foram definidos os seguintes critérios:

- **Abaixo do ritmo:** Pacing inferior a 90%.
- **No ritmo:** Pacing entre 90% e 110%, incluindo os limites.
- **Acima do ritmo:** Pacing superior a 110%.

A classificação considera uma margem de tolerância de 10% em relação ao investimento esperado e é atualizada dinamicamente conforme os filtros aplicados no dashboard.

Essa lógica permite identificar campanhas que necessitam de maior atenção e apoiar o acompanhamento da execução dos investimentos.

## Oportunidades identificadas

Com base nos resultados, identifiquei alguns pontos que merecem atenção:

- **Eficiência dos investimentos:** O TikTok Ads apresentou os menores custos por clique e por mil impressões, sendo uma oportunidade para investigar o desempenho dessa plataforma em relação aos objetivos das campanhas.
- **Distribuição do orçamento:** O Meta Ads concentrou a maior parte dos investimentos. É importante avaliar se essa distribuição está alinhada aos resultados esperados de cada canal.
- **Controle orçamentário:** Das 40 campanhas analisadas no Pacing, 11 apresentaram desvios em relação ao ritmo esperado, sendo 6 abaixo e 5 acima. Essas campanhas merecem acompanhamento para entender as causas dos desvios e avaliar possíveis ajustes.

## Origem dos Dados

A base de dados utilizada neste projeto foi disponibilizada para fins educacionais, durante uma formação e mentoria em Data Analytics.

O projeto foi desenvolvido com o objetivo de aplicar conhecimentos de tratamento, modelagem, visualização e análise de dados.

As análises, os indicadores e os dashboards apresentados foram desenvolvidos por mim, buscando transformar os dados em informações relevantes para apoiar decisões de negócio.

## Limitações da análise

Embora os indicadores permitam comparar o desempenho das plataformas, métricas como CPC, CPM e CTR não são suficientes para determinar qual canal apresenta o melhor retorno financeiro.

Para uma avaliação mais completa, seria importante considerar também conversões, receita gerada e retorno sobre o investimento.

Dessa forma, o dashboard funciona como uma ferramenta de acompanhamento e apoio à decisão, permitindo identificar tendências e oportunidades que podem ser aprofundadas em novas análises.


## Como visualizar o projeto

O arquivo `Marketing_Analytics.pbix` está disponível neste repositório.

Para visualizar o dashboard completo, faça o download do arquivo e abra utilizando o Power BI Desktop.
