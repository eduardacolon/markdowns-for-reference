# Manual de Pandas: Análise de Dados com Python

> Um guia completo e prático para dominar a biblioteca mais utilizada para análise de dados em Python.

---

## Sumário

1. [O que é Pandas e Por Que Usar?](#1-o-que-é-pandas-e-por-que-usar)
2. [Instalação](#2-instalação)
3. [Importando Bibliotecas](#3-importando-bibliotecas)
4. [Carregando Dados no Pandas](#4-carregando-dados-no-pandas)
5. [Visualizando Dados](#5-visualizando-dados)
6. [Tratamento de Dados](#6-tratamento-de-dados)
7. [Criando Novas Colunas](#7-criando-novas-colunas)
8. [Selecionando Colunas](#8-selecionando-colunas)
9. [Filtrando Dados](#9-filtrando-dados)
10. [Localizando Valores Específicos (`.loc` e `.iloc`)](#10-localizando-valores-específicos-loc-e-iloc)
11. [Ordenando Dados](#11-ordenando-dados)
12. [Gestão de Índices](#12-gestão-de-índices)
13. [Análises com Agrupamento (`groupby`)](#13-análises-com-agrupamento-groupby)
14. [Mesclando Tabelas (`merge`)](#14-mesclando-tabelas-merge)
15. [Concatenando DataFrames (`concat`)](#15-concatenando-dataframes-concat)
16. [Análise de Séries Temporais](#16-análise-de-séries-temporais)
17. [Visualizando Tendências com Gráficos](#17-visualizando-tendências-com-gráficos)
18. [Exportando Seus Dados](#18-exportando-seus-dados)
19. [Perguntas Frequentes (FAQ)](#19-perguntas-frequentes-faq)
20. [Boas Práticas Resumidas](#20-boas-práticas-resumidas)

---

## 1. O que é Pandas e Por Que Usar?

O **Pandas** é a biblioteca Python mais utilizada na área de dados. Ela permite fazer todo o processo de **ETL** (Extract, Transform, Load):

| Etapa | Descrição |
|-------|-----------|
| **Extract (Extrair)** | Importar dados de diversas fontes (CSV, Excel, JSON, bancos de dados etc.) |
| **Transform (Transformar)** | Limpar, tratar e transformar os dados |
| **Load (Carregar)** | Preparar dados para análises e exportar resultados |

Além disso, você consegue fazer análises completas diretamente no Pandas, sem precisar de ferramentas externas.

### Por que Pandas?

- Estrutura de dados **DataFrame** (tabela com linhas e colunas) intuitiva e poderosa.
- Leitura e escrita de múltiplos formatos (CSV, Excel, JSON, SQL etc.).
- Ferramentas robustas para limpeza, filtro, agrupamento e transformação de dados.
- Integração com bibliotecas de visualização (Matplotlib, Plotly) e machine learning (Scikit-learn).
- Performance otimizada para grandes volumes de dados.

---

## 2. Instalação

### Instalando o Pandas

Abra o terminal do seu editor de código (VS Code, Google Colab, Jupyter Notebook) e execute:

```bash
pip install pandas
```

### Instalando o OpenPyXL (para Excel)

Para trabalhar com arquivos `.xlsx`, instale também a engine OpenPyXL:

```bash
pip install openpyxl
```

### Recomendação de formato

Para projetos de dados, use arquivos `.ipynb` (Jupyter Notebook) ao invés de `.py`, pois permitem executar código célula por célula, facilitam a visualização de dados e são o padrão da indústria para análise de dados.

No VS Code, instale a extensão do **Jupyter** para trabalhar com esses arquivos.

---

## 3. Importando Bibliotecas

```python
import pandas as pd
import numpy as np
```

| Biblioteca | Apelido | Função |
|-----------|---------|--------|
| **pandas** | `pd` | Manipulação e análise de dados estruturados |
| **numpy** | `np` | Operações matemáticas e computação numérica |

> `pd` e `np` são apelidos padrão aplicados pela comunidade Python.

---

## 4. Carregando Dados no Pandas

Após importar as bibliotecas, o próximo passo é carregar os dados em um **DataFrame** — uma estrutura de dados em forma de tabela com linhas e colunas.

### Lendo um CSV

```python
df_vendas = pd.read_csv("vendas.csv")
```

Convenção de nomenclatura: use `df_` como prefixo para identificar um DataFrame, por exemplo `df_vendas`.

### Parâmetros importantes do `pd.read_csv`

| Parâmetro | Descrição | Exemplo |
|-----------|-----------|---------|
| `encoding` | Codificação do arquivo (essencial para caracteres especiais como `ã`, `ç`, `é`) | `pd.read_csv('vendas.csv', encoding='utf-8')` |
| `sep` | Separador de campos (no Brasil, muitos CSVs usam `;`) | `pd.read_csv('vendas.csv', sep=';')` |
| `low_memory` | Controle de leitura de arquivos grandes. `True` lê em partes (menos memória, mas pode inferir tipos incorretamente). `False` analisa o arquivo inteiro (inferência mais consistente). | `pd.read_csv('vendas.csv', low_memory=False)` |

### Outros formatos de leitura

```python
# Excel
df = pd.read_excel('vendas.xlsx')

# JSON
df = pd.read_json('dados.json')

# SQL (exemplo com SQLite)
import sqlite3
conexao = sqlite3.connect('banco.db')
df = pd.read_sql('SELECT * FROM vendas', conexao)
```

---

## 5. Visualizando Dados

Use `display()` (em notebooks `.ipynb`) ao invés de `print()` para melhor visualização.

```python
display(df_vendas)
```

### Métodos de exploração rápida

| Método | Descrição | Exemplo |
|--------|-----------|---------|
| `head(n)` | Primeiras `n` linhas (padrão: 5) | `df_vendas.head(10)` |
| `tail(n)` | Últimas `n` linhas | `df_vendas.tail(10)` |
| `sample(n)` | `n` linhas aleatórias | `df_vendas.sample(15)` |
| `shape` | Dimensões (linhas, colunas) | `df_vendas.shape` |
| `columns` | Lista de nomes das colunas | `df_vendas.columns` |
| `info()` | Tipos de dados, valores não nulos e uso de memória | `df_vendas.info()` |
| `describe()` | Estatísticas descritivas das colunas numéricas (média, desvio padrão, mínimo, máximo, quartis) | `df_vendas.describe()` |

---

## 6. Tratamento de Dados

O tratamento de dados é uma das fases mais críticas da análise, pois garante que as informações estejam consistentes, completas e prontas para gerar insights confiáveis.

### 6.1 Excluindo Colunas Inúteis

```python
df_analise = df_vendas.drop(columns=['data_base'])
```

- `df_vendas`: DataFrame original.
- `.drop()`: método para remover linhas ou colunas.
- `columns=['data_base']`: coluna a ser removida.
- `df_analise`: novo DataFrame sem essa coluna (o original não é alterado).

### 6.2 Tratando Valores Vazios (NaN)

#### Opção 1: Remover linhas com valores vazios

Indicado quando a quantidade de dados faltantes é pequena.

```python
df_analise = df_analise.dropna()
```

#### Opção 2: Preencher valores vazios

Útil quando é importante manter todas as linhas.

```python
df_analise['loja'] = df_analise['loja'].fillna('Online')
```

### 6.3 Corrigindo Tipos de Dados

Converter textos para o tipo `datetime`:

```python
df_analise['data'] = pd.to_datetime(df_analise['data'], format='%Y-%m-%d')
```

- `pd.to_datetime()`: converte textos para o tipo `datetime`.
- `format='%Y-%m-%d'`: define o formato da data (ano-mês-dia).

> Consulte a [documentação do Pandas](https://pandas.pydata.org/docs/reference/api/pandas.to_datetime.html) para outros formatos de data.

### 6.4 Padronização de Textos

```python
df_analise['loja'] = df_analise['loja'].str.strip().str.title()
```

| Método | Função |
|--------|--------|
| `.str.strip()` | Remove espaços em branco no início e no fim |
| `.str.title()` | Coloca a primeira letra de cada palavra em maiúscula |

### 6.5 Removendo Duplicatas

```python
# Remover linhas completamente duplicadas
df_analise = df_analise.drop_duplicates()
```

```python
# Remover duplicatas baseadas em uma coluna específica
df_analise = df_analise.drop_duplicates(subset=['id_pedido'], keep='first')
```

| Valor de `keep` | Comportamento |
|-----------------|---------------|
| `'first'` | Mantém a primeira ocorrência |
| `'last'` | Mantém a última ocorrência |
| `False` | Remove todas as duplicatas |

---

## 7. Criando Novas Colunas

Criar novas colunas significa gerar dados a partir de informações já existentes, permitindo análises mais completas.

### 7.1 Operações diretas entre colunas

```python
df_analise['faturamento'] = df_analise['quantidade'] * df_analise['preco_unitario']
```

O operador `*` é aplicado linha a linha (operação **vetorizada**).

### 7.2 Usando condicionais (`np.where`)

```python
df_analise['forma_venda'] = np.where(
    df_analise['loja'] == 'Online',
    'Online',
    'Presencial'
)
```

- `np.where()` funciona como um `if/else` vetorizado.
- Primeiro parâmetro: a condição.
- Segundo parâmetro: valor se a condição for **verdadeira**.
- Terceiro parâmetro: valor se a condição for **falsa**.

### 7.3 Usando um dicionário (`map`)

```python
dic_regioes = {
    'São Paulo': 'Sudeste',
    'Rio de Janeiro': 'Sudeste',
    'Belo Horizonte': 'Sudeste',
    'Salvador': 'Nordeste',
    'Recife': 'Nordeste',
    'Curitiba': 'Sul',
    'Porto Alegre': 'Sul',
    'Online': 'Online'
}

df_analise['regiao'] = df_analise['loja'].map(dic_regioes)
```

- `.map()` pega cada valor da coluna e procura como chave no dicionário, retornando o valor correspondente.

---

## 8. Selecionando Colunas

### Coluna única (retorna uma Série)

```python
df_analise['loja']
```

### Múltiplas colunas (retorna um DataFrame)

```python
df_analise[['loja', 'produto', 'faturamento']]
```

> Dica: use colchetes duplos `[[ ]]` para múltiplas colunas — colchetes simples `[ ]` retornam uma Série.

---

## 9. Filtrando Dados

### Filtro simples

```python
df_vendas_sp = df_analise[df_analise['loja'] == 'São Paulo']
```

### Múltiplas condições

#### Operador `&` (E lógico)

```python
df_filtrado = df_analise[
    (df_analise['produto'] == 'Cabo HDMI') &
    (df_analise['regiao'] == 'Sul')
]
```

#### Operador `|` (OU lógico)

```python
df_filtrado = df_analise[
    (df_analise['produto'] == 'Mouse') |
    (df_analise['regiao'] == 'Nordeste')
]
```

> Importante: cada condição deve estar entre parênteses `()` antes de usar `&` ou `|`.

### Filtros por data

```python
# Filtrar por ano (requer coluna 'data' no formato datetime)
df_2024 = df_analise[df_analise['data'].dt.year == 2024]

# Filtrar vendas a partir de uma data específica
df_filtrado = df_analise[df_analise['data'] >= '2024-01-01']
```

---

## 10. Localizando Valores Específicos (`.loc` e `.iloc`)

### `.loc` — acesso por nome (rótulo)

Ideal quando você conhece o nome da coluna ou do índice.

```python
# Acessar valor na linha de índice 3 e coluna 'loja'
loja = df_analise.loc[3, 'loja']

# Localizar a 'loja' de um ID específico e extrair apenas o valor
loja_id4 = df_analise.loc[df_analise['id_pedido'] == 4, 'loja'].values[0]
```

### `.iloc` — acesso por posição (inteiro)

Funciona como um sistema de coordenadas, independente dos nomes das colunas ou índices.

```python
# Acessar a primeira linha (0) e a terceira coluna (2)
valor = df_analise.iloc[0, 2]
```

| Método | Acesso por | Exemplo |
|--------|------------|---------|
| `.loc` | Nome do índice/coluna | `df.loc[3, 'loja']` |
| `.iloc` | Posição numérica | `df.iloc[0, 2]` |

---

## 11. Ordenando Dados

### Ordenação crescente (padrão)

```python
df_analise = df_analise.sort_values(by='faturamento')
```

### Ordenação decrescente

```python
df_analise = df_analise.sort_values(by='faturamento', ascending=False)
```

### Múltiplas colunas

```python
df_analise = df_analise.sort_values(
    by=['data', 'faturamento'],
    ascending=[True, False]   # data crescente, faturamento decrescente
)
```

> `ascending` pode ser um único booleano (aplica a todas as colunas) ou uma lista com um valor por coluna.

---

## 12. Gestão de Índices

Quando ordenamos ou removemos linhas, o índice original permanece vinculado à sua linha de origem, gerando um índice "embaralhado".

### Resetar o índice

```python
df_analise = df_analise.reset_index(drop=True)
```

- `drop=True`: evita que o índice antigo seja transformado em uma nova coluna.
- Resultado: índice sequencial (0, 1, 2, 3...) refletindo a nova ordem.

---

## 13. Análises com Agrupamento (`groupby`)

O `groupby()` permite agrupar dados por uma categoria e aplicar operações (soma, média, contagem etc.) em cada grupo.

### Conceito

```
DataFrame → groupby(coluna) → operação (sum, mean, count...)
```

> Importante: selecione apenas as colunas relevantes antes do `groupby` para evitar erros ao tentar somar colunas de texto.

### Exemplo: Faturamento total por loja

```python
analise_lojas = (
    df_analise[['loja', 'faturamento']]
    .groupby('loja')
    .sum()
    .sort_values(by='faturamento', ascending=False)
    .rename(columns={'faturamento': 'Vendas totais'})
    .reset_index()
)
```

### Funções após `groupby`

| Função | Descrição | Exemplo |
|--------|-----------|---------|
| `.sum()` | Soma dos valores | `df.groupby('loja')['faturamento'].sum()` |
| `.mean()` | Média dos valores | `df.groupby('loja')['faturamento'].mean()` |
| `.max()` | Valor máximo | `df.groupby('loja')['faturamento'].max()` |
| `.min()` | Valor mínimo | `df.groupby('loja')['faturamento'].min()` |
| `.count()` | Contagem de registros | `df.groupby('loja')['produto'].count()` |
| `.describe()` | Estatísticas completas | `df.groupby('loja')['faturamento'].describe()` |

### Agrupamento por múltiplas colunas

```python
analise_produto_em_lojas = (
    df_analise[['loja', 'produto', 'quantidade']]
    .groupby(['loja', 'produto'])
    .sum()
)
```

### Exibir todas as linhas do resultado

O Pandas limita a exibição de linhas por padrão. Use `pd.option_context` para exibir todas:

```python
with pd.option_context('display.max_rows', None):
    display(analise_produto_em_lojas)
```

> O bloco `with` cria um contexto temporário: a configuração vale apenas dentro dele e o Pandas retorna ao padrão automaticamente após.

---

## 14. Mesclando Tabelas (`merge`)

O `merge()` combina duas tabelas baseando-se em uma coluna em comum (similar ao JOIN do SQL).

### Sintaxe básica

```python
df_completo = df_vendas.merge(df_gerentes, on='loja', how='left')
```

### Parâmetros do `merge`

| Parâmetro | Descrição |
|-----------|-----------|
| `on='loja'` | Coluna em comum usada para a correspondência |
| `how='left'` | Tipo de join (veja tabela abaixo) |
| `left_on='loja'` | Nome da coluna na tabela da **esquerda** |
| `right_on='cidade'` | Nome da coluna na tabela da **direita** (use quando os nomes forem diferentes) |

### Tipos de `how` (JOIN)

| Tipo | Comportamento |
|------|---------------|
| `'inner'` | Mantém apenas linhas com correspondência em **ambas** as tabelas |
| `'left'` | Mantém **todas** as linhas da esquerda; preenche com `NaN` onde não houver correspondência |
| `'right'` | Oposto do `left` |
| `'outer'` | Mantém **todas** as linhas de ambas as tabelas; preenche com `NaN` onde não houver correspondência |

### Nomes de colunas diferentes

Quando a coluna em comum tem nomes diferentes em cada tabela:

```python
df_completo = df_vendas.merge(
    df_gerentes,
    left_on='loja',      # nome na tabela da esquerda
    right_on='cidade',   # nome na tabela da direita
    how='left'
)
```

> A "tabela da esquerda" é a primeira mencionada (`df_vendas`), e a "da direita" é a segunda (`df_gerentes`).

---

## 15. Concatenando DataFrames (`concat`)

Diferente do `merge()` que une tabelas **lado a lado**, o `concat()` **empilha** tabelas uma sobre a outra.

```python
df_completo = pd.concat([df_janeiro, df_fevereiro, df_marco], ignore_index=True)
```

- `ignore_index=True`: recria os índices sequencialmente (0, 1, 2, 3...) ao invés de manter os índices originais.
- As tabelas devem ter **colunas compatíveis** (mesmas colunas ou pelo menos colunas comuns).

### `concat` vs `merge` — quando usar cada um

| Use `concat` quando | Use `merge` quando |
|---------------------|--------------------|
| Mesma estrutura de dados em períodos diferentes | Informações complementares em tabelas diferentes |
| Quer "empilhar" linhas uma sobre a outra | Precisa "cruzar" dados baseado em uma chave comum |
| Consolidando dados de múltiplas fontes com o mesmo formato | Enriquecendo uma tabela com dados de outra |

---

## 16. Análise de Séries Temporais

A análise temporal permite entender tendências, sazonalidades e padrões ao longo do tempo.

### Criando colunas de período

```python
df_analise['mes_ano'] = df_analise['data'].dt.to_period('M')
```

### Parâmetros de `.to_period()`

| Valor | Tipo de Período | Exemplo |
|-------|----------------|---------|
| `'M'` | Mensal | `2024-01` |
| `'Q'` | Trimestral | `2024Q1` |
| `'Y'` | Anual | `2024` |
| `'W'` | Semanal | — |

### Agrupando por período

```python
df_vendas_mes = df_analise[['mes_ano', 'faturamento']].groupby('mes_ano').sum()
```

### Outros atributos temporais

```python
df_analise['ano'] = df_analise['data'].dt.year
df_analise['mes'] = df_analise['data'].dt.month
df_analise['dia_semana'] = df_analise['data'].dt.day_name()
df_analise['trimestre'] = df_analise['data'].dt.quarter
```

---

## 17. Visualizando Tendências com Gráficos

### Gráfico rápido com o Pandas + Matplotlib

```python
df_vendas_mes.plot()
```

Gera automaticamente um gráfico com a evolução das vendas mês a mês.

### Gráficos profissionais com Plotly

Para visualizações mais profissionais e interativas, use a biblioteca **Plotly**:

```python
import plotly.express as px

fig = px.line(df_vendas_mes.reset_index(), x='mes_ano', y='faturamento', title='Vendas por Mês')
fig.show()
```

> O `.plot()` do Pandas é ótimo para análises exploratórias rápidas, mas para apresentações finais, use bibliotecas especializadas como o Plotly.

---

## 18. Exportando Seus Dados

### Exportar para CSV

```python
df_analise.to_csv('analise_vendas.csv', index=False, encoding='utf-8-sig')
```

| Parâmetro | Motivo |
|-----------|--------|
| `index=False` | Evita que o Pandas adicione uma coluna extra com os índices numéricos |
| `encoding='utf-8-sig'` | Garante que caracteres acentuados sejam exibidos corretamente no Excel |

### Exportar para Excel

```python
df_analise.to_excel('analise_vendas.xlsx', index=False, sheet_name='Vendas')
```

| Parâmetro | Motivo |
|-----------|--------|
| `index=False` | Não exporta o índice como coluna |
| `sheet_name='Vendas'` | Nome personalizado da aba |

> ⚠️ **Erro comum**: formatar dados muito cedo. Transformar valores numéricos em texto com símbolos de moeda impede cálculos futuros. Mantenha dados em formato numérico durante toda a análise. A formatação visual deve ser aplicada apenas no momento final, em uma cópia do DataFrame destinada à apresentação.

---

## 19. Perguntas Frequentes (FAQ)

### 1. Como instalar o Pandas?

```bash
pip install pandas
```

Para trabalhar com Excel, instale também:

```bash
pip install openpyxl
```

Depois, importe com `import pandas as pd`.

### 2. O que é um DataFrame?

O DataFrame é a principal estrutura de dados do Pandas: uma tabela com linhas e colunas, parecida com uma planilha do Excel. Ele organiza as informações de forma estruturada, facilitando a leitura, o tratamento, o filtro e a análise dos dados.

### 3. Como carregar um arquivo CSV?

```python
pd.read_csv('vendas.csv')
```

Ajuste `sep=';'` para arquivos separados por ponto e vírgula (comuns no Brasil) e `encoding='utf-8'` quando houver acentos e caracteres especiais.

### 4. Como visualizar as primeiras linhas de um DataFrame?

```python
df.head(10)     # 10 primeiras linhas
df.tail(10)     # 10 últimas linhas
df.sample(15)   # 15 linhas aleatórias
```

### 5. Como filtrar dados?

```python
df_filtrado = df_analise[df_analise['loja'] == 'São Paulo']
```

Para múltiplas condições:

```python
df_filtrado = df_analise[
    (df_analise['produto'] == 'Cabo HDMI') &
    (df_analise['regiao'] == 'Sul')
]
```

### 6. Como agrupar dados?

```python
analise = df_analise[['loja', 'faturamento']].groupby('loja').sum()
```

### 7. Como mesclar duas tabelas?

```python
df_completo = df_vendas.merge(df_gerentes, on='loja', how='left')
```

### 8. Como concatenar tabelas?

```python
df_completo = pd.concat([df_janeiro, df_fevereiro], ignore_index=True)
```

---

## 20. Boas Práticas Resumidas

| Prática | Motivo |
|---------|--------|
| Use `df_` como prefixo para DataFrames | Convenção da comunidade, torna o código legível |
| Use `display()` em notebooks | Melhor visualização que `print()` |
| Sempre defina `index=False` ao exportar | Evita coluna de índice desnecessária |
| Use `encoding='utf-8-sig'` ao exportar CSV para Excel | Caracteres acentuados são exibidos corretamente |
| Não formate dados durante a análise | Mantenha números como números; formate só no final |
| Use `low_memory=False` para arquivos grandes | Evita inferência incorreta de tipos de dados |
| Padronize textos com `.str.strip().str.title()` | Evita inconsistências em agrupamentos e filtros |
| Remova duplicatas antes de analisar | Evita distorção de resultados |
| Use `ignore_index=True` no `concat()` | Índice sequencial limpo |
| Use `with pd.option_context()` para exibir todas as linhas | Evita alterar configurações globais do Pandas |

---

## Referência Rápida de Métodos

| Categoria | Método | Função |
|-----------|--------|--------|
| **Leitura** | `pd.read_csv()` | Ler arquivo CSV |
| | `pd.read_excel()` | Ler arquivo Excel |
| | `pd.read_json()` | Ler arquivo JSON |
| **Visualização** | `.head(n)` | Primeiras `n` linhas |
| | `.tail(n)` | Últimas `n` linhas |
| | `.sample(n)` | `n` linhas aleatórias |
| | `.info()` | Informações do DataFrame |
| | `.describe()` | Estatísticas descritivas |
| | `.shape` | Dimensões (linhas, colunas) |
| | `.columns` | Nomes das colunas |
| **Limpeza** | `.drop(columns=[])` | Remover colunas |
| | `.dropna()` | Remover linhas com valores vazios |
| | `.fillna(valor)` | Preencher valores vazios |
| | `.drop_duplicates()` | Remover duplicatas |
| | `.str.strip()` | Remover espaços extras |
| | `.str.title()` | Capitalizar texto |
| | `pd.to_datetime()` | Converter para datetime |
| **Manipulação** | `.loc[]` | Acesso por nome |
| | `.iloc[]` | Acesso por posição |
| | `.sort_values()` | Ordenar dados |
| | `.reset_index()` | Resetar índice |
| | `.map(dic)` | Mapear valores via dicionário |
| | `.groupby()` | Agrupar dados |
| | `.merge()` | Mesclar tabelas (JOIN) |
| | `.concat()` | Concatenar tabelas (empilhar) |
| | `.sum()` | Soma |
| | `.mean()` | Média |
| | `.max()` | Máximo |
| | `.min()` | Mínimo |
| | `.count()` | Contagem |
| **Exportação** | `.to_csv()` | Exportar para CSV |
| | `.to_excel()` | Exportar para Excel |

---

*Manual gerado com base no conteúdo do curso da Hashtag Treinamentos.*
