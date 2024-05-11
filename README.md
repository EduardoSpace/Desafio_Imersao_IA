# SACI - Smart Alarm para Câmeras IP 🏠📹🚷🚨📱

## Sobre o Projeto

Este projeto é o resultado de um desafio proposto no programa **#Imersão Inteligência Artificial 2ª Edição**, oferecida pela Alura em parceria com o Google. O objetivo deste projeto foi desenvolver uma solução, para tornar câmeras IPs, DVRs e NVRs de baixo custo em dispositivos "smart" processando imagens das câmeras a fim de detectar intrusos (utilizando a API do Google AI) para o envio de alertas através do Telegram.

##  Arquitetura da Solução
![Arquitetura da Solução](https://drive.google.com/thumbnail?id=1Jy1A89XIDrYfQcnkb-PePTfdmrFTVzvs&sz=w1000)

##  Motivação
Atualmente, muitas residências e empresas possuem câmeras de segurança. Uma funcionalidade muito desejada é a de detectar pessoas e alertar os proprietários. Isso é muito útil para pessoas que possuem imóveis rurais ou que ficam vazios por um período de tempo.
A maioria das câmeras de segurança residenciais, DVRs e NVRs carecem de recursos para detecção de pessoas (esse é um recurso  geralmente presente em equipamentos mais caros). Alguns modelos até oferecem essa funcionalidade como um serviço adicional pela cloud, que é cobrado através de uma assinatura mensal e de elevado custo.

A grande maioria dos modelos é capaz de detectar movimentos (independente do tipo). Isso resulta em uma quantidade significativa de alertas classificados como falsos positivos, uma vez que qualquer movimento - seja de árvores, plantas, animais ou até mesmo das nuvens - pode originar um alerta (que pode ser um e-mail, ou uma notificação através de um aplicativo instalado em um smartphone). 
Um fato relevante é que quase todos os modelos de câmeras, DVRs e NVRs residenciais podem ser configuradas para quando na ocorrência de uma detecção de movimento enviarem imagens do momento exato de detecção por FTP. Entretanto, muitos usuários acabam deixando essa opção desativada devido a grande taxa de falsos positivos que iria receber e por não terem conhecimento de como instalar e/ou acessar um servidor FTP.
A solução aqui apresentada, utiliza inteligência artificial para detectar pessoas nas imagens, e não exige aquisição de novas câmeras, DVRs ou NVRs. Além disso, permite que as imagens com alertas de indivíduos suspeitos sejam recebidas diretamente em seu smartphone através do Telegram.

##  Funcionalidades

-   **Servidor FTP para recebimento de imagens de câmeras IP, DVRs ou NVRs**  
-   **Detecção de pessoas em imagens utilizando API generativeai** 
-   **Envio de mensagens de alertas com imagens pelo Telegram** 

## Tecnologias envolvidas

-   **Python:**  Linguagem de programação.
-   **Google Generative AI (Gemini):**  Modelo de linguagem para processamento de imagens (visão computacional).
-   **Pyftpdlib:**  Biblioteca de funcionalidades de FTP.
-   **Telegram:** Conectividade com o Telegram para envio de alertas.

## Objetivos e Vantagens

-   **Ampla compatibilidade:**  A solução é compatível com a maioria das câmeras IPs, DVRs e NVRs evitando necessidade de troca ou de aquisição de novas câmeras.
-   **Baixo custo:**  A solução envolve apenas o pagamento de utilização da API que é um custo relativamente baixo se comparado à aquisição de novos equipamentos e/ou à assinatura de serviços de cloud com esse serviço de visão computacional embutido.
-   **Alertas por smartphones:** A solução notifica os usuários diretamente pelo Telegram em seus smartphones

## Como executar
**OBS:** O projeto é um servidor FTP (que recebe conexões externas), funcionalidade não suportada pelo Colab. O código foi desenvolvido, executado e testado utilizando-se o Visual Studio Code, mas qualquer outra IDE serve para executá-lo.

**1 - Clone o repositório ou copie o arquivo:**
git clone https://github.com/EduardoSpace/Desafio_Imersao_IA.git

**2 - Instale as dependências:**
	pip install google-generativeai  
	pip install pyftpdlib
 
**3 - Configure sua chave de API Google:**
	Para usar a API Gemini, você precisa de uma chave de API. É possível criar uma chave com um clique no Google AI Studio.
	Comente a linha de código api_key = config['DEFAULT']['api_key'] #Chave da API do Google e descomente a linha #api_key = 'ABC' trocando 'ABC' pela sua chave.
 
**4 - Configure sua chave de Bot Telegram:**
		4.1 - Crie uma conta no Telegram caso ainda não possua uma.
  
		4.2 - Inicie uma conversa com o @botfather1. Lembre-se que os robôs oficiais do Telegram têm um tique azul do lado do nome.
  
		4.3 - Clique em iniciar.
  
			Escolha o comando /new bot. Isso iniciará o processo de criação do bot.
			Escolha o nome do seu chatbot e faça as configurações gerais.
			Defina um username para o bot que termine em “bot”, sem espaços.
			Aguarde a criação do bot no Telegram. O BotFather mandará uma mensagem com o link da conversa do seu bot.
			Guarde o token de API gerado pelo BotFather em um local seguro e não compartilhe com ninguém, pois somente quem possuir o token poderá usar o bot.
			Comente a linha de código token_bot = config['DEFAULT']['token_bot'] e descomente a linha #token_bot = '123' trocando '123' pelo token gerado anteriormente.
   
**5 - Configure sua chave de chat Telegram:**
	5.1 - Usando o @RawDataBot:
			Abra o Telegram (via navegador ou aplicativo) e faça o login.
			Encontre a linha de pesquisa (deslize para baixo se estiver usando um aplicativo móvel para torná-lo visível ou encontre-o no canto superior direito se você estiver usando PC, Mac ou site).
			Digite @RawDataBot e comece a procurar.
			Entre no chat com o bot e você receberá seu ID (chat_id).
			Comente a linha de código chat_id = config['DEFAULT']['chat_id'] # ID do usuário Telegram que receberá os alertas e descomente a linha #chat_id = '321' trocando '321' pelo seu chat_id.
   
**6 - Execute o código**

**7 - Conecte através de um FTP client**

	Caso você não possua uma câmera IP, DVR ou NVR para configurar o envio das imagens à aplicação,
	existem vários clients gratuitos como FileZilla, WinSCP, etc... que podem simular o envio.
	Utilizando o seu cliente FTP, câmera IP, DVR ou NVR, crie uma conexão para localhost com usuário:user e senha:12345.
	Após conectar, envie uma imagem e ela será recebida no Telegram cadastrado (chat_id)
