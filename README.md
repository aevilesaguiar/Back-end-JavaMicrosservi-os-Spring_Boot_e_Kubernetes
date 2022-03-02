# Back-end Java: Microsserviços, Spring Boot e Kubernetes

Livro Casa do Código

## Capítulo 1: Introdução

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











## Referencias

 [lista](https://www.opus-software.com.br/micro-servicos-arquietura-monolitica/)
