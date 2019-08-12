# Internet

`Cidadania Digital` `4 horas-aula`

`Objetivos` Apresentar e discutir os principais conceitos, protocolos e infraestruturas que viabilizam a internet.

`Competências` Conhecer o quê é e como funciona a internet; compreender as principais nomenclaturas e unidades físicas; distinguir entre infraestrutura, protocolos e diferentes camadas de serviços. 

`Roteiro`

#### 1) A internet mais de perto

> Muitas pessoas não sabem diferenciar o que é o Facebook ou o Google do que é a Internet, e só acessam a rede através desses servidores centralizados. [El País 29/07/2019](https://brasil.elpais.com/brasil/2019/07/30/tecnologia/1564437803_087942.html)

Você ou alguém por perto deve ter em mãos um celular Android (ou um Chromebook). Vamos usá-lo de um modo diferente para acessar a internet. Um celular Android é um computador bastante sofisticado, mas a interface para o usuário é bastante restrita. Fica limitada aos aplicativos.

Ficava!

Vamos instalar o [Termux](https://play.google.com/store/apps/details?id=com.termux&hl=pt) e abrir uma janela para dentro do seu celular! Tem um ótimo [tutorial sobre o básico do Termux](https://sempreupdate.com.br/conheca-o-termux-e-aproveite-ao-maximo-o-linux-no-android/) para olhar depois. E o [wiki do Termux](https://wiki.termux.com/wiki/Main_Page) para aprofundar.

Assim que instalar e abrir o Termux vai aparecer uma linha de comando. Copie para lá o seguinte comando:

$ `curl https://raw.githubusercontent.com/mauro-zac/Trilha-Digital/master/m%C3%B3dulos/cidadania_digital/internet.md`

O que aconteceu? Você acessou o conteúdo desta aula em texto-plano (*raw*) diretamente do site do GitHub. O [comando curl](https://pt.wikipedia.org/wiki/Curl_(Unix)) encontrou o servidor especificado no endereço *github.com*, usando o protocolo *https* e retornou o conteúdo que está lá disponível, fisicamente salvo em um *datacenter* em algum lugar do mundo. Todo esse processo ocorreu em frações de segundo. 

O curl baixa o conteúdo exatamente como está no servidor. No link acima, o texto *raw* é perfeitamente legível. Mas tente agora baixar uma página mais típica da internet:

$ `curl https://github.com/mauro-zac/Trilha-Digital/blob/master/m%C3%B3dulos/cidadania_digital/internet.md`

O mesmo texto agora chega misturado em uma "sopa de letrinhas". Essa sopa é nada mais do que o código-fonte da página *web* escrito em HTML5. É isso que um navegador de internet (*browser*) espera receber. Ele usa as instruções contidas nesse código para montar a página para você. Abra o mesmo endereço em um navegador para conferir.

O curl mostra como uma página de fato é transmitida pela internet. Dizemos que o trabalho de montar e mostrar a página é feito no **cliente** porque é o navegador que você usa quem realiza esse processo. O **servidor** envia o que o você vê pelo curl (que não é um navegador e não sabe como processar os comandos que estão no código-fonte).

Mas o curl é capaz de mostrar outras coisas interessantes.

$ `curl --head https://github.com/mauro-zac/Trilha-Digital/raw/master/m%C3%B3dulos/cidadania_digital/internet.md`

A adição do sufixo `-head` informa o curl que você quer ver o [cabeçalho do protocolo HTTP](https://pt.wikipedia.org/wiki/Lista_de_campos_de_cabeçalho_HTTP). Esse pacote de informação é sempre parte das transações entre cliente e servidor e contém diversas instruções e declarações úteis para que a comunicação funcione e para que eventuais erros sejam corrigidos. Por exemplo, se tudo correr bem você verá em algum lugar do cabeçalho:

`Status: 200 OK`

Você já deve ter se deparado com um site te pedindo para **aceitar cookies**. Mas você já viu um [cookie](https://en.wikipedia.org/wiki/HTTP_cookie)? Basta procurar no cabeçalho do HTTP, é por onde ele vem. O tal de cookie na vida real não é lá tão simpático, mas olhando de perto é isso o que a gente vê!

`Set-Cookie: _gh_sess=WGFkREVGQVJtdTJvazV4azljK05Ja1Q3U3RpUG5zUWdHdGtuS1RyWk01b1ZCbEZhL0VicHlucS9GM2dsdXdad1FuS05mbHkxRTFRM2NyYStIeFdNazB0S3g1Sk8zQTkwZFFMdEpON2hKUVJvdFlzUXgzc2JHajBVNmlucE8xazFNQU9IKyt1Z0dvaDBZVXpkZFM4dzBGTk96b0FMYjlBaUhuVTNrRXJSYVVLSllMcmkzQ0lvbWVrVHg4UEgyR1hZaHJJTGpDdFZudFhXQkMya3hIbGo2QzdSck9QUG5iS2hLd2RtTStjOU9vTWdCb0NnNmFoTUZrN1JxWjJPZjNGcnM2MXFNeGxJd1U3MTdRUkUxM1hVMXVyT0FTVGVnbXBYR3ZTdGNJRkkySTQ9LS01dmFhNWdJQXQxbHQzNmY1OEtJZFN3PT0%3D--ee7b1af97c971c10b33689ece64315e32f464d34; path=/; secure; HttpOnly`

O comando curl faz muitas outras coisas importantes. Por exemplo, ele é um aliado seguro para examinar sites suspeitos. Como o curl é incapaz de executar os códigos que baixa, ele te permite investigar páginas maliciosas sem correr riscos.

$ `curl --help` mostra outras possibilidades de uso do comando curl.

#### 2) Servidores

Muita gente imagina que um servidor é algum tipo de computador extremamente sofisticado e caro, cheio de luzinhas piscando e fios conectados em um *datacenter*. Ok, a maioria dos grandes sistemas operando *em produção* é desse tipo e requer muitas etapas de configuração para funcionar de modo otimizado e seguro.

Mas não é isso que define um servidor. Na internet, qualquer máquina pode ser um servidor. Até o seu celular. 

Um servidor é simplesmente um computador configurado para receber **requests** (pedidos, requerimentos) de outros computadores e entregar os conteúdos solicitados. O computador que envia o *request* e recebe a *response* (resposta) é o **cliente**.

Para que cliente e servidor se entendam eles precisam falar a mesma língua. Vimos com o curl como é a cara do protocolo HTTP, uma das línguas mais usadas. O HTTP foi criado para transmitir as páginas da web, chamadas antigamente de híper-texto: *Hyper Text Transmition Protocol*. Mas na prática, dados, arquivos, imagens e vídeos também podem ser transimitidos pelo HTTP, mesmo ele não sendo o modo mais eficiente para todos os casos.

O cliente declara que língua está usando bem no ínício da frase: "https://..." 

O HTTPS é uma variante mais segura do protocolo HTTP capaz de [criptografar](https://pt.wikipedia.org/wiki/Criptografia) os dados transmitidos. Sem a criptografia, as mensagens podem ser lidas por terceiros enquanto transitam na rede. 

Outros protocolos bastante utilizados na internet incluem SSH, FTP, POP, IMAP, SMTP e WS. Procure saber mais sobre eles. Mas depois, porque a atividade de hoje será transformar seu celular em um servidor.

Todo navegador (Chrome, Firefox, Safari, Edge, etc.) é capaz de fazer requisições dirigidas à própria máquina em que está instaldao. Chamamos isso de requisição local ou ao *localhost*. Se nossa máquina estiver servindo algum conteúdo, ele será visível no endereço:

`http://localhost`

Se você acessar esse endereço em sua máquina, provavelmente será informado de que o navegador não pode acessar o site ou que a conexão foi recusada. Tente acessar para ver. Está certo, se não houver nada sendo servido, não vai ter nada mesmo para ser visto.

Para ativar um servidor localmente, vamos primeiro precisar instalar o Python.  

$ `pkg install python`

Você vai usar Python para muitas coisas na Trilha Digital, é bom ter ele por perto inclusive em seu celular!

Ok, uma vez instalado o Python, rode este comando:

$ `python -m http.server 8000 --bind 127.0.0.1`

E acesse novamente o localhost pelo navegador:

`http://localhost:8000`

Ah, você agora pode ver parte da estrutura de diretórios de seu celular! O programa `http.server` está servindo as pastas e os arquivos de seu celular para o endereço 127.0.0.1 (que é o número de IP padrão para o *localhost*). Nesse exemplo, instruímos o programa para servir os dados pela porta 8000. A porta padrão do http é a 80, mas constumamos não usar essa porta fora de um ambiente de produção bem configurado.

Para desligar o servidor, você precisa executar o comando `CTRL+C` no Termux. Mas antes de desligar note as mensagens mostrando as respostas do servidor aos acessos do navegador, você vai encontrar algo como `"GET / HTTP/1.1" 200` mostrando que o servidor recebeu um request do tipo GET usando o protocolo HTTP 1.1 e respondeu corretamente gerando uma mensagem de status 200 que significa OK.

E você pode rodar até programas mais parrudos do que o servidor do Python. Por exemplo o [Nginx](https://nginx.org/), um dos melhores e mais usados no mundo.

$ `pkg install nginx`

$ `nginx` para ligar

$ `nginx -s stop` para desligar

O nginx por padrão serve na porta 8080:

`http://localhost:8080` e você verá uma página em HTML: "Welcome to nginx!". Ela é servida a partir de um diretório. Caminhe até lá no Termux:

$ `cd /data/data/com.termux/files/usr/share/nginx/html`

Vamos usar um editor de texto chamado *nano* para olhar e modificar o index.

$ `pkg install nano`

$ `nano index.html`

Você verá a página do Welcome com a marcação do HTML. Modifique uma linha, por exemplo:

`<h1>Bem-vindo à Trilha Digital!</h1>`

Use `CTRL+X` para sair e não se esqueça de confirmar (YES) que quer salvar o arquivo. 
   
Vá ao navegador e recarregue `http://localhost:8080`. Pronto, você está virando um desenvolvedor!

Se liga: não deixe servidores ativos em seu celular. Depois de brincar com eles, desligue-os!

#### 3) Explorando endereços de IP (TO_DO)

$ `curl ifconfig.me`

[Python Geocoder](https://github.com/DenisCarriere/geocoder)

$ `pip install geocoder`



#### 4) 



-----
#### Não deixe de dar uma olhada em: 

https://pt.wikipedia.org/wiki/Internet

