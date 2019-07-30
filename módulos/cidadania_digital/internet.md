# Internet

`Cidadania Digital` `4 horas-aula`

`Objetivos` Apresentar e discutir os principais conceitos, protocolos e infraestruturas que viabilizam a internet.

`Competências` Conhecer o quê é e como funciona a internet; compreender as principais nomenclaturas e unidades físicas; distinguir entre infraestrutura, protocolos e diferentes camadas de serviços. 

`Roteiro`

> Muitas pessoas não sabem diferenciar o que é o Facebook ou o Google do que é a Internet, e só acessam a rede através desses servidores centralizados. [El País 29/07/2019](https://brasil.elpais.com/brasil/2019/07/30/tecnologia/1564437803_087942.html)

#### 1) Dando uma olhada mais de perto em como ocorre a comunicação na internet

Você ou alguém por perto deve ter em mãos um celular Android. Vamos usar esse aparelho de um modo diferente para acessar a internet. Um celular Android é um computador bastante sofisticado, mas a interface para o usuário é bastante restrita. Fica limitada aos aplicativos.

Ficava!

Vamos instalar o [Termux](https://play.google.com/store/apps/details?id=com.termux&hl=pt) e abrir uma janela para dentro do seu celular! Tem um ótimo [tutorial sobre o básico do Termux aqui](https://sempreupdate.com.br/conheca-o-termux-e-aproveite-ao-maximo-o-linux-no-android/) para olhar depois. E o [wiki do Termux](https://wiki.termux.com/wiki/Main_Page) para aprofundar.

Assim que instalar e abrir o Termux vai aparecer uma linha de comando. Copie para lá o seguinte comando:

$ `curl https://github.com/mauro-zac/Trilha-Digital/raw/master/m%C3%B3dulos/cidadania_digital/internet.md`

O que aconteceu? Você acessou o conteúdo desta aula em texto-plano (*raw*) diretamente do site do GitHub. O [comando curl](https://pt.wikipedia.org/wiki/Curl_(Unix)) encontrou o servidor especificado no endereço *github.com*, usando o protocolo *https* e retornou o conteúdo que está lá disponível, fisicamente salvo em um *datacenter* em algum lugar do mundo. Todo esse processo ocorreu em frações de segundo. 

O curl baixa o conteúdo exatamente como está no servidor. No link acima, o texto *raw* é perfeitamente legível. Mas tente agora baixar uma página "normal" da internet...

$ `curl https://github.com/mauro-zac/Trilha-Digital/blob/master/m%C3%B3dulos/cidadania_digital/internet.md`

O mesmo texto agora chega misturado em uma "sopa de letrinhas". Essa sopa é nada mais do que o código-fonte da página *web* escrito em HTML5. É isso que um navegador de internet (*browser*) espera receber. Ele usa as instruções contidas nesse código para montar a página para você. Abra o mesmo endereço em um navegador para conferir.

O curl mostra como uma página de fato é transmitida pela internet. Dizemos que o trabalho de montar e mostrar a página é feito no **cliente** porque é o navegador que você usa quem realiza esse processo. O **servidor** envia o que o você vê pelo curl (que não é um navegador e não sabe como processar os comandos que estão no código-fonte).

Mas o curl é capaz de mostrar outras coisas interessantes.

$ `curl https://github.com/mauro-zac/Trilha-Digital/raw/master/m%C3%B3dulos/cidadania_digital/internet.md --head`

A adição do sufixo `-head` informa o curl que você quer ver o [cabeçalho do protocolo HTTP](https://pt.wikipedia.org/wiki/Lista_de_campos_de_cabeçalho_HTTP). Esse pacote de informação é sempre parte de toda transação entre cliente e servidor e contém diversas instruções e declarações úteis para que a comunicação funcione e para que eventuais erros possam ser corrigidos. Por exemplo, se tudo correr bem você verá em algum lugar do cabeçalho:

`Status: 200 OK`

Você já deve ter se deparado com um site te pedindo para aceitar cookies. Mas você já viu um cookie? Basta procurar no cabeçalho do HTTP, é por ele que o [cookie](https://en.wikipedia.org/wiki/HTTP_cookie) vem. O tal de cookie na vida real não é lá tão simpático, mas olhando de perto é isso o que a gente vê!

`Set-Cookie: _gh_sess=WGFkREVGQVJtdTJvazV4azljK05Ja1Q3U3RpUG5zUWdHdGtuS1RyWk01b1ZCbEZhL0VicHlucS9GM2dsdXdad1FuS05mbHkxRTFRM2NyYStIeFdNazB0S3g1Sk8zQTkwZFFMdEpON2hKUVJvdFlzUXgzc2JHajBVNmlucE8xazFNQU9IKyt1Z0dvaDBZVXpkZFM4dzBGTk96b0FMYjlBaUhuVTNrRXJSYVVLSllMcmkzQ0lvbWVrVHg4UEgyR1hZaHJJTGpDdFZudFhXQkMya3hIbGo2QzdSck9QUG5iS2hLd2RtTStjOU9vTWdCb0NnNmFoTUZrN1JxWjJPZjNGcnM2MXFNeGxJd1U3MTdRUkUxM1hVMXVyT0FTVGVnbXBYR3ZTdGNJRkkySTQ9LS01dmFhNWdJQXQxbHQzNmY1OEtJZFN3PT0%3D--ee7b1af97c971c10b33689ece64315e32f464d34; path=/; secure; HttpOnly`

O comando curl faz muitas outras coisas importantes. Por exemplo, ele é um aliado seguro para examinar sites suspeitos. Como o curl é incapaz de executar os códigos que baixa, ele te permite investigar páginas maliciosas sem correr riscos.

$ `curl --help` mostra outras possibilidades de uso do comando curl. Divirta-se.


#### 2) Infraestrutura

$ `curl ifconfig.me`


#### 3) Protocolos


#### 4) Camadas de serviços


#### 5) Aplicações


-----
#### Não deixe de dar uma olhada em: 

https://wiki.termux.com/wiki/Main_Page

https://pt.wikipedia.org/wiki/Internet

