# Guia Completo das Principais Bibliotecas Python

> Um guia prático e organizado das principais bibliotecas Python por categoria de uso.

---

## Sumário

1. [Introdução](#1-introdução)
2. [Manipulação e Análise de Dados](#2-manipulação-e-análise-de-dados)
   - [Pandas](#21-pandas)
   - [NumPy](#22-numpy)
   - [Polars](#23-polars)
   - [PySpark](#24-pyspark)
   - [OpenPyXL](#25-openpyxl)
3. [Inteligência Artificial e Machine Learning](#3-inteligência-artificial-e-machine-learning)
   - [Scikit-Learn](#31-scikit-learn)
   - [PyTorch e TensorFlow](#32-pytorch-e-tensorflow)
   - [LangChain](#33-langchain)
   - [Hugging Face](#34-hugging-face)
   - [Perguntas Frequentes (IA/ML)](#35-perguntas-frequentes-iaml)
4. [Automação e Web Scraping](#4-automação-e-web-scraping)
   - [Requests](#41-requests)
   - [Beautiful Soup](#42-beautiful-soup)
   - [Playwright e Selenium](#43-playwright-e-selenium)
   - [Scrapy](#44-scrapy)
   - [PyAutoGUI](#45-pyautogui)
5. [Desenvolvimento Web](#5-desenvolvimento-web)
   - [FastAPI](#51-fastapi)
   - [Django](#52-django)
   - [Flask](#53-flask)
   - [Pydantic](#54-pydantic)
6. [Visualização de Dados e Dashboards](#6-visualização-de-dados-e-dashboards)
   - [Matplotlib e Seaborn](#61-matplotlib-e-seaborn)
   - [Plotly](#62-plotly)
   - [Streamlit](#63-streamlit)
7. [Bibliotecas Utilitárias](#7-bibliotecas-utilitárias)
8. [Visão Computacional e Tratamento de Imagens](#8-visão-computacional-e-tratamento-de-imagens)
   - [OpenCV](#81-opencv)
   - [Pillow](#82-pillow)
9. [Banco de Dados](#9-banco-de-dados)
   - [SQLAlchemy](#91-sqlalchemy)
   - [SQLite](#92-sqlite)
10. [Interface Gráfica](#10-interface-gráfica)
    - [Tkinter](#101-tkinter)
    - [CustomTkinter e TtkBootstrap](#102-customtkinter-e-ttkbootstrap)
    - [Kivy](#103-kivy)
11. [Perguntas Frequentes (FAQ Geral)](#11-perguntas-frequentes-faq-geral)
12. [Conclusão](#12-conclusão)
13. [Referência Rápida por Categoria](#13-referência-rápida-por-categoria)

---

## 1. Introdução

Se você trabalha com Python ou está começando agora, provavelmente já ouviu falar de bibliotecas como Pandas, NumPy ou Flask. Mas você sabe exatamente o que cada uma faz e quando usar?

Neste guia completo, você vai conhecer as principais bibliotecas Python explicadas de forma simples e prática, organizadas por categoria de uso. Vamos mostrar quando usar cada uma, quais são as diferenças entre ferramentas similares e como elas podem resolver seus problemas do dia a dia.

### O que são bibliotecas Python?

Bibliotecas são pacotes externos instalados com `pip` que ampliam o que o Python faz, sem reescrever código já consolidado pela comunidade. Elas empacotam funções, classes e recursos prontos para você importar e usar diretamente no seu projeto.

### Como instalar uma biblioteca

```bash
pip install nome_da_biblioteca
```

> Exemplo: `pip install pandas`, `pip install requests`, `pip install flask`.

### Divisão por área

| Categoria | Bibliotecas principais |
|-----------|----------------------|
| Manipulação e Análise de Dados | Pandas, NumPy, Polars, PySpark, OpenPyXL |
| Inteligência Artificial e Machine Learning | Scikit-Learn, PyTorch, TensorFlow, LangChain, Hugging Face |
| Automação e Web Scraping | Requests, Beautiful Soup, Playwright, Selenium, Scrapy, PyAutoGUI |
| Desenvolvimento Web | FastAPI, Django, Flask, Pydantic |
| Visualização de Dados e Dashboards | Matplotlib, Seaborn, Plotly, Streamlit |
| Visão Computacional | OpenCV, Pillow |
| Banco de Dados | SQLAlchemy, SQLite |
| Interface Gráfica | Tkinter, CustomTkinter, TtkBootstrap, Kivy |
| Utilitárias | PyInstaller, SMTPLib, Pickle, PyTest |

---

## 2. Manipulação e Análise de Dados

### 2.1 Pandas

O **Pandas** é a biblioteca mais importante quando falamos de dados em Python. Se você trabalha com análise de dados, ciência de dados, engenharia de dados ou qualquer área que envolva manipulação de informações, o Pandas é essencial.

O Pandas permite importar bases de dados de diferentes formatos (Excel, CSV, SQL e muito mais), organizar essas informações em estruturas chamadas **DataFrames** (que funcionam como tabelas) e realizar análises, transformações e extrações de insights de forma eficiente.

Ele transforma operações complexas em código simples. Em vez de percorrer linha por linha de uma planilha manualmente, o Pandas processa tudo de uma vez, economizando tempo e tornando o código muito mais rápido.

#### Instalação

```bash
pip install pandas
```

#### Conceito principal — DataFrame

O DataFrame é a estrutura central do Pandas: uma tabela com linhas e colunas, parecida com uma planilha do Excel.

```python
import pandas as pd

# Ler um arquivo CSV
df = pd.read_csv('vendas.csv')

# Visualizar as primeiras linhas
df.head()
```

> Para um guia completo do Pandas, consulte o [Manual de Pandas](#) deste documento.

---

### 2.2 NumPy

O **NumPy** é a fundação sobre a qual o Pandas foi construído. Ele serve principalmente para **operações matemáticas e matriciais** em Python.

Permite trabalhar com arrays (listas numéricas) de forma extremamente eficiente, realizando cálculos matemáticos complexos em alta velocidade.

O NumPy foi escrito em **C**, uma linguagem muito mais rápida que Python puro. Por isso, quando você faz operações com milhões de números, o NumPy consegue processar tudo rapidamente.

#### Instalação

```bash
pip install numpy
```

#### Conceito principal — ndarray

```python
import numpy as np

# Criar um array
array = np.array([1, 2, 3, 4, 5])

# Operações vetorizadas
dobro = array * 2         # [2, 4, 6, 8, 10]
soma = array.sum()        # 15
media = array.mean()      # 3.0

# Matrizes
matriz = np.array([[1, 2], [3, 4]])
```

#### Quando usar NumPy vs Pandas

| Use NumPy quando | Use Pandas quando |
|-----------------|------------------|
| Operações matemáticas puras | Dados estruturados em tabela |
| Vetores e matrizes | Análise de dados com rótulos |
| Algoritmos científicos | Limpeza, filtro e agrupamento de dados |
| Computação numérica de alta performance | Leitura de arquivos CSV/Excel |

---

### 2.3 Polars

O **Polars** é o concorrente mais moderno do Pandas, construído em **Rust** para ser ainda mais rápido. Ele usa processamento paralelo e técnicas modernas de otimização, tornando-o ideal para bases de dados muito grandes onde o Pandas pode travar seu computador.

#### Instalação

```bash
pip install polars
```

#### Quando usar Polars

- Se você está trabalhando com **milhões de linhas** e o Pandas está lento.
- Se precisa de **processamento paralelo** automático.

> Caso contrário, fique com o Pandas, que tem muito mais recursos e uma comunidade maior.

#### Comparação rápida

| Característica | Pandas | Polars |
|---------------|--------|--------|
| Linguagem base | Python/C | Rust |
| Velocidade | Boa | Muito superior em dados grandes |
| Processamento paralelo | Limitado | Nativo |
| Comunidade e recursos | Muito grande | Em crescimento |
| Curva de aprendizado | Baixa (padrão) | Média |

---

### 2.4 PySpark

O **PySpark** é a ferramenta padrão para trabalhar com **Big Data**. Ele consegue dividir tarefas entre vários computadores ao mesmo tempo (**processamento distribuído**). Isso significa que, em vez de um computador processar tudo sozinho, você pode usar a capacidade de vários computadores trabalhando juntos.

#### Instalação

```bash
pip install pyspark
```

#### Quando usar PySpark

- Suas bases de dados são tão grandes (terabytes) que o Pandas ou Polars não conseguem processar.
- Você precisa de processamento distribuído em clusters.
- Está trabalhando em ambiente Hadoop ou cloud (AWS EMR, Google Dataproc).

> Se seus dados cabem na memória do seu computador, comece com Pandas ou Polars.

---

### 2.5 OpenPyXL

Se sua empresa ainda trabalha muito com Excel e você quer automatizar planilhas mantendo a **formatação visual**, o OpenPyXL é a escolha certa.

#### Instalação

```bash
pip install openpyxl
```

#### Diferença entre OpenPyXL e Pandas para Excel

| | Pandas | OpenPyXL |
|-|--------|----------|
| Formatação visual | Ignora (cores, fórmulas, fontes) | Mantém e edita |
| Uso principal | Análise de dados brutos | Automação de planilhas |
| Velocidade | Rápida para dados brutos | Mais lenta, mas completa |

```python
import openpyxl

# Abrir uma planilha
wb = openpyxl.load_workbook('relatorio.xlsx')
ws = wb.active

# Editar uma célula mantendo a formatação
ws['A1'] = 'Novo valor'

# Salvar
wb.save('relatorio_atualizado.xlsx')
```

---

## 3. Inteligência Artificial e Machine Learning

### 3.1 Scikit-Learn

O **Scikit-Learn** é a principal biblioteca para criar modelos de **Machine Learning** em Python. Com ele é possível:

- Prever valores (ex: preços de casas)
- Classificar informações (ex: identificar spam em e-mails)
- Agrupar dados semelhantes (ex: segmentação de clientes)

Ele é bastante utilizado para implementar os principais algoritmos de Machine Learning de forma simples e intuitiva, permitindo que você crie modelos poderosos com poucas linhas de código.

#### Instalação

```bash
pip install scikit-learn
```

#### Exemplo prático

```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression

# Dividir dados em treino e teste
X_treino, X_teste, y_treino, y_teste = train_test_split(X, y, test_size=0.2)

# Criar e treinar modelo
modelo = LinearRegression()
modelo.fit(X_treino, y_treino)

# Fazer previsões
previsoes = modelo.predict(X_teste)
```

---

### 3.2 PyTorch e TensorFlow

Essas são as duas bibliotecas que permitiram o crescimento explosivo das **IAs generativas** que temos atualmente. Ambas permitem criar **redes neurais profundas (Deep Learning)** para tarefas complexas como reconhecimento de imagem, processamento de linguagem natural e criação de IAs como o ChatGPT.

#### Qual a diferença?

| | PyTorch | TensorFlow |
|-|---------|------------|
| Uso principal | Pesquisa acadêmica e desenvolvimento | Produção em larga escala |
| Curva de aprendizado | Mais intuitivo | Mais complexo |
| Comunidade | Muito forte na academia | Muito forte na indústria |
| Ecossistema | PyTorch ecosystem | TensorFlow Extended (TFX) |

```python
# Exemplo conceitual com PyTorch
import torch
import torch.nn as nn

# Definir uma rede neural simples
modelo = nn.Sequential(
    nn.Linear(10, 5),
    nn.ReLU(),
    nn.Linear(5, 1)
)
```

```python
# Exemplo conceitual com TensorFlow
import tensorflow as tf

modelo = tf.keras.Sequential([
    tf.keras.layers.Dense(5, activation='relu', input_shape=(10,)),
    tf.keras.layers.Dense(1)
])
```

---

### 3.3 LangChain

O **LangChain** é o padrão do mercado para integrar **modelos de linguagem (LLMs)** como ChatGPT, Gemini e Claude em suas aplicações, principalmente para criar sistemas **RAG** (Retrieval-Augmented Generation) — modelos que utilizam informações que não são nativas daquele modelo de linguagem, como PDFs e bases de dados da sua empresa.

#### Instalação

```bash
pip install langchain
```

#### O que o LangChain faz?

- Padroniza o processo de uso de IAs: conectar com a API do modelo, gerenciar memória, processar documentos e criar agentes de IA.
- Permite criar fluxos de trabalho complexos com LLMs em poucas linhas.

---

### 3.4 Hugging Face

O **Hugging Face** funciona como uma **loja de modelos de IA**. Nele há milhares de modelos prontos para:

- Tradução
- Transcrição de áudio
- Geração de imagens
- Análise de sentimentos
- Classificação de texto
- E muito mais

#### Instalação

```bash
pip install transformers
```

#### Exemplo de uso

```python
from transformers import pipeline

# Usar um modelo pré-treinado para análise de sentimentos
classificador = pipeline('sentiment-analysis')
resultado = classificador('Eu adorei este produto!')
# [{'label': 'POSITIVE', 'score': 0.9998}]
```

> O Hugging Face é também uma plataforma colaborativa onde a comunidade compartilha modelos, datasets e espaços (demos interativas).

---

### 3.5 Perguntas Frequentes (IA/ML)

**1. Qual biblioteca usar para começar em Machine Learning?**

Comece com o **Scikit-Learn**. Ele é o mais intuitivo para iniciantes e cobre os algoritmos clássicos de ML.

**2. Qual a diferença entre PyTorch e TensorFlow para Deep Learning?**

Use **PyTorch** para pesquisa e prototipagem (é mais intuitivo). Use **TensorFlow** para deploy em produção (é mais otimizado para ambientes de produção).

**3. Preciso de GPU para usar essas bibliotecas?**

Para treinar modelos de Deep Learning com dados grandes, sim. Para Scikit-Learn com dados pequenos/médios, não é necessário.

---

## 4. Automação e Web Scraping

### 4.1 Requests

A biblioteca **Requests** é a forma mais usada de fazer requisições HTTP em Python. Ela permite que seu código Python se conecte com sites e APIs da internet para buscar ou enviar informações.

#### Instalação

```bash
pip install requests
```

#### Exemplo prático

```python
import requests

# Fazer uma requisição GET a uma API
response = requests.get('https://api.exemplo.com/dados')
dados = response.json()

# Fazer uma requisição POST
response = requests.post('https://api.exemplo.com/enviar', json={'nome': 'João'})
```

---

### 4.2 Beautiful Soup

O **Beautiful Soup** organiza e limpa o código HTML de sites para você extrair informações específicas.

O fluxo típico é:
1. Faça uma requisição com `Requests`
2. Receba o código HTML do site
3. Use `Beautiful Soup` para filtrar e extrair apenas as informações que precisa (preços de produtos, informações de contato, notícias etc.)

#### Instalação

```bash
pip install beautifulsoup4
```

#### Exemplo prático

```python
import requests
from bs4 import BeautifulSoup

# 1. Fazer requisição
response = requests.get('https://siteexemplo.com/produtos')
html = response.text

# 2. Parsear o HTML
soup = BeautifulSoup(html, 'html.parser')

# 3. Extrair informações
precos = soup.find_all('span', class_='preco')
for preco in precos:
    print(preco.text)
```

---

### 4.3 Playwright e Selenium

Tanto o **Playwright** quanto o **Selenium** permitem automatizar interações com navegadores web.

#### Diferença entre Playwright e Selenium

| | Playwright | Selenium |
|-|-----------|----------|
| Velocidade | Mais rápido | Mais lento |
| Manutenção | Mais moderno, menos bugs | Mais maduro, mais recursos |
| Suporte de navegador | Chrome, Firefox, Safari | Chrome, Firefox, Safari, Edge |
| Uso recomendado | Projetos novos | Projetos existentes |

#### Exemplos de uso

- Preencher formulários automaticamente
- Fazer login em sites
- Navegar por páginas
- Extrair dados de sites dinâmicos (YouTube, sites com JavaScript)

```python
# Exemplo com Playwright
from playwright.sync_api import sync_playwright

with sync_playwright() as p:
    browser = p.chromium.launch()
    page = browser.new_page()
    page.goto('https://siteexemplo.com')
    page.fill('input[name="busca"]', 'Python')
    page.click('button[type="submit"]')
    browser.close()
```

---

### 4.4 Scrapy

O **Scrapy** é feito para raspagem de dados em **larga escala**. Enquanto o Beautiful Soup processa um site por vez, o Scrapy consegue fazer requisições paralelas para centenas ou milhares de sites simultaneamente.

#### Instalação

```bash
pip install scrapy
```

#### Quando usar Scrapy

- Quando você precisa extrair dados de **muitos sites** ao mesmo tempo.
- Quando precisa de um framework estruturado para raspagem ( spiders, middlewares, pipelines).
- Para projetos de raspagem em larga escala e contínua.

> Se você só precisa raspar um ou poucos sites, comece com Requests + Beautiful Soup. Migre para Scrapy quando precisar de escala.

---

### 4.5 PyAutoGUI

O **PyAutoGUI** controla o **mouse e teclado** do seu computador automaticamente. Com esta ferramenta, qualquer tarefa repetitiva que você faz no computador pode ser automatizada:

- Clicar em botões
- Digitar textos
- Preencher formulários
- Mover o mouse
- Tirar screenshots

#### Instalação

```bash
pip install pyautogui
```

#### Exemplo prático

```python
import pyautogui
import time

# Abrir o navegador
pyautogui.click(100, 100)       # Clicar na posição (x=100, y=100)
pyautogui.write('Python')        # Digitar texto
pyautogui.press('enter')         # Pressionar tecla
time.sleep(2)
```

> Útil para automatizar processos que não têm API disponível. Use com cuidado — o PyAutoGUI controla o mouse e teclado reais do seu computador.

---

## 5. Desenvolvimento Web

### 5.1 FastAPI

O **FastAPI** é a biblioteca mais moderna para criar **APIs** em Python. Ela suporta processamento **assíncrono**, permitindo que sua API responda a milhares de requisições simultâneas de forma eficiente.

#### Instalação

```bash
pip install fastapi uvicorn
```

#### Exemplo prático

```python
from fastapi import FastAPI

app = FastAPI()

@app.get('/')
def saudacao():
    return {'mensagem': 'Olá, mundo!'}

@app.get('/produtos/{id}')
def buscar_produto(id: int):
    return {'id': id, 'nome': 'Produto Exemplo'}
```

> Execute com: `uvicorn main:app --reload`

#### Por que FastAPI?

- **Performance**: um dos frameworks Python mais rápidos.
- **Documentação automática**: gera docs interativas (Swagger UI) automaticamente.
- **Validação de dados**: usa Pydantic para validar tipos.
- **Assíncrono**: suporte nativo a `async/await`.

---

### 5.2 Django

O **Django** é o framework mais completo para criar sites com Python. O próprio Instagram é feito com Django.

Com o Django você tem acesso a:

- Sistemas de autenticação de usuários
- Painel administrativo automático
- Conexão com banco de dados
- Sistemas de templates
- Segurança integrada (proteção contra CSRF, SQL injection etc.)

#### Instalação

```bash
pip install django
django-admin startproject meu_projeto
cd meu_projeto
python manage.py runserver
```

#### Quando usar Django

- Projetos web grandes e complexos
- Quando você precisa de muitas funcionalidades prontas (admin, auth, ORM)
- Aplicações com banco de dados relacional

---

### 5.3 Flask

O **Flask** é um micro-framework, muito mais simples que o Django, em que você insere as funcionalidades conforme precisar. Ele é leve e fácil de aprender, perfeito para iniciantes ou projetos pequenos.

#### Instalação

```bash
pip install flask
```

#### Exemplo prático

```python
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return 'Olá, mundo!'

@app.route('/produtos')
def produtos():
    return {'produtos': ['Camiseta', 'Calça', 'Tênis']}

if __name__ == '__main__':
    app.run(debug=True)
```

#### Quando usar Flask

- Projetos pequenos e rápidos
- APIs simples
- Microsserviços
- Quando você quer controle total sobre cada componente

---

### 5.4 Pydantic

O **Pydantic** valida dados automaticamente. Em aplicações web, recebemos dados de várias fontes (API, formulários, arquivos). O Pydantic garante que esses dados estão no formato correto antes de processar, evitando erros.

#### Instalação

```bash
pip install pydantic
```

#### Exemplo prático

```python
from pydantic import BaseModel, ValidationError

class Produto(BaseModel):
    nome: str
    preco: float
    quantidade: int

# Validação automática
try:
    produto = Produto(nome='Camiseta', preco=49.90, quantidade=10)
    print(produto.nome)      # 'Camiseta'
    print(produto.preco)     # 49.90
except ValidationError as e:
    print(e)
```

> Usado principalmente em conjunto com **FastAPI**, mas funciona com qualquer framework.

---

## 6. Visualização de Dados e Dashboards

### 6.1 Matplotlib e Seaborn

Essas são as bibliotecas clássicas para criar gráficos em Python.

#### Matplotlib

O **Matplotlib** é muito flexível e permite controle total sobre cada elemento do gráfico, mas seus gráficos não são bonitos por padrão.

```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4, 5]
y = [10, 20, 15, 30, 25]

plt.plot(x, y)
plt.title('Vendas Mensais')
plt.xlabel('Mês')
plt.ylabel('Faturamento (R$)')
plt.show()
```

#### Seaborn

O **Seaborn** cria gráficos mais visuais e atrativos automaticamente, pois é construído sobre o Matplotlib com estilos pré-definidos.

```python
import seaborn as sns

sns.barplot(x=['Jan', 'Fev', 'Mar'], y=[1000, 1500, 1200])
plt.title('Vendas por Mês')
plt.show()
```

#### Quando usar cada um

| | Matplotlib | Seaborn |
|-|------------|---------|
| Controle | Total | Limitado |
| Estética | Básica | Mais bonita por padrão |
| Complexidade | Mais código | Menos código |
| Tipos de gráfico | Todos | Focados em dados estatísticos |

---

### 6.2 Plotly

O **Plotly** cria gráficos **interativos** por padrão: você pode passar o mouse, dar zoom, clicar em legendas para mostrar/esconder dados.

#### Instalação

```bash
pip install plotly
```

#### Exemplo prático

```python
import plotly.express as px

fig = px.line(
    df_vendas_mes,
    x='mes_ano',
    y='faturamento',
    title='Evolução de Vendas'
)
fig.show()
```

#### Quando usar Plotly

- Dashboards interativos
- Apresentações e relatórios interativos
- Quando precisa de gráficos que o usuário pode explorar

---

### 6.3 Streamlit

O **Streamlit** permite criar aplicações web de dados em minutos. Você escreve código Python puro e o Streamlit transforma automaticamente em um site bonito e interativo, sem precisar saber HTML, CSS ou JavaScript.

#### Instalação

```bash
pip install streamlit
```

#### Exemplo prático

```python
import streamlit as st
import pandas as pd

st.title('Dashboard de Vendas')

df = pd.read_csv('vendas.csv')
st.dataframe(df)

# Gráfico interativo
st.bar_chart(df['faturamento'])
```

#### Execute com

```bash
streamlit run app.py
```

#### Quando usar Streamlit

- Compartilhar análises de dados com a equipe rapidamente
- Prototipar dashboards sem desenvolver frontend
- Demonstrar modelos de Machine Learning

---

## 7. Bibliotecas Utilitárias

### PyInstaller

Transforma seu código Python em um **arquivo executável**. Com ele, a pessoa pode clicar duas vezes no arquivo e usar seu programa, sem precisar ter Python instalado.

```bash
pip install pyinstaller
pyinstaller --onefile meu_script.py
```

### SMTPLib e Email

Bibliotecas padrão do Python para enviar e-mails automaticamente.

```python
import smtplib
from email.mime.text import MIMEText

msg = MIMEText('Corpo do e-mail')
msg['Subject'] = 'Assunto'
msg['From'] = 'remetente@email.com'
msg['To'] = 'destinatario@email.com'

with smtplib.SMTP('smtp.gmail.com', 587) as server:
    server.starttls()
    server.login('usuario', 'senha')
    server.send_message(msg)
```

### Pickle

Salva qualquer objeto Python em um arquivo. Por exemplo, você treinou um modelo de Machine Learning que demorou 3 horas. Com o Pickle, você salva esse modelo treinado e pode carregá-lo em segundos depois.

```python
import pickle

# Salvar
with open('modelo.pkl', 'wb') as f:
    pickle.dump(modelo_treinado, f)

# Carregar
with open('modelo.pkl', 'rb') as f:
    modelo = pickle.load(f)
```

> `wb` (write binary) e `rb` (read binary) são essenciais — o Pickle precisa de modo binário.

### PyTest

Biblioteca padrão para criar **testes automatizados** em Python que garantem que o código funciona corretamente.

```bash
pip install pytest
```

```python
# test_soma.py
def soma(a, b):
    return a + b

def test_soma():
    assert soma(2, 3) == 5
    assert soma(-1, 1) == 0

# Execute com: pytest test_soma.py
```

---

## 8. Visão Computacional e Tratamento de Imagens

### 8.1 OpenCV

O **OpenCV** é a principal biblioteca para **visão computacional** em Python. Com ela você pode:

- Rastrear objetos em vídeos
- Realizar reconhecimento facial
- Detectar movimento
- Fazer processamento de imagens em tempo real

#### Instalação

```bash
pip install opencv-python
```

#### Exemplo prático

```python
import cv2

# Ler uma imagem
imagem = cv2.imread('foto.jpg')

# Converter para escala de cinza
imagem_cinza = cv2.cvtColor(imagem, cv2.COLOR_BGR2GRAY)

# Detectar faces
detector = cv2.CascadeClassifier('haarcascade_frontalface.xml')
faces = detector.detectMultiScale(imagem_cinza)

# Desenhar retângulos nas faces detectadas
for (x, y, w, h) in faces:
    cv2.rectangle(imagem, (x, y), (x+w, y+h), (0, 255, 0), 2)

cv2.imshow('Faces', imagem)
cv2.waitKey(0)
```

---

### 8.2 Pillow

O **Pillow** é usado para **edições simples** de imagens sem a complexidade do OpenCV. Ele permite:

- Converter formatos (PNG para JPG)
- Redimensionar imagens
- Aplicar filtros
- Processar imagens em lote

#### Instalação

```bash
pip install pillow
```

#### Exemplo prático

```python
from PIL import Image, ImageFilter

# Abrir imagem
img = Image.open('foto.jpg')

# Redimensionar
img_pequena = img.resize((200, 200))

# Aplicar filtro
img_blur = img.filter(ImageFilter.BLUR)

# Converter formato e salvar
img.save('foto.png')

# Processar em lote
import os
for arquivo in os.listdir('fotos/'):
    img = Image.open(f'fotos/{arquivo}')
    img_pequena = img.resize((800, 600))
    img_pequena.save(f'fotos_redimensionadas/{arquivo}')
```

| | OpenCV | Pillow |
|-|--------|--------|
| Complexidade | Alta | Baixa |
| Visão computacional | Completa | Limitada |
| Edições simples | Possível, mas verboso | Direto e simples |
| Performance | Alta | Média |

---

## 9. Banco de Dados

### 9.1 SQLAlchemy

O **SQLAlchemy** é a biblioteca mais usada para trabalhar com **bancos de dados SQL** em Python. Ela permite escrever código Python que se traduz automaticamente em comandos SQL, sem você precisar escrever queries manualmente.

#### Instalação

```bash
pip install sqlalchemy
```

#### Exemplo prático

```python
from sqlalchemy import create_engine, Column, Integer, String
from sqlalchemy.orm import declarative_base

Base = declarative_base()

class Produto(Base):
    __tablename__ = 'produtos'
    id = Column(Integer, primary_key=True)
    nome = Column(String)
    preco = Column(Integer)

# Conectar ao banco
engine = create_engine('sqlite:///loja.db')
Base.metadata.create_all(engine)
```

> Utilizado para conectar seu código Python a bancos de dados como PostgreSQL, MySQL ou Oracle.

---

### 9.2 SQLite

O **SQLite** é um banco de dados leve que já vem com o Python. Sua aplicação é usada em projetos pequenos que precisam de um banco de dados simples, sem complexidade de instalação ou configuração.

#### Uso com Python (biblioteca padrão)

```python
import sqlite3

# Conectar (cria o arquivo se não existir)
conexao = sqlite3.connect('meu_banco.db')
cursor = conexao.cursor()

# Criar tabela
cursor.execute('''
    CREATE TABLE IF NOT EXISTS produtos (
        id INTEGER PRIMARY KEY,
        nome TEXT,
        preco REAL
    )
''')

# Inserir dados
cursor.execute("INSERT INTO produtos VALUES (1, 'Camiseta', 49.90)")
conexao.commit()

# Consultar
cursor.execute('SELECT * FROM produtos')
resultados = cursor.fetchall()

conexao.close()
```

> Use SQLite para projetos pequenos, protótipos e aplicações locais. Para produção com dados maiores, use PostgreSQL ou MySQL com SQLAlchemy.

---

## 10. Interface Gráfica

### 10.1 Tkinter

O **Tkinter** é a biblioteca padrão do Python para criar **interfaces gráficas (telas)**. Com ele é possível criar janelas com botões, campos de texto, menus e caixas de seleção.

#### Uso (já vem com Python)

```python
import tkinter as tk

janela = tk.Tk()
janela.title('Minha Aplicação')

tk.Label(janela, text='Digite seu nome:').pack()
entrada = tk.Entry(janela)
entrada.pack()

def saudar():
    nome = entrada.get()
    print(f'Olá, {nome}!')

tk.Button(janela, text='Enviar', command=saudar).pack()
janela.mainloop()
```

---

### 10.2 CustomTkinter e TtkBootstrap

O **CustomTkinter** e o **TtkBootstrap** são bibliotecas que deixam o Tkinter mais bonito automaticamente, com temas modernos, cores e estilos pré-definidos.

#### Instalação

```bash
pip install customtkinter
# ou
pip install ttkbootstrap
```

```python
import customtkinter as ctk

ctk.set_appearance_mode('dark')
ctk.set_default_color_theme('blue')

janela = ctk.CTk()
janela.geometry('400x300')

label = ctk.CTkLabel(janela, text='Olá, mundo!')
label.pack(pady=20)

janela.mainloop()
```

| | Tkinter padrão | CustomTkinter/TtkBootstrap |
|-|----------------|---------------------------|
| Aparência | Clássica/antiga | Moderna |
| Temas | Limitados | Múltiplos temas pré-definidos |
| Componentes | Básicos | Mais variados |

---

### 10.3 Kivy

O **Kivy** é específico para criar **aplicativos mobile** (Android e iOS) com Python.

#### Instalação

```bash
pip install kivy
```

```python
from kivy.app import App
from kivy.uix.label import Label

class MeuApp(App):
    def build(self):
        return Label(text='Olá, mobile!')

MeuApp().run()
```

> Kivy usa suas próprias widgets e não depende dos componentes nativos do sistema operacional.

---

## 11. Perguntas Frequentes (FAQ Geral)

### 1. Quais são as principais bibliotecas do Python?

Entre as mais usadas estão **Pandas** e **NumPy** (dados), **Scikit-Learn**, **PyTorch** e **TensorFlow** (machine learning), **Requests** e **Selenium** (automação e web scraping) e **Matplotlib** (gráficos). A escolha depende da área em que você atua.

### 2. O que é uma biblioteca no Python?

É um conjunto de códigos prontos (funções e classes) que você importa para resolver tarefas específicas sem programar do zero. Bibliotecas como Pandas e Requests adicionam recursos poderosos ao Python com poucas linhas.

### 3. Quais bibliotecas usar para análise de dados?

**Pandas** é a principal, para manipular tabelas; **NumPy**, para cálculos numéricos; **Matplotlib** e **Seaborn**, para gráficos. Para grandes volumes, **Polars** e **PySpark** são alternativas rápidas e escaláveis.

### 4. Como instalar uma biblioteca Python?

Use o `pip` no terminal:

```bash
pip install nome_da_biblioteca
```

Exemplo: `pip install pandas`. O pip baixa o pacote e suas dependências do PyPI e deixa pronto para importar no seu código.

---

## 12. Conclusão

Python se destaca como uma das linguagens mais versáteis do mundo, e um dos seus maiores diferenciais é o ecossistema de bibliotecas. Não importa a área — dados, IA, web, automação, visão computacional, mobile — existe uma biblioteca Python pronta para resolver o problema.

### Resumo por objetivo

| Seu objetivo | Comece por aqui |
|-------------|----------------|
| Análise de dados | Pandas + NumPy |
| Machine Learning | Scikit-Learn |
| Deep Learning | PyTorch ou TensorFlow |
| Big Data | PySpark |
| APIs Web | FastAPI |
| Sites completos | Django |
| Raspagem de dados | Requests + Beautiful Soup |
| Automação de tarefas | PyAutoGUI |
| Dashboards | Streamlit |
| Gráficos | Matplotlib + Plotly |
| Visão computacional | OpenCV |
| Bancos de dados | SQLAlchemy |
| Apps desktop | Tkinter / CustomTkinter |
| Apps mobile | Kivy |

A chave é começar pela biblioteca que resolve seu problema atual e expandir conforme necessário. Com o tempo, você naturalmente construirá um conjunto de ferramentas que acompanham sua jornada.

---

## 13. Referência Rápida por Categoria

### Manipulação de Dados

| Biblioteca | Instalação | Função principal |
|-----------|-----------|------------------|
| Pandas | `pip install pandas` | DataFrames, ETL, análise de dados |
| NumPy | `pip install numpy` | Arrays numéricos, operações matemáticas |
| Polars | `pip install polars` | Pandas mais rápido (Rust) |
| PySpark | `pip install pyspark` | Big Data, processamento distribuído |
| OpenPyXL | `pip install openpyxl` | Automação de Excel com formatação |

### IA e Machine Learning

| Biblioteca | Instalação | Função principal |
|-----------|-----------|------------------|
| Scikit-Learn | `pip install scikit-learn` | ML clássico (classificação, regressão, clustering) |
| PyTorch | `pip install torch` | Deep Learning (pesquisa e prototipagem) |
| TensorFlow | `pip install tensorflow` | Deep Learning (produção) |
| LangChain | `pip install langchain` | Integração de LLMs e agentes de IA |
| Hugging Face | `pip install transformers` | Modelos pré-treinados de IA |

### Automação e Web Scraping

| Biblioteca | Instalação | Função principal |
|-----------|-----------|------------------|
| Requests | `pip install requests` | Requisições HTTP |
| Beautiful Soup | `pip install beautifulsoup4` | Parsing de HTML |
| Playwright | `pip install playwright` | Automação de navegador |
| Selenium | `pip install selenium` | Automação de navegador (alternativa) |
| Scrapy | `pip install scrapy` | Scraping em larga escala |
| PyAutoGUI | `pip install pyautogui` | Automação de mouse/teclado |

### Desenvolvimento Web

| Biblioteca | Instalação | Função principal |
|-----------|-----------|------------------|
| FastAPI | `pip install fastapi uvicorn` | APIs modernas e rápidas |
| Django | `pip install django` | Framework web completo |
| Flask | `pip install flask` | Micro-framework web |
| Pydantic | `pip install pydantic` | Validação de dados |

### Visualização

| Biblioteca | Instalação | Função principal |
|-----------|-----------|------------------|
| Matplotlib | `pip install matplotlib` | Gráficos flexíveis |
| Seaborn | `pip install seaborn` | Gráficos estatísticos bonitos |
| Plotly | `pip install plotly` | Gráficos interativos |
| Streamlit | `pip install streamlit` | Dashboards web em minutos |

### Outras Categorias

| Categoria | Biblioteca | Instalação | Função principal |
|-----------|-----------|-----------|------------------|
| Visão Computacional | OpenCV | `pip install opencv-python` | Processamento de imagem/vídeo |
| Visão Computacional | Pillow | `pip install pillow` | Edição simples de imagens |
| Banco de Dados | SQLAlchemy | `pip install sqlalchemy` | ORM para bancos SQL |
| Banco de Dados | SQLite | (padrão) | Banco de dados leve embutido |
| Interface Gráfica | Tkinter | (padrão) | Telas desktop |
| Interface Gráfica | CustomTkinter | `pip install customtkinter` | Tkinter com visual moderno |
| Interface Gráfica | Kivy | `pip install kivy` | Apps mobile |
| Utilitárias | PyInstaller | `pip install pyinstaller` | Compilar para .exe |
| Utilitárias | PyTest | `pip install pytest` | Testes automatizados |

---

*Guia completo baseado no conteúdo da Hashtag Treinamentos.*
