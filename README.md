# Gerador de Agenda de Discussão de IA para Empresas

Este Google Colab é uma ferramenta automatizada para auxiliar empresas a se manterem atualizadas sobre os avanços em Inteligência Artificial (IA) e a planejar discussões estratégicas internas. Ele busca os principais tópicos de IA (inovação, ferramentas, notícias), identifica eventos relevantes no Brasil e propõe uma agenda de discussão personalizada com base no segmento da empresa e nos projetos em andamento/backlog.

## Funcionalidades

* **Seleção de Segmento da Empresa:** Escolha o segmento da sua empresa através de um dropdown para personalizar a relevância do conteúdo de IA.
* **Integração com Gemini API:** Utiliza a API do Google Gemini para:
    * Gerar consultas de busca inteligentes.
    * Analisar e resumir o conteúdo de notícias e artigos.
    * Selecionar os **dois principais** exemplos de inovação, ferramentas e notícias relevantes em IA a cada mês, considerando o segmento da empresa.
* **Busca Automatizada de Eventos:** Encontra eventos de IA (online ou presenciais, gratuitos) no Brasil para o mês seguinte, usando a busca no Google.
* **Análise de Projetos (Opcional):** Conecte uma planilha de projetos (CSV ou XLSX) com status "Em Andamento" e "Backlog" para que a agenda sugira sinergias com as tendências de IA.
* **Geração de Agenda Personalizada:** Propõe uma agenda de discussão detalhada, com tópicos baseados nas informações levantadas e na relevância para o negócio.
* **Notificações Integradas:**
    * **E-mail:** Envie a agenda gerada para múltiplos endereços de e-mail via SMTP (requer configuração de senha de aplicativo Gmail).
    * **WhatsApp (via Evolution API):** Envie a agenda via WhatsApp para números específicos (requer uma instância da Evolution API configurada).

## Como Usar

1.  **Abra no Google Colab:** Clique no botão "Open in Colab" (se estiver visualizando no GitHub) ou copie o conteúdo do `notebook.ipynb` para um novo Colab.
2.  **Configurar a API do Gemini:**
    * Obtenha sua chave de API do Google Gemini em [Google AI Studio](https://aistudio.google.com/app/apikey).
    * No Google Colab, clique no ícone "Secrets" (uma chave) no painel esquerdo.
    * Adicione uma nova variável secreta chamada `GOOGLE_API_KEY` e cole sua chave de API como valor.
    * **Nunca exponha sua chave diretamente no código ou no GitHub!**
3.  **Instalar Dependências:** Execute a primeira célula do Colab para instalar todas as bibliotecas necessárias.
4.  **Selecione o Segmento:** Escolha o segmento da sua empresa no dropdown.
5.  **Carregar Planilha de Projetos (Opcional):**
    * Clique em "Conectar com Planilha de Projetos" e faça o upload de um arquivo CSV ou XLSX.
    * A planilha deve conter as colunas `Projeto` e `Status` (com valores como "Em Andamento" ou "Backlog").
    * Alternativamente, clique em "IGNORAR" se não desejar usar uma planilha.
6.  **Gerar Agenda:** Clique no botão "Gerar Agenda de Discussão". O Colab fará as buscas e apresentará a agenda.
7.  **Enviar Notificações (Opcional):**
    * **E-mail:** Preencha os campos de e-mail de destino, seu e-mail Gmail e a senha de aplicativo (veja abaixo como gerar). Clique em "Enviar Agenda por E-mail".
        * **Para Gmail:** Você precisará ativar a verificação em duas etapas na sua conta Google e gerar uma "senha de aplicativo" para usar aqui, em vez da sua senha normal. Pesquise por "gerar senha de aplicativo Gmail".
    * **WhatsApp (Evolution API):** Preencha o URL da sua instância da Evolution API, sua API Key e os números de WhatsApp (formato `55DDNNNNNNNNN`). Clique em "Enviar Agenda por WhatsApp".
        * **Atenção:** Você precisa ter uma instância da Evolution API configurada e rodando para esta funcionalidade. Verifique a documentação da Evolution API para detalhes sobre a instância e a chave de API.

## Estrutura do Código

O notebook é dividido em células lógicas:

* **Configuração Inicial:** Instalação de bibliotecas e configuração da API do Gemini.
* **Variáveis Globais:** Definição de variáveis que persistem dados entre as células.
* **Segmento da Empresa:** Widget de dropdown para seleção do segmento.
* **Conexão com Planilha de Projetos:** Widgets para upload de arquivo e processamento.
* **Coleta de Dados de IA:** Função `coletar_dados_ia_com_gemini` que interage com a API do Gemini e simula a busca no Google.
* **Busca de Eventos:** Função `coletar_eventos_ia_google` que simula a busca por eventos no Google.
* **Geração da Agenda:** Função `gerar_agenda` que compila as informações e personaliza o output.
* **Botão Gerar Agenda:** Dispara o processo principal.
* **Envio por E-mail:** Widgets e função `send_email_notification` para o envio via SMTP.
* **Envio por WhatsApp:** Widgets e função `send_whatsapp_message` para a integração com a Evolution API.

## Contribuições

Sinta-se à vontade para contribuir com melhorias, como:

* Adicionar mais fontes de dados para IA (web scraping de blogs específicos, outras APIs de notícias).
* Melhorar a lógica de filtragem e seleção dos "top 2" itens.
* Refinar a extração de detalhes de eventos.
* Adicionar suporte a outras APIs de comunicação.

---
**Desenvolvido por:** [Seu Nome/GitHub User]
**Licença:** MIT (Opcional, se você quiser adicionar uma licença)
