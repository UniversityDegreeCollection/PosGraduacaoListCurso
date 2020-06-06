BANCOS DE DADOS PARA BIG DATA - HADOOP


## UNIDADE 3 | CAPÍTULO 2

## CONCEITOS DE BIG DATA COM HADOOP

Que o Big Data está surgindo como uma oportunidade para as organizações é incontestável e inevitável. O que as organizações precisam saber – e muitas delas já estão tirando proveito disso – são os muitos benefícios oferecidos pelo Big Data Analytics. Elas estão examinando grandes conjuntos de dados para descobrir todos os padrões ocultos, correlações desconhecidas, tendências de mercado, preferências do cliente e outras informações comerciais úteis.

Essas descobertas analíticas estão ajudando as organizações, por exemplo, em marketing mais eficaz, novas oportunidades de receita e melhor atendimento ao cliente. Eles estão melhorando a eficiência operacional, vantagens competitivas sobre organizações rivais e outros benefícios comerciais. Portanto, citaremos algumas dificuldades e problemas com diversas abordagens, para depois fundamentarmos soluções com o Big Data Hadoop.

Na abordagem tradicional, o principal problema era lidar com a heterogeneidade dos dados, isto é, estruturados, semiestruturados e não estruturados. Os RDBMS concentram-se principalmente em dados estruturados, como transações bancárias, dados operacionais etc. e o Hadoop é especializado em dados semiestruturados e não estruturados, como texto, vídeos, áudios, postagens no Facebook, registros etc. A tecnologia RDBMS é um sistema comprovado, altamente consistente e amadurecido suportado por muitas empresas. Por outro lado, o Hadoop está em demanda devido ao Big Data, que consiste principalmente de dados não estruturados em diferentes formatos.

Toda demanda parte de uma necessidade e, muitas vezes, essas trazem problemas a serem resolvidos. Particularmente no mundo Big Data não seria diferente, e serão listados alguns dos principais problemas enfrentados, em seguida, como resolvê-los utilizando Hadoop.

O primeiro e principal problema é a quantidade de dados que estão sendo gerados a cada segundo, o que não significa que deverão ser armazenados em um único local. Várias empresas captam e utilizam uma quantidade de dados inimagináveis. Por isso, armazenar esses dados nos meios tradicionais está impossível e os motivos são diversos, como banda de rede e armazenamento.

Não bastasse a quantidade dos dados, a qualidade e a heterogeneidade também devem apresentar muitos problemas. A qualidade deve ter um impacto um pouco menor, pois, atualmente, muitos tratamentos no front estão sendo feitos, justamente para que eles cheguem com uma certa tolerância e usabilidade. O problema maior está na diversidade dos dados que chegam.

Normalmente, os dados internos de uma empresa giram em torno dos usuários, trabalhando em um ERP, e-mails, pastas compartilhadas, redes sociais e aplicativos de mensagens. Imagine agora ter que fazer um trabalho de mineração de dados e reunir todos esses formatos de dados para que a informação faça sentido. Os dados são estruturados (base do ERP), semiestruturados (redes sociais) e não estruturados (pastas compartilhadas).

Quando é dito armazenamento, logo se imagina a facilidade em adquirir alguns HDs de Terabytes e colocar todos esses dados lá. Entretanto, os dados não bastam ser somente armazenados. Temos que lembrar que, na sequência, será feito um trabalho de mineração e valores serão extraídos. Se o resgate, as consultas ou buscas desses dados forem lentas, de nada adiantou armazená-los. A capacidade e a segurança do disco rígido estão aumentando, mas a velocidade de transferência e acesso não estão aumentando na mesma taxa de proporção.

Por exemplo, se um disco com uma taxa de transferência de 100 Mbps está processando 1 TB de dados, levará cerca de 2,91 horas para a conclusão. Se for aumentado o número de máquinas quatro vezes, por exemplo, para a mesma quantidade de dados, serão necessários aproximadamente 43 minutos. A tecnologia do disco também é um fator importante. Discos com tecnologia SSD também tendem a ser mais rápidos. Veja, por exemplo, a comparação de dois discos, instalados em PCs comuns:

Foi utilizado o hwinfo para obter as especificações:

Tabela 6. Informações sobre discos


|   |    |
|----|---|
|Hardware Class: disk|Hardware Class: disk|
|Model: "KINGSTON SA400S3"| Model: "VBOX HARDDISK"|
|Vendor: "KINGSTON"|Vendor: "VBOX"|
|Device: "SA400S3"| Device: "HARDDISK"|
|Device File: /dev/sda|Device File: /dev/sda|
|Size: 468862128 sectors a 512 bytes|Size: 20971520 sectors a 512 bytes|
|Capacity: 223 GB| Capacity: 10 GB|

Depois, para testes de leitura foi utilizado o hdparm:

Tabela 7. Teste de velocidade de leitura


|   |     |
|---|-----|
|**sudo hdparm -I /dev/sda | grep -i speed**|**sudo hdparm -I /dev/sda | grep -i speed**|
|Gen1 signaling speed (1.5Gb/s)|Gen2 signaling speed (3.0Gb/s)|
|Gen2 signaling speed (3.0Gb/s)||
|Gen3 signaling speed (6.0Gb/s)||


Fonte: O autor.

E, em seguida, um teste para gravação com dd.

Tabela 8. Teste de velocidade de gravação



|   |     |
|----|----|
|**sudo dd if=/dev/zero of=/tmp/output.img bs=8k count=10k; sudo rm -vf /tmp/output.img**|**sudo dd if=/dev/zero of=/tmp/output.img bs=8k count=10k; sudo rm -vf /tmp/output.img**|
|10240+0 registros de entrada|10240+0 registros de entrada|
|10240+0 registros de saída|10240+0 registros de saída|
|83886080 bytes (84 MB, 80 MiB) copiados, 0,0495489 s, 1,7 GB/s|83886080 bytes (84 MB, 80 MiB) copiados, 0,143656 s, 584 MB/s|
|removido '/tmp/output.img'|removido '/tmp/output.img'|

Fonte: O autor.

Outro componente da infraestrutura de um cluster Hadoop é a rede. Apesar do tráfego do Hadoop ser pequeno, ele pode congestionar redes lentas. Existem várias formas e aparelhos para testar o desempenho da rede, porém, se não dispor de nenhum desses produtos em mãos, o ping é um bom utilitário. Quando enviado pela rede com pacotes grandes, o tempo de resposta deverá ser muito menor que 1 milissegundo. O comando para esse teste é: 

```
$ ping –s 64512 IP_destino 
```


Portanto, a velocidade de acesso e processamento é o maior problema enfrentado pelo armazenamento de Big Data. Vejamos agora algumas possibilidades em que o Hadoop pode ajudar nesses problemas. Serão mencionados alguns componentes do Hadoop apenas para ilustrar os exemplos. Esses componentes serão detalhados nos próximos capítulos.

O problema sobre armazenamento poderá ser resolvido com o componente chamado HDFS, que fornece uma maneira distribuída de armazenar os dados em formato de blocos nos DataNodes, e quais poderão ser especificados o seu tamanho. Exemplo: os dados que forem armazenados chegaram ao HD para serem escritos e possuir 512 MB e se o HDFS estiver configurado de tal forma, ele criará 128 MB de blocos de dados. Portanto, o HDFS dividirá os dados em 4 blocos (512/128) e os armazenará em diferentes DataNodes, além de fazer sua replicação em blocos diferentes.

O problema de dimensionamento também será resolvido devido à escala. O Hadoop se concentra sua escalada na horizontal e não na vertical, e isso só é possível por poder adicionar nodes (nós) a qualquer momento no cluster HDFS, em vez de aumentar os recursos de seus DataNodes. Por exemplo, se a demanda de dados for de 1TB, não será preciso ter um HD de 1TB, podendo distribuir em vários de 128GB.

Outro problema a se resolver com HDFS é a variedade dos dados. Como o HDFS não faz validação de esquemas, é possível armazenar todos os tipos de dados, sejam eles estruturados, semiestruturados ou não estruturados. Outra vantagem é a forma com que grava e recupera os dados. Ele escreve uma vez e lê vários modelos, ou seja, é possível escrever os dados apenas uma vez e lê-los várias vezes para encontrar informações.

O desafio principal em qualquer implementação de Big Data foi a velocidade. É utilizada a seguinte lógica: o processamento é movido para os dados e não os dados para o processamento. Isso significa que, em vez de os dados serem movidos para o nó principal, para serem processados, o processamento é enviado para os nós escravos, os dados são processados paralelamente e o resultado é enviado de volta ao cliente. Isso é possível através do componente YARN.

Embora tenha sido visto que o Hadoop tem um conjunto maior de componentes e funcionalidades, utilizadas inclusive pelo Spark, o que a torna uma ferramenta robusta e poderosa, existem algumas desvantagens em sua implementação e utilização:

###  Baixa velocidade de processamento

No Hadoop, o algoritmo MapReduce, que é paralelo e distribuído, processa conjuntos de dados realmente grandes. Estas são as tarefas que precisam ser executadas aqui:

- Mapa: o mapa pega uma quantidade de dados como entrada e os converte em outro conjunto de dados, que novamente é dividido em pares chave / valor.

- Reduzir: a saída da tarefa “mapa” é inserida em “reduzir” como entrada. Na tarefa “reduzir”, como o nome sugere, esses pares de chave / valor são combinados em um conjunto menor de tuplas. A tarefa “reduzir” é sempre realizada após o mapeamento.

### Processamento em lote

O Hadoop implanta o processamento em lote, que coleta os dados e depois os processa em massa posteriormente. Embora o processamento em lote seja eficiente para processar grandes volumes de dados, ele não processa dados em fluxo. Por isso, o desempenho é menor.

### Sem pipelining de dados

O Hadoop não oferece suporte ao pipelining de dados (ou seja, uma sequência de estágios em que o ID de saída do estágio anterior é a entrada do próximo estágio).

### Não é fácil de usar

Os desenvolvedores do MapReduce precisam escrever seu próprio código para cada operação, o que dificulta muito o trabalho. E também, o MapReduce não tem modo interativo.

### Latência

No Hadoop, a estrutura do MapReduce é mais lenta, pois suporta diferentes formatos, estruturas e grandes volumes de dados.

### Linha de código longa

Como o Hadoop é escrito em Java, o código é longo. E isso leva mais tempo para executar o programa.

---


Em um artigo denominado “Top Advantages and Disadvantages of Hadoop 3 ”, Data Flair (2019), listou as principais vantagens e desvantagens que encontraram em utilização e implementações do Hadoop:

**Vantagens**


- **Fontes de dados variadas**: o Hadoop aceita uma variedade de dados.

- **Custo-benefício**: o Hadoop é uma solução econômica, pois usa um cluster de hardware comum para armazenar dados.

- **Desempenho**: o Hadoop, com seu processamento distribuído e arquitetura de armazenamento distribuído, processa grandes quantidades de dados com alta velocidade.

- **Tolerante a falhas**: no Hadoop 3.0, a tolerância a falhas é fornecida pela codificação de apagamento.

- **Altamente disponível**: no Hadoop 2.x, a arquitetura HDFS tem um único NameNode ativo e um único NameNode em espera.

- **Baixo tráfego de rede**: no Hadoop, cada tarefa enviada pelo usuário é dividida em várias subtarefas.

- **Alto rendimento**: Hadoop armazena dados de maneira distribuída, o que permite usar o processamento distribuído com facilidade.

- **Código aberto**: podemos modificar o código fonte para atender a um requisito específico.

- **Escalável**: o Hadoop trabalha com o princípio da escalabilidade horizontal, nós podem ser adicionados ao cluster do Hadoop rapidamente, tornando-o uma estrutura escalável.

- **Facilidade de uso**: a estrutura do Hadoop cuida do processamento paralelo, os programadores do MapReduce não precisam cuidar do alcance do processamento distribuído, isso é feito automaticamente no back-end.

- **Compatibilidade**: a maior parte da tecnologia emergente do Big Data é compatível com o Hadoop como Spark, Flink etc.

- **Várias linguagens de programação suportadas**: os desenvolvedores podem codificar usando muitas linguagens no Hadoop, como C, C ++, Perl, Python.



**Desvantagens do Hadoop**


###  Problema com arquivos pequenos:

O Hadoop é adequado para um pequeno número de arquivos grandes, mas quando se trata do aplicativo que lida com um grande número de arquivos pequenos, o Hadoop falha aqui.

### Vulnerável por natureza:

O Hadoop é escrito em Java, que é uma linguagem de programação amplamente usada; portanto, é facilmente explorado por cibercriminosos.



###  Processamento de custos indiretos:

No Hadoop, os dados são lidos e gravados no disco, o que torna as operações de leitura / gravação muito caras quando lidamos com tera e petabytes de dados. O Hadoop não pode fazer cálculos na memória, portanto, incorre em sobrecarga de processamento.



### Suporta apenas processamento em lote:

No núcleo, o Hadoop possui um mecanismo de processamento em lote que não é eficiente no processamento de fluxo.

### Processamento Iterativo:

O Hadoop não pode executar o processamento iterativo por si só.


###  Segurança:

Por segurança, o Hadoop usa a autenticação Kerberos, que é difícil de gerenciar. Falta criptografia nos níveis de armazenamento e rede, o que é um grande ponto de preocupação.












