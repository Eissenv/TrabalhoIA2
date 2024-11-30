# Projeto de Chatbot com Classificação de Textos

Este projeto implementa um chatbot do Telegram que classifica textos em inglês enviados pelos usuários como positivo, negativo ou neutro. Além disso, o bot pode processar imagens contendo texto, extrair o conteúdo textual e classificá-lo.


## Estrutura de Arquivos

treinamento.ipynb: Contém todas as funções e etapas relacionadas ao treinamento dos modelos de classificação de texto.

chatbot.ipynb: Configura o bot do Telegram e define as funções de resposta para mensagens de texto e imagens.

Classes/: Diretório com os dados utilizados para o treinamento. Inclui arquivos .txt contendo dados para as classes 'positive', 'negative' e 'neutral'.

## Arquiteturas utilizadas
DistilBERT (distilbert-base-uncased-finetuned-sst-2-english):

- https://huggingface.co/distilbert/distilbert-base-uncased-finetuned-sst-2-english

- Descrição:

    O DistilBERT é uma versão mais leve do BERT. É ajustada (fine-tuned) para análise de sentimentos com o conjunto de dados SST-2, que realiza classificação binária (Positivo ou Negativo), sendo adaptada neste projeto para também incluir a classe Neutro.

---

Twitter-RoBERTa (cardiffnlp/twitter-roberta-base-sentiment):

- https://huggingface.co/cardiffnlp/twitter-roberta-base-sentiment

- Descrição:

    O Twitter-RoBERTa é um modelo baseado no RoBERTa, otimizado especificamente para tarefas de análise de sentimentos em textos oriundos de redes sociais, como o Twitter.
    Ele realiza classificação de sentimentos em três categorias: Positivo, Negativo e Neutro.


    
## Execução:

1. Clone esse repositório e coloque os arquivos dentro de uma pasta chamada "TrabalhoIA2" no google drive. 

    Caso queira utilizar outra pasta, lembre de mudar os caminhos utilizados durante o treinamento e o chatbot. Veja um exemplo de caminho dentro de treinamento.ipynb: 

    ```python
    # Diretório das imagens
    data_dir = '/content/drive/MyDrive/TrabalhoIA2/Classes'
    ```
---
2. Execute o arquivo de treinamento.
---
3. Após finalizar o treinamento crie um bot no Telegram e obtenha o token através do BotFather. Esse token deve ser colocado em chatbot.ipynb, na seguinte parte:

    ```python
    TELEGRAM_TOKEN = 'YOUR-TOKEN-HERE'
    ```
4. Verifique se o caminho para o modelo que deseja utilizar está correto em chatbot.ipynb: 
    ```python
    # Caminho para o modelo salvo
    model_path = '/content/drive/MyDrive/TrabalhoIA2/Modelos/cardiffnlp_twitter-roberta-base-sentiment'
    ```

5. Execute todo o código de chatbot.ipynb. O bot funcionará após a execução da main().

## Funcionamento do Bot

Classificação de Textos:

- O usuário envia um texto em inglês, e o bot responde com a classificação de sentimento (positivo, neutro ou negativo), junto com as probabilidades.

Classificação de Imagens:

- O usuário envia uma imagem contendo texto em inglês.
- O bot extrai o texto da imagem, processa-o e responde com a classificação de sentimento.