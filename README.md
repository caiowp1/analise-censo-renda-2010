# Análise Exploratória de Renda — Censo Demográfico 2010 (Macapá)

Trabalho da disciplina de **Ciência de Dados** (UFAM), realizado em equipe de 3 alunos, com foco
no município de Macapá/AP comparado ao restante do país. Este repositório contém a etapa de
**qualidade de dados, análise estatística e seleção de atributos**, da qual fui o responsável
técnico individual dentro do grupo — meus colegas de equipe ficaram responsáveis pela produção
do vídeo de storytelling final, entrega separada do trabalho.

## Sobre os dados

Amostra dos microdados do Censo Demográfico 2010 (IBGE), com foco no tema **Trabalho e Rendimento**,
fornecida pela disciplina com nulos e inconsistências inseridos propositalmente para fins didáticos.
O dataset não está incluído neste repositório (arquivo do curso, não redistribuível) — apenas o
notebook com a análise.

## O que foi feito

- **Qualidade de dados**: identificação e tratamento de nulos estruturais vs. nulos residuais,
  correção de inconsistências de domínio (idade, sexo) e de erros de digitação em renda,
  remoção de duplicatas, e estratégias de imputação diferenciadas por tipo de variável
  (remoção, categoria "não informado", imputação pela mediana).
- **Análise estatística**: comparação de renda por sexo (teste de Mann-Whitney U, unicaudal,
  95% de confiança), por cor/raça, por faixa etária (com intervalos de confiança) e por nível de
  instrução (correlação de Spearman), com foco em Macapá vs. o restante do país.
- **Análise interseccional**: cruzamento de raça e sexo na distribuição de renda.
- **Engenharia e seleção de atributos**: avaliação de cardinalidade de variáveis categóricas,
  criação de faixas etárias e de renda, e ranqueamento de atributos preditivos (correlação,
  ANOVA, qui-quadrado, informação mútua, importância via Random Forest) como preparação
  para uma etapa futura de classificação.

## Principais achados

- Homens ganham significativamente mais que mulheres, tanto em Macapá quanto no restante
  do país (p ≈ 0, Mann-Whitney U).
- Existe desigualdade racial clara na renda, com disparidades ainda mais acentuadas quando
  raça e sexo são analisados em conjunto (desigualdade interseccional).
- A posição na ocupação (ex.: com carteira assinada vs. informal) é o atributo mais relevante
  para prever a faixa de renda — mais até do que o nível de instrução.

## Ferramentas

Python, Pandas, NumPy, SciPy (testes de hipótese), Seaborn/Matplotlib (visualização),
Scikit-learn (seleção de atributos, Random Forest).

## Como rodar

```bash
pip install -r requirements.txt
jupyter notebook analise_censo_macapa.ipynb
```

> Requer o arquivo `censo2010_pessoas.parquet` fornecido pela disciplina, colocado na raiz do repositório (mesmo diretório do notebook).
