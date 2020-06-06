BANCOS DE DADOS PARA BIG DATA - HADOOP

## UNIDADE 3 | CAPÍTULO 1

# INTRODUÇÃO
O projeto Hadoop é um framework, ou seja, um conjunto de softwares para computação confiável, escalável e distribuída. Ele possui uma estrutura projetada para processar um grande volume de dados de forma distribuída e projetado escalonar de um simples servidor individual a milhares de máquinas. Sua utilização também ganha muitos adeptos devido ao grande número de bibliotecas e software de terceiros, que realizam tarefas essenciais para o trabalho dos cientistas de dados, além, inclusive, possuir mecanismos que detectam e recuperam falhas.

### História do Hadoop

O Hadoop foi criado pelos cientistas da computação Doug Cuttinge Mike Cafarella, inicialmente para dar suporte ao processamento no mecanismo de pesquisa de código aberto Apache Nutch (<https://nutch.apache.org/>) e no rastreador da Web. Depois que o Google publicou documentos técnicos detalhando sua estrutura de programação do Google File System e do MapReduce em 2003 e 2004, Cutting e Cafarella modificaram os planos tecnológicos anteriores e desenvolveram uma implementação MapReduce baseada em Java e um sistema de arquivos modelado no Google. Ao mesmo tempo, Cutting foi contratado pela empresa de serviços de Internet Yahoo, que se tornou o primeiro usuário de produção do Hadoop no final de 2006.

O filho de Doug Cutting nomeou um de seus brinquedos de Hadoop, um elefante amarelo. Doug então usou o nome para seu projeto de código aberto, porque era fácil soletrar, pronunciar e não ser usado em outros lugares.

O uso da estrutura cresceu nos próximos anos e foram criados três fornecedores independentes do Hadoop:

- Cloudera, em 2008 (<https://www.cloudera.com/products/open-source/apache-hadoop.html>).

- MapR Technologies, um ano depois (<https://mapr.com/>).

- AWS lançou um serviço de nuvem Hadoop chamado Elastic MapReduce, em 2009 (<https://aws.amazon.com/pt/emr/>).

Isso aconteceu antes de a Apache Foundation lançar sua primeira versão do Hadoop, disponibilizada em dezembro de 2011.

A natureza flexível de um sistema Hadoop significa que as empresas podem adicionar ou modificar funcionalidades conforme suas necessidades. Tanto uma grande corporação quanto apenas uma pessoa física são livres para alterá-lo para seus próprios propósitos. As modificações feitas no software por engenheiros especialistas, por exemplo, Amazon e Google, são retornadas à comunidade de desenvolvimento, onde são frequentemente usados para melhorar o produto "oficial". Essa forma de desenvolvimento colaborativo entre usuários voluntários e comerciais é uma característica essencial do software de código aberto, ou Open Source. 

Ele é mantido pela Apache Foudation e, como a maioria dos projetos da organização, é composto de vários módulos e projetos, que inclui:


>Hadoop Common: os utilitários comuns que oferecem suporte aos outros módulos do Hadoop.
>Hadoop Distributed File System (HDFS): um sistema de arquivos distribuídos que fornece acesso de alta taxa de transferência aos dados do aplicativo.
>Hadoop YARN: uma estrutura para agendamento de tarefas e gerenciamento de recursos de cluster.
>Hadoop MapReduce: um sistema baseado em YARN para processamento paralelo de grandes conjuntos de dados.


Algumas considerações devem ser levadas antes de escolher um banco de dados para um projeto de Big Data. Embora esse material aborde alguns, existem vários outros e cada um para um determinado tipo de aplicação e, muitas vezes, trabalhando juntos. Aqui abordamos o Hadoop e o MongoDB e suas particularidades. A seguir, foi elaborada uma lista com as principais diferenças entre os dois e cabe ao projetista avaliar a relevância sob o projeto:

**Linguagem de programação**

- O Hadoop em Programação Java.
- MongoDB C ++.

**Código aberto**

- Tanto o Hadoop quanto o MongoDB são de código aberto.

**Escalabilidade**

- Tanto o Hadoop quanto o MongoDB são escaláveis.


**NoSQL**

- O Hadoop não suporta NoSQL nativamente, apenas através de um outro software chamado HBase.

- O MongoDB suporta NoSQL.


**Dados Estruturados**

- O Hadoop possui uma estrutura de dados flexível.
- O MongoDB suporta a estrutura de dados baseada em documentos.

**Custo**

- Hadoop precisa implementar um ecossistema mais complexo.
- O MongoDB é um único software, portanto, mais econômico.

**Volumes de Dados

- O Hadoop pode lidar com grandes volumes de dados.
- O MongoDB pode lidar com o tamanho moderado de dados, menos que o Hadoop.

**Formato de dados geoespacial**

- O Hadoop não pode lidar com dados geoespaciais com eficiência.
- O MongoDB pode analisar dados geoespaciais com sua capacidade de indexação.









