BANCOS DE DADOS PARA BIG DATA - HADOOP

## UNIDADE 3 | CAPÍTULO 3


## ARQUITETURA PRINCIPAL DO

Hadoop Distributed File System

O Hadoop Distributed File System é um sistema de arquivos distribuído que permite o armazenamento de grande volume de dados de maneira tolerante a falhas. Sistemas de arquivos são estruturas lógicas que os sistemas operacionais, como o Linux, utilizam para gerenciar os arquivos. Quanto mais os dados vão aumentando, mais complexo fica o gerenciamento dos arquivos pelos servidores. O gerenciamento de arquivos pelo sistema operacional inclui desde manipulação, como gravação e leitura, até controle de nível de acesso e segurança. Entretanto, esse gerenciamento só poderá ser efetuado em uma única máquina. Já o HDFS também efetua todo esse gerenciamento, porém em um sistema distribuído de computação, se comportando como se fosse uma única máquina em um sistema de cluster.

Existem três componentes principais do Hadoop HDFS:


### DataNodes

O HDFS armazena os dados reais e de maneira distribuída nos DataNodes, dividindo os variados tipos de arquivos de entrada em vários blocos.

A lógica do DataNode é a seguinte:

- Quando inicializa, o DataNode faz uma validação com o nó principal, chamado NameNode.
- Ele verifica o ID do espaço de alocação e a versão do software do DataNode.
- Também, envia uma lista com as características de bloco para o NameNode a cada três segundos, informando que está ativo.

### NameNode

NameNode é o daemon principal que mantém e gerencia os DataNodes. No caso de falha do DataNode, o NameNode escolhe novos DataNodes para novas réplicas, equilibra o uso do disco e gerencia o tráfego de comunicação para os DataNodes. Ele é responsável por gerenciar o espaço de nome do sistema de arquivos, controlar tarefas de manipulação de arquivos e diretórios, como: abrir, fechar, nomear e renomear, anexar dados ao arquivo, controlar o nível de acesso dos usuários, como permissão de arquivo, cota de disco, registro de data e hora da modificação, horário de acesso e os logs, grava alterações incrementais, como renomear o arquivo. Essas informações ficam contidas em um arquivo chamado FSImage. Todas as modificações feitas no FSImage são armazenadas em um arquivo chamado EditLogs.

### Secondary NameNode

O Secondary NameNode pode ser pensado como um assistente do NameNode que leva parte da carga de trabalho do NameNode. Caso o NameNode não seja reiniciado de tempos em tempos, o tamanho de seu log aumenta e atrasa a reinicialização do cluster. O papel do Secundary NameNode aplica atualizações no FSImage em intervalos e atualiza o novo FSImage no NameNode primário.


## Hadoop MapReduce

O objetivo do HDFS é fazer a gestão dos enormes volumes de dados em um sistema distribuídos de armazenamento, ou seja, em vários clusters de computadores. Uma vez armazenados, esses dados precisam ser processados, ou seja, deverão ser extraídos para um conjunto de informações com alguma utilidade. Para isso, foi criado outro componente: o MapReduce.

MapReduce é um conceito de redução e otimização dos dados, já armazenados, existentes antes do Hadoop, que foi incluído pela equipe de desenvolvimento para dentro do framework. MapReduce é o componente de processamento de dados do Hadoop. Aplica a computação em conjuntos de dados em paralelo, melhorando, assim, o desempenho. A estrutura MapReduce opera exclusivamente em pares, ou seja, a estrutura exibe a entrada para o trabalho como um conjunto de pares e produz um conjunto de pares como a saída do trabalho, possivelmente de diferentes tipos.

Ele funciona em duas fases:

- Map – como o nome sugere, ele faz apenas o mapeamento, ou seja, recebe a entrada como pares de valores-chave e produz saída como pares de valores-chave, processa os dados e manda para a fase de redução.

- Reduce – classifica o par de valores-chave e aplica o tipo de resumo dos cálculos aos pares de valores-chave, reduzindo o seu conteúdo.

A lógica é a seguinte:

- Um mecanismo chamado Mapper lê o bloco de dados e o converte em pares de valores-chave.
- Os pares de chave entram no redutor.
- O redutor recebe tuplas de dados de vários Mappers.
- O redutor aplica agregação a essas tuplas com base na chave.
- A saída final do redutor é gravada no HDFS.

O MapReduce ainda cuida de possíveis falhas e recuperação dos dados nos nós. Sua documentação oficial.

## Hadoop YARN

É através do YARN (Yet Another Resource Manager) que o Hadoop monitora e gerencia os recursos. Ele lida com as cargas de trabalho como processamento de fluxo, processamento interativo e processamento em lote em uma única plataforma e tem dois componentes principais: ResourceManager e o NodeManager. Juntos, eles formam a estrutura de computação de dados, na qual o ResourceManager é quem gerencia todos os recursos dos aplicativos no sistema e o NodeManager é o agente responsável pelos contêineres, monitorando o uso de recursos (CPU, memória, disco, rede) e relatando o mesmo ao Scheduler do ResourceManager.

Segundo a documentação do Hadoop YARN: “a ideia fundamental do YARN é dividir as funcionalidades de gerenciamento de recursos e agendamento / monitoramento de tarefas em daemons separados. A ideia é ter um ResourceManager global e um ApplicationMaster por aplicativo”. O ApplicationMaster por aplicativo é, na verdade, uma biblioteca específica da estrutura e recebe a tarefa de negociar recursos do ResourceManager e trabalhar com o NodeManager para executar e monitorar as tarefas. O ResourceManager possui dois componentes principais: o Scheduler e ApplicationsManager.

Scheduler é responsável pela alocação de recursos para os vários aplicativos em execução, capaz de gerenciar filas, não executa nenhum monitoramento e agenda tarefas baseado em requisitos de recursos de aplicativos. Ele ainda possui plug-ins que são desenvolvidos conforme a ferramenta vai evoluindo, podendo citar o CapacityScheduler e o FairScheduler.

ApplicationsManager é responsável por aceitar os envios de tarefas, negociando o primeiro contêiner para executar o ApplicationMaster específico do aplicativo e fornece o serviço para reiniciar o contêiner ApplicationMaster em caso de falha. O ApplicationMaster por aplicativo tem a responsabilidade de negociar contêineres de recursos apropriados do Scheduler, rastreando seu status e monitorando o progresso.





