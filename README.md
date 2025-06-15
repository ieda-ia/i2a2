# Agente Local para Análise de Notas Fiscais 📊

Este projeto implementa um agente local utilizando Python 🐍, Pandas 🐼, Langchain e Google Generative AI ✨ para analisar dados de notas fiscais. O principal objetivo é simplificar a análise de grandes volumes de dados fiscais, permitindo que usuários façam perguntas em linguagem natural 🗣️ e obtenham insights rápidos e precisos sobre suas notas fiscais. 🧾

A ferramenta combina o poder do processamento de dados do Pandas com a capacidade de compreensão e geração de linguagem natural do Google Generative AI (através da biblioteca Langchain), criando uma interface conversacional para explorar os dados das notas fiscais. Isso elimina a necessidade de escrever código complexo para realizar consultas e análises básicas.


## Configuração ⚙️

Para configurar e executar este projeto, siga os passos abaixo:

### Pré-requisitos ✅

*   **Python:** Certifique-se de ter o Python 3.7 ou superior instalado em seu sistema. Você pode baixá-lo do site oficial do Python: [python.org](https://www.python.org/).

### Instalação das Dependências 📦

As bibliotecas necessárias para este projeto podem ser instaladas utilizando o `pip`. Embora o código no notebook instale as bibliotecas diretamente, em um projeto local, você geralmente teria um arquivo `requirements.txt`. Para este projeto, as principais bibliotecas são:

*   `langchain`
*   `langchain_experimental`
*   `langchain-community`
*   `pandas`
*   `tabulate`
*   `gdown`
*   `langchain-google-genai`
*   `google-ai-generativelanguage`

Você pode instalar todas elas de uma vez executando o seguinte comando no seu terminal:

```bash
pip install langchain langchain_experimental langchain-community pandas tabulate gdown langchain-google-genai google-ai-generativelanguage==0.6.15
```

### Obtenção da Chave de API do Google 🔑

Este projeto utiliza a API do Google Generative AI. Você precisará obter uma chave de API:

1.  Vá para o [Google AI Studio](https://aistudio.google.com/app/apikey).
2.  Faça login com sua conta Google.
3.  Clique em "Create API key" (Criar chave de API).
4.  Copie a chave gerada.

### Configuração da Chave de API

A chave de API precisa ser configurada como uma variável de ambiente chamada `GOOGLE_API_KEY`.

*   **No Google Colab:** A maneira mais segura e **recomendada**** é usar a funcionalidade "Secrets" do Colab.
    1.  No painel esquerdo do Colab, clique no ícone de chave (Secrets).
    2.  Clique em "Add new secret" (Adicionar novo segredo).
    3.  No campo "Name", digite `GOOGLE_API_KEY`.
    4.  No campo "Value", cole a chave de API que você obteve do Google AI Studio.
    5.  Marque a caixa "Notebook access" (Acesso ao notebook) para este notebook.
    O código fornecido no notebook já inclui o carregamento automático desta variável do Secrets.

*   **Execução Local (Terminal):** Você pode definir a variável de ambiente no seu terminal antes de executar o script Python.
    *   **Linux/macOS:**
        ```bash
        export GOOGLE_API_KEY='SUA_CHAVE_API_AQUI'
        ```
    *   **Windows (Command Prompt):**
        ```bash
        set GOOGLE_API_KEY=SUA_CHAVE_API_AQUI
        ```
    *   **Windows (PowerShell):**
        ```powershell
        $env:GOOGLE_API_KEY='SUA_CHAVE_API_AQUI'
        ```
    Substitua `'SUA_CHAVE_API_AQUI'` pela sua chave de API real.



## Executando no Google Colab 🚀

A maneira mais simples e rápida de executar este projeto é utilizando o Google Colab.

1.  Abra o arquivo do notebook (`.ipynb`) diretamente no Google Colab.
2.  Execute cada célula de código sequencialmente, do início ao fim.
3.  Na seção de configuração da chave de API (Célula 2), **é essencial** que você utilize a funcionalidade "Secrets" do Colab para armazenar e carregar sua `GOOGLE_API_KEY`, conforme detalhado na seção "Configuração" acima. O código no notebook já está preparado para carregar a chave desta forma.
4.  As células seguintes cuidarão automaticamente do download dos dados, da descompactação e da criação do agente de análise.
5.  Após a execução da última célula, a interface interativa de perguntas será iniciada no output da célula, permitindo que você comece a interagir com o agente.



## Executando Localmente 🖥️

Se você preferir executar o agente em seu ambiente local, siga estes passos:

1.  **Clone o Repositório:** Se o código estiver hospedado em um repositório (por exemplo, GitHub), clone-o para o seu ambiente local.
    ```bash
    git clone <URL_DO_SEU_REPOSITORIO>
    cd <NOME_DA_PASTA_DO_REPOSITORIO>
    ```
    (Substitua `<URL_DO_SEU_REPOSITORIO>` e `<NOME_DA_PASTA_DO_REPOSITORIO>` pelos valores corretos).

2.  **Crie e Ative um Ambiente Virtual:** É altamente recomendado usar um ambiente virtual para isolar as dependências do projeto.
    ```bash
    python -m venv .venv
    ```
    *   **No Windows:**
        ```bash
        .venv\Scriptsctivate
        ```
    *   **No Linux/macOS:**
        ```bash
        source .venv/bin/activate
        ```

3.  **Instale as Dependências:** Com o ambiente virtual ativado, instale as bibliotecas necessárias. Use o comando `pip install` fornecido na seção "Configuração".
    ```bash
    pip install langchain langchain_experimental langchain-community pandas tabulate gdown langchain-google-genai google-ai-generativelanguage==0.6.15
    ```

4.  **Configure a Chave de API:** Defina a variável de ambiente `GOOGLE_API_KEY` no seu terminal **antes** de executar o script. Consulte as instruções específicas para o seu sistema operacional na seção "Configuração".
    *   **No Linux/macOS:**
        ```bash
        export GOOGLE_API_KEY='SUA_CHAVE_API_AQUI'
        ```
    *   **No Windows (Command Prompt):**
        ```bash
        set GOOGLE_API_KEY=SUA_CHAVE_API_AQUI
        ```
    *   **No Windows (PowerShell):**
        ```powershell
        $env:GOOGLE_API_KEY='SUA_CHAVE_API_AQUI'
        ```
    Lembre-se de substituir `'SUA_CHAVE_API_AQUI'` pela sua chave de API real.

5.  **Execute o Script:** Salve o código do notebook como um arquivo Python (por exemplo, `agent_app.py`) e execute-o a partir do terminal com o ambiente virtual ativado.
    ```bash
    python agent_app.py
    ```
    O script baixará os dados, configurará o agente e iniciará a interface interativa de perguntas no seu terminal.



## Utilizando o Agente

Após configurar e executar o script (seja no Google Colab ou localmente), você verá um prompt interativo no output da célula (no Colab) ou no seu terminal (localmente).

Digite suas perguntas sobre os dados das notas fiscais no prompt e pressione Enter. O agente utilizará o DataFrame combinado (`df_completo`) para processar sua pergunta e fornecer uma resposta com base nos dados disponíveis.

Aqui estão alguns exemplos de perguntas que você pode fazer:

*   Qual é o fornecedor que teve maior montante recebido no total?
*   Qual item teve maior volume entregue em quantidade?
*   Liste os 5 itens mais caros com base no valor unitário.
*   Qual a data da nota fiscal mais recente?

Para encerrar a sessão interativa, basta digitar `sair` e pressionar Enter.



## Estrutura do Projeto 📂

O projeto consiste principalmente em um notebook Jupyter (que pode ser executado no Google Colab ou salvo como um script Python para execução local) e os arquivos de dados.

*   **Notebook/Script Principal:** Contém todo o código para configurar o ambiente, baixar e processar os dados, criar o agente e iniciar a interface interativa.
*   **`dados_nfs/`:** Este diretório é criado automaticamente pelo script ao baixar e descompactar o arquivo ZIP. Ele contém os arquivos CSV brutos:
    *   `202401_NFs_Cabecalho.csv`: Contém as informações de cabeçalho de cada nota fiscal.
    *   `202401_NFs_Itens.csv`: Contém os detalhes dos itens de cada nota fiscal.
*   **`202401_NFs.zip`:** O arquivo ZIP original baixado do Google Drive, contendo os dois arquivos CSV mencionados acima.



## Resolução de Problemas Comuns

Aqui estão algumas dicas para resolver problemas comuns que você pode encontrar:

*   **`API key not valid`:** Este erro indica que a chave de API do Google não é válida ou não foi configurada corretamente como uma variável de ambiente.
    *   **Solução:** Verifique sua chave de API no [Google AI Studio](https://aistudio.google.com/app/apikey) para garantir que está correta. Confirme se a variável de ambiente `GOOGLE_API_KEY` foi definida corretamente, seja usando os "Secrets" do Google Colab (método recomendado) ou exportando-a no seu terminal antes de executar o script, conforme detalhado na seção "Configuração".

*   **`FileNotFoundError`:** Este erro geralmente significa que os arquivos de dados (`.csv`) não foram baixados ou descompactados corretamente.
    *   **Solução:** Verifique o link do Google Drive na Célula 3 do notebook para garantir que está correto. Certifique-se de que as permissões de compartilhamento do arquivo no Google Drive estão definidas como "Any person with the link". Após executar a Célula 3, confirme se o diretório `dados_nfs` foi criado e se contém os arquivos `202401_NFs_Cabecalho.csv` e `202401_NFs_Itens.csv`.

*   **Erros de parsing ou comportamento inesperado do agente:** Se o agente tiver dificuldade em entender sua pergunta ou retornar resultados incorretos, isso pode ser devido a formatos de dados inesperados ou à complexidade da sua pergunta.
    *   **Solução:** Tente reformular sua pergunta de forma mais clara e direta. Se possível, inspecione os arquivos CSV brutos (`.csv`) para entender melhor a estrutura e o conteúdo dos dados. Lembre-se que o agente está configurado com `verbose=True`, o que mostrará o "raciocínio" dele e pode ajudar a identificar onde a interpretação falhou.

