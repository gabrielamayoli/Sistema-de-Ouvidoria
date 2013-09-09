##Descrição do Produto

O Sistema de Ouvidoria foi desenvolvido em plataforma livre e possibilitará que um cidadão, externo à organização ou empregado desta, submeta mensagens (denúncias, reclamações, críticas, sugestões) para análise e resposta da Ouvidoria da instituição. Isto permitirá que se mantenha aberto um canal de comunicação entre o cidadão e a instituição, auxiliando na identificação de problemas da organização. Através deste sistema a Ouvidoria da instituição poderá efetuar o diagnóstico e a análise dos acionamentos submetidos, visando a rápida solução de questionamentos. Será permitido ao cidadão acompanhar o andamento de seu acionamento através da internet ou de serviço de atendimento da Ouvidoria.

O sistema permitirá a emissão de relatórios gerenciais, apresentando estatísticas dos dados consolidados, visando não só possibilitar melhorias no processo de atendimento da ouvidoria como, também, facilitar o diagnóstico dos problemas nos processos da organização. A área estratégica da Ouvidoria poderá acompanhar todo o processo de atendimento a um acionamento, podendo inclusive agir no processo de solução. O Sistema poderá ser utilizado por Organizações com estrutura orgânica compostas de vários órgãos ou por um único órgão.

##Pré-requisitos

MySQLServer 4.1.20 instalado;
MySQL Administrator instalado;
Tomcat 5.0.28 instalado 1;
Java 1.4.2;
Eclipse 3.6 ou superior instalado 1;
Browser Firefox 3.0 ou superior 2.
Maven 2 3.

1. A codificação padrão da aplicação deve ser “UTF-8”, esteja ela rodando dentro do Eclipse ou direto no servidor.
2. Garantimos o correto funcionamento da aplicação neste browser. Para utilização de outros navegadores, deverão ser realizados testes para garantir a compatibilidade.
3. O Maven é o responsável por manter as dependências de bibliotecas utilizadas pelo software.

O software foi testado utilizando estas versões. A utilização de versões diferentes pode ocasionar erros.
Caso você seja um usuário iniciante, sugerimos que você use o framework Demoiselle, disponível também no Portal Software Público. O Eclipse e o Maven vem instalado e integrado no framework. O Servidor Tomcat disponível no framework não é recomendado, sendo melhor utilizar em separado. Também é preciso que, ao fazer a instalação e configuração, o servidor tenha acesso à internet para que o Maven possa fazer download das bibliotecas utilizadas na aplicação.
	
##Instalação

##Banco de dados

Passo 1: Baixe o script sistema_ouvidoria.sql na sessão de download

Passo 2: Abra o MySQL Browser, escolha a opção OpenScript do menu File e selecione o arquivo sistema_ouvidoria.sql para que seja aberto;

	
![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/imagens/1.png) &nbsp;
	


Passo 3: Execute o script para a criação do banco de dados com os dados mínimos para configuração de um novo Órgão;



![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/imagens/2.png) &nbsp;












##Aplicação
	
Passo 1: Baixe os arquivos-fonte do Sistema Ouvidoria e faça a configuração do projeto no Eclipse apontando para o diretório onde serão armazenados. Para isso, abra o Eclipse, vá em “File → Import”. Abrirá a tela de seleção do tipo de importação a se fazer. Escolha a opção “Maven → Existing Maven Project”

![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/3.JPG) &nbsp;

Em seguida, você irá indicar ao Eclipse, onde está o código fonte da aplicação. Indique a pasta onde está o código da aplicação baixado do portal. O Eclipse irá 'enxergar' o arquivo de configuração 'pom.xml'. Selecione o arquivo e clique em Finish. Após isso, o Eclipse irá verificar as dependências e fará o download automático das bibliotecas que você irá precisar.

![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/4.JPG) &nbsp;


Obs: O arquivo pom.xml do Maven, assim como outros arquivos de configuração, foram configurados para funcionamento da aplicação com o servidor Tomcat. Para utilização com outros servidores de aplicações, podem ser necessárias algumas alterações no arquivo, como por exemplo, remoção de bibliotecas que o servidor já possua.

Passo 2: Configuração de banco nos arquivos context.xml e hibernate.cfg.xml com o nome do database, usuário e senha criados. Abra o arquivo 'context.xml' no caminho indicado na figura abaixo


![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/5.JPG) &nbsp;














Procure pelas linhas onde estão os parâmetros “username” e “password”. Nos valores destes parâmetros insira o nome de usuário e a senha que terão permissão de acesso ao banco de dados.

           


![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/6.JPG) &nbsp;















Agora, configure o arquivo 'hibernate.cfg.xml'. O arquivo está no caminho indicado na figura abaixo








![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/7.JPG) &nbsp;







Configure a string de conexão da aplicação com o banco de dados. Insira também o 'username' e o 'password' para acesso ao banco de dados. Não se esqueça de mudar o parâmetro “Show Sql” para false caso não queria que ele seja impresso no console/log.

![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/8.JPG) &nbsp;


Passo 3: Geração do pacote “ouvidoria.war” da aplicação Ouvidoria.
Antes de gerar o pacote 'war', é interessante que você clique com o botão direito do mouse no nome do projeto (ouvidoria) e escolha a opção “Refresh”. Também é recomendado que você clique com o botão direito do mouse no arquivo 'pom.xml' e escolha a opção “Run as → Maven Clean”. Com isso, garantimos que o arquivo 'war' será gerado totalmente atualizado. Feito isso, clique com o botão direito do mouse no nome do projeto (Ouvidoria), escolha a opção “Export → War File”. Escolha o local onde o arquivo será criado e clique em “Finish”.

![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/9.JPG) &nbsp;

Passo 4: Após gerar o arquivo ouvidoria.war, copie o mesmo para a pasta  “webapps” do Tomcat . 

Passo 5: É necessário configurar alguns parâmetros da JVM que serão usados na inicialização do Tomcat.
Para um ambiente Linux, no diretório raiz do Tomcat, crie o arquivo setenv.sh (caso ainda não exista) e adicione a este arquivo a seguinte linha:

	export JAVA_OPTS="-server -Xms32M -Xmx256M"

Caso você tenha instalado em sua máquina, outra versão do java, é necessário também dizer ao Tomcat qual versão do Java deverá ser utilizada. Para isso, sugerimos que você procure por tutoriais adequados ao seu ambiente de trabalho, pois essa configuração varia de acordo com o sistema operacional e a versão do sistema instalado.

Passo 6: Após iniciar o Tomcat, acesse a aplicação pelo browser.  O Tomcat, por padrão, responde as requisições na porta 8080. Portanto, se as únicas modificações feitas no arquivo context.xml foram a do usuário e senha do banco, o caminho para acesso será “http://localhost:8080/ouvidoria”.


![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/10.JPG) &nbsp;



##Configurando um novo Órgão

Passo 1: Para configurar uma nova Ouvidoria, você deverá acessar a aplicação com o usuário Administrador do Sistema (CPF → 11111111111, senha → 123). Para ter acesso ao menu “Acesso Restrito” é necessário alterar a URL substituindo o trecho “MainInternet” por “MainIntranet”:

![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/11.JPG) &nbsp;

Passo 2: Após o acesso, configure os parâmetros gerais do sistema , acessando o 	menu “Administrar/Parâmetros Gerais”.

![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/12.JPG) &nbsp;

Passo 3: Verifique se o campo “Diretório raiz da aplicação” foi preenchido com uma estrutura de diretório válida, com permissões de leitura e escrita para o usuário do Tomcat (novamente, para saber como fazer isso, é necessário saber qual sistema operacional e versão do sistema você está usando e buscar por um tutorial adequado, pois essas configurações podem variar). Esse será o diretório de trabalho do sistema e será usado para criar os anexos e outros arquivos necessários. Também tenha o cuidado de colocar um endereço válido para o servidor de e-mail que será usado na aplicação. Por último, tenha o cuidado de incluir uma “/” ao final do caminho do diretório raiz da aplicação.

Passo 4: Cadastre o um novo Órgão, acessando o menu “Administrar/Manter Órgãos”
	
![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/13.JPG) &nbsp;

Nesta parte da instalação, é preciso ter um cuidado especial com as datas de configuração do novo órgão criado. Tenha certeza que:
– A data de Inicio da Operação seja maior que a Data de Fim de Cadastramento.
A data de Inicio de Acionamento  seja maior que a Data de Inicio de Cadastramento.
A data de Inicio Consulta de Resposta seja maior que a Data de Inicio de Acionamento
Para as datas de fim, utilize a mesma lógica usada para as Datas de Início.


Passo 5: Após o cadastro do novo órgão, atualize as configurações do órgão, acessando “Administrar/Manter >> Órgão”. Após isso clique no botão 	“Atualizar Configuração” pertinente ao Órgão cadastrado. Abaixo, explicações sobre os textos que são configuráveis e qual a finalidade de cada um.

![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/14.JPG) &nbsp;

![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/15.JPG) &nbsp;

![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/16.JPG) &nbsp;

![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/17.JPG) &nbsp;
	

Abaixo, uma explicação para os demais campos de configuração:

Notificar aos responsáveis por acionamento sem resposta / Hora/Minuto do Envio de Notificação (HH:MM) 
O sistema pode gerar um e-mail de cobrança para os responsáveis por responder aos acionamentos abertos no sistema. Juntamente com a mensagem de cobrança, é enviado o link de acesso direto a mensagem, bem como a situação em que ela se encontra. A mensagem é enviada diariamente, no horário indicado.

Órgão permite anexar arquivo ao acionamento / Tamanho máximo para arquivos anexos (em KB) 
É possível permitir que sejam anexados arquivos ao acionamento. Este campo habilita esta opção, e o tamanho máximo permitido para cada anexo. O tipo de arquivo que pode ser anexado é configurado na opção “Administrar → Parâmetros Gerais”

Órgão permite mensagem digitalizada no acionamento 
Funciona de maneira similar a opção anterior.

Órgão possui código de acesso 
Indica se o usuário receberá um código de acesso para consulta aos acionamentos. O código de acesso é gerado junto com o protocolo de atendimento

Existe bloqueio por falhas na digitação do código de acesso /Número máximo de falhas no código de acesso /Tempo de bloqueio pelo código de acesso (em minutos)
Indica se o sistema irá bloquear a consulta a um determinado protocolo, uma vez o código de acesso seja digitado errado. É necessário informar o número de tentativas erradas que irá resultar no bloqueio, e o tempo em minutos que este bloqueio irá funcionar.

Existe bloqueio por falhas na digitação da pergunta para recuperação do código de acesso / Número máximo de falhas no código de acesso / Tempo de bloqueio pelo código de acesso (em minutos)
Similar a opção anterior.

Atendente pode consultar mensagens durante o atendimento
Indica se o usuário com perfil de “Atendente” poderá acessar o sistema e consultar acionamentos durante a realização de um atendimento a usuário. 
	
 é exigido certificado digital para acesso ao órgão e a todos os sub-órgãos / é exigido certificado digital para acesso ao órgão e opcional para todos os sub-órgãos 

Nome do diretório do órgão
Aqui é informado o diretório onde serão armazenados os dados do órgão criado. Note que o nome do diretório deve ser exatamente igual ao diretório criado, pois de outro modo, os anexos e imagens não serão salvos corretamente.

URL para consulta de funcionários

URL de suporte ao usuário 
Indica algum endereço internet/intranet que o usuário poderá acessar para ajudá-lo a fazer o acionamento de forma correta.


Remetente dos e-mails que serão enviados pela aplicação 
O e-mail informado aqui será visualizado pelos usuários como o remetente de todas as mensagens do sistema. Geralmente é usado um e-mail corporativo como 'ouvidoria@orgao.br'. Não é recomendado o uso de um e-mail pessoal.

Tipos de acionador permitidos para o órgão
Indica de que maneira o usuário poderá se identificar ao fazer um acionamento.

Meios de envio de resposta permitidos para o órgão

Indica que meio de comunicação o usuário pode informar para o recebimento de sua resposta.


		
Passo 6
Após o cadastro, altere a classe OrgãoCtrl.java configurando o código do órgão 	(variável orgaoId),	recém cadastrado, da seguinte forma:
	
a) Obtenha o código do órgão recém cadastrado consultando o banco de dados 	da aplicação (tabela INSTITUICAO coluna COD_INSTIT).

b) Vá novamente ao Eclipse, encontra a classe OrgãoCtrl.java e substitua o código de órgão existente pelo código de órgão da nova instituição. 
	
	
	
![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/18.JPG) &nbsp;

	




Feita esta substituição, salve o arquivo e execute novamente o procedimento de criação do  pacote  'ouvidoria.war'
Esta parte é um pouco trabalhosa, então vamos explicar detalhadamente. Não será feito um novo “Deploy” da aplicação. Iremos apenas gerar o código fonte novamente, desta vez com o código do órgão criado. Antes de gerar o novo arquivo “ouvidoria.war”, pare o servidor tomcat. 
Uma vez parado o servidor, abra o arquivo 'ouvidoria.war' com um descompactador de arquivo (os arquivos '.war' na verdade são arquivos compactados para serem lidos por servidores web). Depois de descompatar os arquivos, substitua os arquivos da pasta '[diretório do tomcat]/webapps/ouvidoria/', pelos novos arquivos e em seguida apague o arquivo 'ouvidoria.war' (isto impede que o servidor enxergue o novo arquivo “.war” e faça um novo deploy da aplicação). Em seguida, no console do terminal, digite o comando 'touch /[diretório do tomcat]/webapps/ouvidoria/WEB-INF/web.xml”. Este comando irá modificar a data e hora do arquivo web-xml, e com isso o servidor tomcat irá atualizar a aplicação. Feito isso, basta reinicar o servidor tomcat.
	
Passo 7
Por fim, acesse novamente a aplicação e já estará usando o novo Órgão.
Para acessar a parte de “acesso restrito”, como na figura, basta editar a url de   acesso no navegador, trocando a parte onde diz “MainInternet” para “MainIntranet”

![](https://github.com/gabrielamayoli/Sistema-de-Ouvidoria/blob/master/Imagens/19.JPG) &nbsp;
	

Passo 8
Por fim, crie as informações necessárias para uso do sistema. A melhor ordem é se criar “Sub Órgão”, “Localidades”, “Tipos de Mensagens”, “Assuntos de 	Mensagens”, “Usuários”, nessa ordem, de forma a atender todas as dependências 	para o funcionamento do sistema. Obrigatoriamente, você precisa cadastrar um 	usuário no perfil “Ouvidor Geral”.
