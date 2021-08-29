# Auditoria no cluster Hadoop.

[![NPM](https://img.shields.io/npm/l/react)](https://github.com/pand-eX/Teste_Invas-o/blob/main/LICENSE) 

# About the project

Basicamente irei verificar as falhas e vulnerabilidade do Data Lake que implementei com o Apache Hadoop e como eu implementeie no cluster Alta Disponibilidade e configurei segurança com o Kerberos será um bom teste de vulnerabilidade


## Porque? 

Porque esse é um procedimento necessário afinal se uma pessoa mal-intencionada conseguir encontrar alguma brecha no ambiente Hadoop ele poderá faze bastante estrago na organização. O objetivo desse projeto e testar o meu próprio ambiente de cluster Hadoop e melhorar a segurança do ambiente de Big Data.

-Este projeto faz parte do meu portfólio pessoal, então ficarei feliz se você puder me fornecer qualquer feedback sobre o projeto, código, estrutura ou qualquer coisa que você possa relatar que possa me fazer um melhor engenheiro de dados!

Email-me: henricao_7@yahoo.com.br

Connect with me at [LinkedIn](https://www.linkedin.com/in/henrique-castro-484269203//).

## O que é um Teste de Penetração – PENTEST?

Teste de penetração (PENTEST) é o teste realizado para verificação de vulnerabilidades analisando os ativos expostos (Rede, Servidores, Aplicativos) em busca de falhas existentes.
Basicamente queremos verificar as falhas em nossos sistemas. Seja ele de rede, sistema de uma aplicação, eventualmente o conjunto de servidores, ou seja, o principal objetivo de um teste de penetração é verificar se empresa está vulnerável a algum tipo de invasão ou violação dos seus sistemas. Em geral quando você realiza um teste de penetração você executa o teste até que o objetivo seja alcançado, ou seja, você traça um objetivo eu quero checar se tem alguma porta aberta nos servidores da empresa com esse objetivo em mente você prepara o teste e então faz a checagem de vulnerabilidade. Um teste de penetração deve ser feito regularmente por qualquer empresa. Também é comum ter teste sempre que há uma mudança na infraestrutura por exemplo mudou a regra de Firewall por mais que seja uma mudança pequena e interessante fazer um novo teste de penetração por essa regra pode afetar uma outra regra e assim por diante.

Análise de vulnerabilidade é o teste realizado a fim de identificar vulnerabilidades em sistemas ou redes.
Testes de Penetração verificam e “exploram” essas vulnerabilidades de forma segura e controlada. Ou seja, simulamos a exploração das vulnerabilidades.

## Trazendo o Contexto para o Big Data
Estamos olhando o seguinte primeiro o relatório para chegar as deficiências em nosso sistema depois uma outra atividade para tentar explorar exatamente essas fraquezas são duas ações diferentes.
Existe 3 testes de penetração o primeiro é o Teste de Penetração Externa basicamente verificar se pela internet nós conseguimos explorar algum tipo de vulnerabilidade no sistema, serviço ou aplicativos expostos a internet. Quaisquer sistemas expostos a internet corre risco a minha máquina, um Website, banco de dados, aplicações Web e etc... Você pode primeiro fazer uma análise verificar se há ou não uma vulnerabilidade depois tenta explora-las porque o fato de ter uma vulnerabilidade não significa que era será explorada por alguém com uma pessoa mal-intencionada.
Teste de Invasão Interna que tem como objetivo simular um funcionário mal-intencionado que tente copiar dados de um banco de dados, apagar dados de um banco de dados para esconder alguma fraude por exemplo e etc... O teste é basicamente para antecipar esse tipo de problemas, além disso tem outras questões interessante imagine um funcionário de uma grande empresa ele acaba de receber um email que diz clique neste link para ganhar alguns milhões de dólares pode ser que algum funcionário curioso clique para ver então praticamente a máquina recebeu um Malware ou algum tipo de vírus na máquina do usuário e com esse tipo de problema pode abrir uma porta de acesso para que outros usuário externo mal-intencionado ganhe acesso ao computador ao sistema e consiga copiar senhas e etc... Então o teste de Penetração interna é simular primeiro usuários mal-intencionados e segundo fazer uma varredura em busca de Malware, vírus ou qualquer tipo de ameaça ao sistema interno da empresa porque uma vez que o malware esteja instalado toda empresa está sobre risco. Pode ter o melhor Firewall do mundo não adianta porque alguém já entrou na rede da empresa.
O Terceiro tipo é Avaliação de Aplicações Web porque toda aplicação tem Bugs então podemos fazer um teste para explorar exatamente esses bugs porque se o bug for muito crítico eventualmente temos que buscar uma correção.

As cinco fases de um Pentest (Penetrationt Test) se referem às etapas principaisdo processo de operação de um teste de penetração, e o conceito é crítico para compreender como o teste funciona. 

## Aqui está uma visão geral das cinco fases do teste de penetração:

Fase 1: Reconhecimento.
Reconhecimento é o ato de coletar dados ou informações preliminares sobre seu alvo. Os dados são coletados para melhor planejar seu ataque. O reconhecimento pode ser realizado ativamente (o que significa que você está tocando diretamente no alvo) ou  passivamente  (o  que  significa  que  o  reconhecimento  está  sendo realizado por meio de um intermediário).

Fase 2: Scanning

A fase de varredura requer a aplicação de ferramentas técnicas para coletar mais informações sobre o seu destino, mas, neste caso, as informações procuradas são mais comuns sobre os sistemas que eles possuem. Um bom exemplo seria o uso de um scanner de vulnerabilidades em uma rede de destino.

Fase 3: Ganhando acesso

A fase 3 para obter acesso requer o controle de um ou mais dispositivos de rede para extrair  dados do destino ou usar esse  dispositivo para iniciar  ataques a outros destinos.

Fase 4: Manutenção do acesso

Manter o  acesso requer as etapas  envolvidas  para  poder  permanecer persistentemente  no  ambiente de destino para coletar o máximo  de dados possível. O invasor deve permanecer furtivo nesta fase, para não ser pego enquanto estiver usando o ambiente host.
Fase 5: Cobrindo Rastros
A fase final de cobrir rastros significa simplesmente que o atacante deve tomar as medidas necessárias para remover qualquer sinal que possa ser detectado. Quaisquer alterações feitas, autorizações que foram encaminhadas, etc. devem retornar a um estado de não reconhecimento pelos administradores da rede host.
O Kali Linux nos oferece ferramentas para todas essas fases.
Em geral nós começamos um teste de checagem de segurança verificando as portas abertas no Host alvo na máquina alvo onde nós queremos realizar o teste de vulnerabilidade e o teste de penetração temos duas ferramentas de grande nível para isso no Kali Linux lembrando que não é exclusividade do Kali Linux você pode usar em qualquer ambiente Linux.

![1](https://github.com/pand-eX/Teste_Invas-o/blob/main/Teste%20De%20Penetra%C3%A7%C3%A3o%20no%20Cluster%20Hadoop/assets/1.png)

Fazendo um Scan na máquina destino e descobri que uma série de serviços estão disponíveis em diferentes portas. Então já temos uma dica importante. Quando for montar um servidor coloque apenas o serviço que for realmente necessário se ele não deve estar ativo deslique-o. Porque ele pode ser uma porta de entrada ou uma possível porta para uma invasão.
A ferramenta Searchsploit ela tem um banco de dados de vulnerabilidade eu quero verificar se tem alguma vulnerabilidade disponível no Mysql 5

![2](https://github.com/pand-eX/Teste_Invas-o/blob/main/Teste%20De%20Penetra%C3%A7%C3%A3o%20no%20Cluster%20Hadoop/assets/2.png)

E encontramos diversas vulnerabilidade na verdade todos os softwares possui vulnerabilidade é puramente questão de tempo para um ambiente seja exposto a falha de segurança por isso a equipe de segurança e os administradores deve estar sempre vigilantes rodando teste de vulnerabilidade, checagem de segurança, instalando patch de correção, atualizando versões e etc... 


## Chegando vulnerabilidade 


![3](https://github.com/pand-eX/Teste_Invas-o/blob/main/Teste%20De%20Penetra%C3%A7%C3%A3o%20no%20Cluster%20Hadoop/assets/3.png)


existe uma vulnerabilidade de Denial-of-service, ou seja, negação de serviço. Um hacker mal-intencionado pode explorar esse problema e quebrar o banco de dados dar um crash no banco de dados simplesmente negando acesso para usuários legítimos esse problema afeta versões anteriores ao MySQL 5.1.49. Essa é a importância de usar o Kali Linux as ferramentas estão todas disponíveis. Você faz um Scan das portas encontra os serviços rodando depois verifica se tem alguma vulnerabilidade com exploits que possam ser explorados por hackers mal-intencionados naqueles serviços se eu tiver usando versão 5.1.48 do MySQL valeria a pena atualizar para 5.1.49 simplesmente para não ter meu banco de dados exposto a essa vulnerabilidade esse é o trabalho de segurança que precisa ser feito. 


## Isso é uma visão geral da ferramenta do Kali Linux o foco será para meu ambiente de Big Data com Apache Hadoop que construí para ver possíveis falhas de segurança.
Vamos inicializar o laboratório.

Primeira coisa é checagem básica de segurança e ao mesmo tempo importante nós vamos verificar quais máquinas estão ativas nesta rede e vamos coletar o nome dessas máquinas tudo isso a partir do Kali Linux. As vezes algumas pessoas esquecem a máquina ligada em um CPD (Centro de processamento de dados) muito grande.
Vamos usar a ferramenta Nmap do Kali Linux.
O comando é arp-scan (e a rede que eu quero fazer o scan) é um envio de várias mensagens, vários pacotes na rede e se estiver alguma máquina ligada ela vai responder aquela solicitação e vamos checar no relatório
Enquanto faz o Scan temos uma alternativa que é outra ferramenta chamada Wireshark que é um analisador de tráfego de rede como se fosse um Sniffer, ou seja, ele vai ficar ouvindo tudo que passa na rede e vai contar para nós.


![4](https://github.com/pand-eX/Teste_Invas-o/blob/main/Teste%20De%20Penetra%C3%A7%C3%A3o%20no%20Cluster%20Hadoop/assets/4.png)

![5](https://github.com/pand-eX/Teste_Invas-o/blob/main/Teste%20De%20Penetra%C3%A7%C3%A3o%20no%20Cluster%20Hadoop/assets/5.png)

esse é meu arquivo hosts do Cluster ele conseguiu pegar o ip das máquinas na rede do meu Cluster Hadoop e outros que estavam na rede.
Esse é o primeiro passo agora que temos o ip nós vamos tentar um Password Crack, ou seja, vamos checar se os usuários dessas máquinas estão com senhas conhecidas, senhas simples. E usaremos a Hydra basicamente ela vai fazer uma checagem se o usuário daquele Sistema Operacional tem uma senha que eu vou definir em uma lista. Para ter um laboratório mais divertido eu troquei a senha do SO do Data Node para verificar a checagem e coloquei hadoop123


![6](https://github.com/pand-eX/Teste_Invas-o/blob/main/Teste%20De%20Penetra%C3%A7%C3%A3o%20no%20Cluster%20Hadoop/assets/6.png)


Agora iremos usar a Hydra para ver se temos senhas conhecidas. Talvez despois desse exercício você não utilize mais senhas simples. Primeiro você cria a senha de logins que você quer testar e cria a lista de senha que você quer testar e a lista de máquinas esses são os ips que a gente encontro quando fez o scan para verificar se encontra a conexão. Você pode buscar essas listas de senha na internet com as mais usadas se preferir.
E temos os serviços que suporta essa verificação.

![7](https://github.com/pand-eX/Teste_Invas-o/blob/main/Teste%20De%20Penetra%C3%A7%C3%A3o%20no%20Cluster%20Hadoop/assets/7.png)

Veja que ele permite testar o oracle-listener você pode testar inclusive senhas para um banco Oracle entre outros serviços disponíveis

![8](https://github.com/pand-eX/Teste_Invas-o/blob/main/Teste%20De%20Penetra%C3%A7%C3%A3o%20no%20Cluster%20Hadoop/assets/8.png)

E encontrou.... Hydra é fácil de compreender então use para aprender sobre segurança não para causar mal...
Essa são 2 atividades iniciais para o teste de segurança primeiro você checa qual máquinas estão ativas na rede do cluster Hadoop o ideal e ter uma rede isolada para as máquinas do cluster. Depois verificamos se os usuários tivessem senha fracas nada adianta fazer toda a parte da segurança se a senha for fraca.
Agora vamos avançar para próxima etapa verifica um teste de vulnerabilidade no Cluster Hadoop, mas não é um teste qualquer será um teste completo chamado openVAS com relatório e Dashboard.


![9](https://github.com/pand-eX/Teste_Invas-o/blob/main/Teste%20De%20Penetra%C3%A7%C3%A3o%20no%20Cluster%20Hadoop/assets/9.png)


Ambiente inicializado com Hadoop com Alta Disponibilidade e com segurança Kerberos. Temos 2 NameNodes e um Datanode.
O processo é simples atualizar e instalar o openvas na máquina.

![10](https://github.com/pand-eX/Teste_Invas-o/blob/main/Teste%20De%20Penetra%C3%A7%C3%A3o%20no%20Cluster%20Hadoop/assets/10.png)

Ele achou 2 vulnerabilidades. Isso mostra que nossa máquina está com nível de segurança bastante razoável. Ele encontrou o Kerberos é uma boa prática instalar o KDC em outra máquina caso o hacker soubesse dessa informação ele poderia pesquisar por falhas no protocolo e tentar explorar isso de alguma forma.
Repare que tem services um é o HDFS rodando na porta 9000 a ferramenta não identificou que é o HDFS mas detectou que provavelmente tenha algum serviço rodando nessa porta.

![11](https://github.com/pand-eX/Teste_Invas-o/blob/main/Teste%20De%20Penetra%C3%A7%C3%A3o%20no%20Cluster%20Hadoop/assets/11.png)

Aqui ele mostrou o risco mais baixo o seu efeito colateral e deu ainda uma proposta de solução com o comando completo para resolver é só ir no SO adicionar o parâmetro no arquivo aplicar o sysctl –p para não ter que reiniciar e pronto problema resolvido. É um exemplo simples, mas que mostra a importância de um teste de vulnerabilidade.
Aqui mostra como configuramos bem nosso Ambiente Hadoop com Segurança.
E para finalizar vamos tentar derrubar o Cluster com Ataque DDoS que nada mais é que você inundar uma porta ou endereço ip e o servidor fica indisponível.
Primeiro passa e descobrir qual porta nós vamos realizar o ataque DDoS

![12](https://github.com/pand-eX/Teste_Invas-o/blob/main/Teste%20De%20Penetra%C3%A7%C3%A3o%20no%20Cluster%20Hadoop/assets/12.png)

E ele encontra é claro que ele não vai falar explicitamente que é o HDFS, mas nós sabemos que o protocolo hadoop-ipc é o HDFS na porta 9000

![13](https://github.com/pand-eX/Teste_Invas-o/blob/main/Teste%20De%20Penetra%C3%A7%C3%A3o%20no%20Cluster%20Hadoop/assets/13.png)

Usarei uma ferramenta auxiliar o msfconsole. Coloquei o ip e a porta e está em execução, mas meu processador está fritando nesse momento. Se eu não desligar em breve pode entrar em pânico completo.

![14](https://github.com/pand-eX/Teste_Invas-o/blob/main/Teste%20De%20Penetra%C3%A7%C3%A3o%20no%20Cluster%20Hadoop/assets/14.png)

Só vai parar quando eu der um ctrl + z


já começa dar sinais de problemas é claro que não posso deixar pegar fogo porque meu processador já está gritando. Agora não tem mais o que fazer é claro que a gente está com alta disponibilidade então quando cair o namenode1 automaticamente o namenode2 que está em standby ficara ativo.
Um teste de vulnerabilidade precisa ser feito em tempos em tempos dependendo de como a empresa mantem a segurança dos servidores. Checar as portar que estão abertas, serviços que estão rodando, senha e etc...  

Precisamos verificar as vulnerabilidades nas máquinas nível médio, baixo e alto corrigir essas vulnerabilidades que forem encontradas e documentamos todo esse processo e fazemos isso periodicamente.

Muitas empresas só se preocupam com isso quando é violada ou muitas nem sabe que está sendo violadas e que os dados estão sendo roubados.
No caso do cluster hadoop veja que passamos por todo processo de segurança e praticamente não encontramos grande vulnerabilidade então precisamos fazer esses testes documentar é mostrar para o cliente ou para a empresa e recomendar que esse teste seja feito em tempo em tempos lembrando que não existe software 100% seguro no planeta. Portanto, ela pode acontecer o que temos que fazer é fechar as portas tanto quanto possível. 

Um Engenheiro de Dados não é responsável direto por testes de vulnerabilidades, mas nós podemos participar desse tipo de operação porque o responsável pela segurança talvez não sabe o que é um Hadoop ou não tem experiência então como engenheiro de dados podemos trabalhar em conjunto com a área de segurança.

FIM.

