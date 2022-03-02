# Back-end Java: Microsserviços, Spring Boot e Kubernetes

Livro Casa do Código

## Capítulo 1: Introdução

Até alguns anos atrás, a grande maioria dos sistemas web era desenvolvida em uma arquitetura monolítica, isto é, tudo ficava em apenas um projeto,
incluindo o back-end e o front-end. Alguns frameworks como o Struts e o JavaServer Faces inclusive disponibilizam diversas bibliotecas para a
criação de interfaces ricas, o Prime Faces e o Rich Faces. Esse modelo tinha uma série de problemas, como alto acoplamento do front-end e do back-end
da aplicação, projetos enormes com milhares de arquivos (HTMLs, JavaScript, CSS, scripts de banco de dados, Java) e diversas cópias do
mesmo código em várias aplicações.



## Como funciona a arquitetura monolítica 


As principais linguagens de desenvolvimento de aplicações oferecem abstrações para quebrar a complexidade dos sistemas em módulos. 
Entretanto, são projetadas para a criação de um único executável monolítico, no qual toda a modularização utilizada é executada em uma mesma máquina. Assim, 
os módulos compartilham recursos de processamento, memória, bancos de dados e arquivos.

Uma arquitetura monolítica típica de um sistema complexo pode ser representada pela figura abaixo, na qual todas as funções do negócio estão implementadas em um único processo. 

![image](https://user-images.githubusercontent.com/52088444/156379462-93414204-9267-4d68-823b-e074a01e8d0c.png)

## Desafios da arquitetura monolítica   

Ao longo do tempo o sistema vai crescendo, se tornando mais complexo e consumindo cada vez mais recursos, o que acaba gerando também alguns desafios substanciais
para a manutenção desse tipo de arquitetura. São eles:  

**Aumento da complexidade e tamanho ao longo do tempo** 
O sistema se torna tão complexo que a manutenção fica cada vez mais cara e lenta, porque os desenvolvedores têm que navegar em uma infinidade de códigos. 

**Alta dependência de componentes de código**
Muitas funções são interdependentes e entrelaçadas, de forma que a inclusão ou manutenção de componentes do sistema pode causar inconsistências ou comportamentos inesperados. 

**Escalabilidade do sistema é limitada**
Mesmo que apenas parte da funcionalidade seja necessária na nova instância, uma arquitetura monolítica exige que todo o sistema seja replicado, o que gera custos maiores do que o esperado.  

**Falta de flexibilidade**
Exige que os desenvolvedores fiquem amarrados à tecnologia originalmente escolhida para o sistema, mesmo que em algumas situações ela não seja a melhor escolha. 

**Dificuldade para colocar alterações em produção**
Qualquer mudança, por menor que seja, requer a reinicialização do sistema. Como isso pode causar algum risco operacional, é necessário que as equipes de desenvolvimento, testes e manutenção desses sistema acompanhem essas alterações.  

## Como funciona a arquitetura de micro serviços 

A arquitetura de micro serviços é utilizada para desenvolver uma aplicação como um conjunto de pequenos serviços, que funcionam com seu próprio processo. Cada serviço é desenvolvido em torno de um conjunto de regras de negócio específicas, e é implementado de forma independente. 

Com isso, é possível quebrar algumas barreiras existentes no modelo de arquitetura monolítica.

**Benefícios dos micro serviços**

- Manutenção e evolução dos serviços mais estáveis: Como os desenvolvedores vão trabalhar com códigos que executam uma única função, os serviços individuais 
não vão acompanhar o potencial crescimento do sistema, evitando que você precise carregar uma parte desnecessária da aplicação.  

- Serviços com baixo nível de acoplamento e interdependência: A manutenção em um serviço específico não interfere diretamente nas outras funcionalidades do sistema. 

- Escalabilidade do sistema: Os deploys e replicações de micro serviços são feitos por meio de infraestruturas de servidores, máquinas virtuais
 e containers que se organizam de forma independente. Isso torna o crescimento e a possibilidade de adaptação do sistema muito mais flexível. 
 
 - Redução de custos: Cada aplicação só utiliza os serviços que necessita. Por isso, você não vai ter gastos extras carregando funcionalidades não utilizadas, afinal os custos estão diretamente associados à funcionalidade e à carga de uso do sistema.  
 - Flexibilidade de tecnologia: Por conta do baixo acoplamento entre os serviços, não é necessário amarrar os desenvolvedores a uma tecnologia específica, o que te permite escolher a melhor opção para atender cada caso.   Isso diminui os riscos de obsolescência tecnológica e possibilita a evolução constante do sistema.  
 - Facilidade de colocar alterações em produção: As mudanças no sistema são executadas por meio de alterações e evoluções feitas nos serviços. Portanto, o sistema como um todo não precisa ser reinicializado para continuar funcionando.  Assim, o time de desenvolvimento que vai precisar acompanhar a mudança será apenas o de responsáveis pelos serviços que estão sendo alterados. 



Atualmente, a maioria dos sistemas está sendo desenvolvida utilizando APIs e a arquiteturas de microsserviços, que busca resolver exatamente os
problemas mencionados anteriormente. Com as APIs, o back-end é totalmente isolado do front-end e, com os microsserviços, os projetos são
muito menores, não passando de algumas dezenas ou centenas de arquivos. Além disso, evita-se a duplicação de código já que cada serviço implementa
uma funcionalidade específica e pode ser reutilizado por diversas aplicações.


O Java continua sendo a linguagem mais utilizada para o desenvolvimento de aplicações back-end. Isso se deve ao grande grau de maturidade da
linguagem e da sua máquina virtual. Existem diversas formas de desenvolver microsserviços em Java, como utilizar bibliotecas nativas ou o
framework Spring. Aqui utilizaremos Spring Boot, Spring Data e o Spring Cloud.


Obviamente, essa arquitetura também possui algumas desvantagens, como maior complexidade das aplicações e a latência para a comunicação entre os
serviços. Testar as aplicações é uma tarefa mais complexa porque um microsserviço pode depender de vários outros. Um microsserviço de
compras pode depender dos dados sobre o cliente e sobre os produtos, por exemplo. É possível testar os serviços localmente, mas, para isso, a pessoa
desenvolvedora deve executar localmente todos os serviços.

Uma maneira mais simples de testar as aplicações é criar um cluster local utilizando o Kubernetes, já que o cluster pode ficar executando em
background e apenas o microsserviço alterado necessita ser atualizado. Além de facilitar os testes, utilizar o Kubernetes no ambiente de
desenvolvimento aumenta a confiabilidade da aplicação, já que o ambiente do programador é muito mais próximo dos ambientes de homologação e
produção.

Para explicar todos esses conceitos, este livro começa apresentando o framework Spring e desenvolvendo um exemplo de uma aplicação com três
microsserviços. A aplicação consiste em um serviço para cadastro de cliente, um para cadastro de produtos e um para compras. Para a execução
das compras, os clientes e os produtos devem ser validados, o que requer a comunicação entre os serviços. Depois que a aplicação estiver pronta, será
mostrado como criar um cluster no ambiente de desenvolvimento utilizando o Kubernetes.


## 1.1 Framework Spring

O Spring é um framework Java que possui uma grande quantidade de projetos, como o Spring Boot, o Spring Data e o Spring Cloud, que podem
ser utilizados em conjunto ou não. É também possível utilizar outros frameworks com o Spring e até mesmo as bibliotecas do Enterprise Java
Beans (EJB).
Spring Framework é um framework desenvolvido para a plataforma Java baseado nos padrões de projetos (Design Patterns), inversão de controle e 
injeção de dependência. É constituído por diversos e completos módulos capazes de dar um boost na aplicação Java.

**Inversão de Controle**: Inversão de controle (Inversion of Control ou IoC, em inglês) trata-se da interrupção do fluxo de execução de um código 
retirando, de certa forma, o controle sobre ele e delegando-o para uma dependência ou container. O principal propósito é minificar o acoplamento do código.No Java, 
falamos mesmo em desacoplamento das classes. Isso permite um ganho enorme em manutenibilidade, além da facilidade de trocar ou acrescentar comportamentos ao 
sistema, se necessário. Também diminui a possibilidade de ocorrência bugs em cascata.
No Spring Framework, as instâncias das classes são fracamente acopladas, ou seja, a interdependência entre os objetos é mínima.A inversão de controle, 
no Spring, é facilitada por outro Design Pattern: Injeção de Dependência.

**Injeção de Dependência**: A injeção de dependência tem o propósito de evitar o acoplamento de código numa aplicação. Em outras palavras, é a proveniência 
de instâncias de classes que um objeto precisa sem que este instancie por si mesmo. Podemos dizer que a injeção de dependência é uma forma de aplicar a 
inversão de controle.

## Spring Boot

O Spring Boot é uma forma de criar aplicações baseadas no framework Spring de forma simples e rápida. Nelas, já existe um contêiner Web, que
pode ser o Tomcat ou o Jetty, e a aplicação é executada com apenas um run, diferentemente de quando é necessário primeiro instalar e configurar um
contêiner, gerar um arquivo WAR (Web Application Resource) e por fim implantá-lo no contêiner. O Spring Boot também facilita a configuração das
aplicações através de arquivos properties ou diretamente no código, não sendo necessário o uso de arquivos XML. Há também uma grande
quantidade de bibliotecas especialmente criadas para ele, como para acesso a dados em banco de dados relacionais e NoSQL, para geração de métricas
sobre a aplicação, acesso a serviços e muito mais.

## Spring Data

O Spring Data é um projeto do Spring para facilitar a criação da camada de persistência de dados. Esse projeto tem abstrações para diferentes modelos
de dados, como banco de dados relacionais e não relacionais como o MongoDB e o Redis.
Relacionado a banco de dados relacionais, o Spring Data possibilita o acesso aos dados utilizando interfaces e definindo apenas o nome de um
método. O framework, com isso, implementa todo o acesso ao banco de dados automaticamente. Por exemplo, a classe na listagem a seguir define
três métodos que serão traduzidos para consultas em um banco de dados relacional:

List<Pessoa> findByName(String name);
List<Pessoa> findByAge(int age);
Pessoa findByCpf(String cpf);
 
 Nesse exemplo, para uma classe Pessoa , o Spring Data automaticamente gera um método que fará a busca, no primeiro caso pelo nome, no segundo,
pela idade e no terceiro, pelo CPF. Obviamente, existe uma sintaxe correta para que o Spring Boot consiga gerar os métodos.
 
## Spring Cloud

 O Spring Cloud é um projeto que disponibiliza diversas funcionalidades para a construção de sistemas distribuídos, como gerenciamento de
configuração, serviços de descoberta, proxys, eleição de líderes etc. É bastante simples usá-lo junto a projetos Spring Boot.
 
Neste livro, vamos usá-lo para a gerência de configuração das aplicações.Nele serão centralizadas todas as configurações da aplicação, como nomes
dos microsserviços e endereços de banco de dados. Isso evita problemas no caso de haver alterações. Por exemplo, imagine um projeto com mais de 20
microsserviços, e que se deve mudar a porta do banco de dados em todos eles. Se a configuração é feita diretamente em cada serviço, o trabalho para
mudar essa configuração será enorme. Com o Spring Cloud, essa mudança é feita em apenas um lugar, e todas as aplicações serão atualizadas.
 
## Kubernetes

 O Kubernetes, ou k8s, é uma ferramenta para facilitar a execução e a operação de contêineres inicialmente desenvolvida por engenheiros do
Google, mas hoje aberta para ser utilizada em diversas plataformas. Nela, é possível definir diversas opções para a implantação, execução e
disponibilização dos contêineres de forma fácil e, em muitos casos, automática.
 
 Atualmente, o k8s é uma das principais ferramentas de DevOps, pois é utilizada normalmente em ambientes de produção e homologação das
aplicações. Porém, também é possível a criação de um cluster local em uma máquina de desenvolvimento, o que facilita bastante os testes locais de uma
aplicação e também aumenta a confiabilidade de um novodesenvolvimento, já que o ambiente de programação é muito mais próximo
do ambiente de produção.

A estrutura básica dessa ferramenta é criar definições para os contêineres que serão executados, com algumas configurações básicas como número de
CPUs e quantidade de memória necessária para executar esse contêiner. A partir deles, é possível criar máquinas virtuais (chamadas Pods) que os
executam. Assim, o k8s disponibiliza diversas funcionalidades para facilitar e otimizar a execução dos Pods, como aproveitar melhor o hardware da
máquina alocando e desalocando recursos automaticamente, monitorar aplicações, escalar rapidamente e automaticamente serviços de acordo com
o uso de hardware e garantir a autorrecuperação das aplicações de forma rápida e simples
 
## Referencias

 [Arquitetura Monolítica e Microsserviços](https://www.opus-software.com.br/micro-servicos-arquietura-monolitica/)
