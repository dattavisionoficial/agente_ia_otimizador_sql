# Agente de IA para Otimização de Consultas SQL

Este repositório contém um agente de inteligência artificial desenvolvido para auxiliar na otimização de consultas Structured Query Language (SQL) através da análise de planos de execução. O agente identifica gargalos e sugere melhorias para aprimorar a performance do banco de dados.

## Funcionalidades Principais

* **Análise de Planos de Execução:** Processa e interpreta planos de execução de consultas SQL.
* **Identificação de Gargalos:** Aponta possíveis pontos de lentidão e ineficiência nas consultas.
* **Sugestões de Melhoria:** Propõe otimizações para a estrutura das consultas, índices e arquitetura do banco de dados, seguindo as melhores práticas.
* **Conhecimento Atualizado:** Utiliza a ferramenta de busca do Google para incorporar as últimas informações e melhores práticas (dados de até 1 ano).
* **Arquitetura Multi-Agente:** O sistema é composto por agentes especializados que trabalham em conjunto:
    * **Agente Buscador:** Coleta informações relevantes sobre otimização de SQL a partir da análise do plano de execução.
    * **Agente Planejador:** Analisa as informações e planeja as estratégias de otimização, detalhando vantagens, desvantagens e scripts necessários.
    * **Agente Validador:** Realiza uma avaliação técnica das otimizações propostas, buscando erros conceituais e em scripts.
    * **Agente Revisor:** Simula ou considera os impactos das otimizações em um ambiente de teste para garantir ganhos de performance reais e evitar efeitos colaterais.

## Pré-requisitos

* **Python 3.x** instalado em seu sistema.
* **Conta Google Cloud com uma chave de API ativa.**
* **Google Cloud CLI** (opcional, mas recomendado para algumas configurações).

## Instalação

1.  **Clone o repositório:**
    ```bash
    git clone https://github.com/dattavisionoficial/agente_ia_otimizador_sql.git
    ```

2.  **Instale as dependências:**
    Execute o seguinte comando `pip` para instalar as bibliotecas necessárias:
    ```bash
    pip install google-genai google-adk ipython requests
    ```
    Certifique-se de ter o `pip` instalado em seu ambiente Python.

3.  **Configure a chave da API do Google Gemini:**
    Você pode configurar a chave da API de duas maneiras:

    * **Usando `userdata` no Google Colab (recomendado para Colab):**
        Se você estiver executando este projeto no Google Colab, siga estas etapas para armazenar sua chave de API de forma segura:
        ```python
        import os
        from google.colab import userdata

        os.environ["GOOGLE_API_KEY"] = userdata.get('GOOGLE_API_KEY')
        ```
        Certifique-se de adicionar sua chave de API em "Secrets" (o ícone de chave na barra lateral esquerda do Colab) com o nome `GOOGLE_API_KEY`.

    * **Definindo como uma variável de ambiente (para ambientes locais):**
        Exporte sua chave de API como uma variável de ambiente no seu terminal:
        ```bash
        export GOOGLE_API_KEY="SUA_CHAVE_DE_API"
        ```
        Ou adicione a linha acima ao seu arquivo de configuração shell (por exemplo, `.bashrc` ou `.zshrc`).

## Como Utilizar

O processo geral para utilizar o agente é o seguinte:

1.  **Forneça o Plano de Execução:** O ponto de partida é obter o plano de execução da consulta SQL que você deseja otimizar. A forma de obter esse plano varia dependendo do seu sistema de gerenciamento de banco de dados (por exemplo, `EXPLAIN` no MySQL e PostgreSQL, `EXPLAIN PLAN` no Oracle, etc.).

2.  **Execute o Agente:** O código principal para executar o fluxo de otimização estará em um script Python (colab). Este script irá instanciar e orquestrar os diferentes agentes, passando o plano de execução como entrada para o `agente_buscador`.

3.  **Analise os Resultados:** O output do agente será um conjunto de sugestões de otimização, incluindo a análise, o plano proposto, a validação técnica e a revisão de impacto.

## Tecnologias Utilizadas

* **Google AI Platform (GenAI):** Utilizado para os modelos de linguagem (como `gemini-2.0-flash`).
* **Google ADK (Agent Development Kit):** Framework para a criação e orquestração dos agentes.
* **Google Search Tool:** Ferramenta para acesso e busca de informações relevantes.
* **Python:** Linguagem de programação principal.
