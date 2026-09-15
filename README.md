# TravelMais — Chatbot de Atendimento com IA Generativa

## Sobre o projeto

O TravelMais é um chatbot de atendimento virtual desenvolvido para uma agência de viagens fictícia, com o objetivo de auxiliar clientes na consulta de informações sobre pacotes de viagem, preços, serviços incluídos, formas de pagamento, regras de cancelamento e reservas.

O projeto utiliza a API do Google Gemini para gerar respostas em linguagem natural, seguindo instruções definidas em um contexto específico da agência. A interação com o chatbot é realizada por meio de uma interface desenvolvida com a biblioteca Panel, permitindo que o usuário envie perguntas e receba respostas em uma conversa interativa.

O chatbot possui um limite de três perguntas por atendimento, conforme definido nas instruções fornecidas ao modelo.

## Funcionalidades

* Atendimento virtual em português do Brasil.
* Consulta de pacotes de viagem e seus respectivos preços.
* Informações sobre duração, hospedagem e serviços incluídos.
* Consulta às regras de pagamento, cancelamento e reserva.
* Respostas baseadas exclusivamente nas informações fornecidas no contexto da TravelMais.
* Interface interativa para envio e visualização de mensagens.
* Limite de três perguntas por atendimento, com resumo da conversa ao final.

## Tecnologias utilizadas

* **Python** — Linguagem de programação utilizada no desenvolvimento.
* **Google Gemini API** — Modelo de inteligência artificial generativa responsável pela geração das respostas.
* **Google GenAI SDK** — Biblioteca utilizada para integração com a API Gemini.
* **Panel** — Biblioteca utilizada para criação da interface interativa do chatbot.
* **Google Colab** — Ambiente utilizado para desenvolvimento e execução do projeto.

## Estrutura do projeto

```text
travelmais-chatbot/
│
├── README.md
├── env.example
├── .env
└── travelmais_chatbot.ipynb
```

> O arquivo `.env` deve ser utilizado para armazenar a chave da API e não deve ser enviado ao repositório. O arquivo `env.example` deve conter apenas o nome do parâmetro, sem o valor da chave.

## Configuração do ambiente

### 1. Clone o repositório

```bash
git clone https://github.com/SEU-USUARIO/travelmais-chatbot.git
```

Acesse a pasta do projeto:

```bash
cd travelmais-chatbot
```

### 2. Configure a chave da API Gemini

O projeto utiliza uma chave de API do Google Gemini para realizar as requisições ao modelo de inteligência artificial.

Crie um arquivo `.env` na raiz do projeto contendo:

```env
GEMINI_KEY=sua_chave_api_aqui
```

O arquivo `env.example` deve ser disponibilizado no repositório com a seguinte estrutura:

```env
GEMINI_KEY=
```

**Importante:** não compartilhe sua chave da API publicamente e não envie o arquivo `.env` para o GitHub.

### 3. Instale as dependências

Instale as bibliotecas necessárias:

```bash
pip install google-genai panel python-dotenv
```

## Como reproduzir a execução apresentada no vídeo

### 1. Acesse o Google Colab

Abra o [Google Colab](https://colab.research.google.com/) e carregue o notebook `travelmais_chatbot.ipynb` disponível neste repositório.

### 2. Configure a chave da API

No Google Colab, configure a variável `GEMINI_KEY` nos Secrets do ambiente:

1. Abra o painel de Secrets, identificado pelo ícone de chave.
2. Adicione um novo segredo com o nome `GEMINI_KEY`.
3. Informe o valor da sua chave da API Gemini.
4. Habilite o acesso ao segredo para o notebook.

O código utiliza o recurso `google.colab.userdata` para recuperar a chave:

```python
from google.colab import userdata

GEMINI_KEY = userdata.get('GEMINI_KEY')
```

### 3. Execute as células do notebook

Execute as células em ordem para:

1. Importar as bibliotecas necessárias.
2. Configurar a chave da API Gemini.
3. Criar o cliente de comunicação com o modelo.
4. Definir a função responsável por enviar as mensagens à API.
5. Configurar o contexto e as instruções do chatbot TravelMais.
6. Criar a interface interativa utilizando Panel.
7. Iniciar o atendimento virtual.

### 4. Interaja com o chatbot

Após executar o notebook, a interface do chatbot será exibida.

Digite uma pergunta no campo de texto e clique no botão **Enviar**.

Exemplos de perguntas que podem ser utilizadas para reproduzir a demonstração:

```text
Quais pacotes de viagem estão disponíveis?
```

```text
Quanto custa uma viagem para Gramado?
```

```text
Quais são as formas de pagamento?
```

O chatbot responderá às perguntas utilizando as informações definidas no contexto da TravelMais.

### 5. Limite de perguntas

O chatbot foi configurado para permitir exatamente três perguntas por atendimento.

* Nas duas primeiras perguntas, o chatbot responde normalmente.
* Na terceira pergunta, o chatbot responde e apresenta um resumo das três perguntas e respostas.
* Após o resumo, o atendimento é encerrado.
* Uma quarta pergunta não deve ser respondida, conforme as instruções definidas para o modelo.

## Exemplo de interação

**Usuário:**

> Quanto custa uma viagem para Gramado?

**Atendente Virtual TravelMais:**

> O pacote para Gramado custa R$ 2.000 por pessoa e possui duração de 4 dias e 3 noites. Inclui hospedagem, café da manhã e transporte do aeroporto até o hotel. As passagens aéreas não estão incluídas.

## Organização do código

O projeto está organizado em um notebook Python, contendo as seguintes etapas:

### Configuração da API

Responsável pela importação das bibliotecas e criação do cliente para comunicação com o Google Gemini.

### Função de geração de respostas

A função `get_completion_from_messages()` recebe o contexto da conversa e realiza uma requisição ao modelo Gemini, retornando a resposta gerada.

### Contexto da TravelMais

Contém as instruções de personalidade, os pacotes de viagem, as regras de pagamento, cancelamento e reserva, além das limitações de resposta do chatbot.

### Interface interativa

Desenvolvida utilizando a biblioteca Panel, permite o envio de mensagens e a exibição das respostas do atendente virtual.

### Controle da conversa

O histórico de mensagens é armazenado em uma lista de contexto, permitindo que o modelo receba as mensagens anteriores durante o atendimento.

## Observações

* A TravelMais é uma agência de viagens fictícia criada exclusivamente para este projeto.
* Os preços, destinos, serviços e regras apresentados são dados fictícios definidos no contexto do chatbot.
* O projeto depende de uma chave válida da API Gemini para funcionar.
* O chatbot não realiza reservas reais nem processa pagamentos.
* As respostas são limitadas às informações fornecidas nas instruções do modelo.

## Autor

Mateus Neri

Projeto desenvolvido para fins acadêmicos e de aprendizado em Inteligência Artificial Generativa.
