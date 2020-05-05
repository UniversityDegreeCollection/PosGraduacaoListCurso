## CLUSTER E PROGRAMAÇÃO PARALELA

Cluster é um conjunto de computadores conectados, trabalhando como um único recurso de computação que pode criar a ilusão de ser uma máquina. Seus componentes geralmente são conectados usando redes de alta velocidade, com cada nó executando sua própria instância de um sistema operacional. Na maioria das configurações, todos os nós usam o mesmo hardware e o mesmo sistema operacional, embora em algumas configurações um hardware ou sistema operacional diferente possa ser usado. Seus nós podem ser configurados para executar a mesma tarefa, controlada e produzida por software.

Segundo Tanenbaum (2007, p. 10), cada cluster consiste em um conjunto de nós de computação controlados e acessados por um único mestre e uma de funções é manipular a alocação de nós a um determinado programa paralelo, manter uma fila de jobs apresentados e proporcionar uma interface aos usuários do sistema.

Definindo, portanto, cluster é um termo amplamente usado que pode significar uma série de computadores independentes combinados em um conjunto unificado de hardware, software e rede. Mesmo quando dois ou mais computadores são utilizados juntos no intuito de resolverem um problema, isso já é considerado um cluster.

A técnica de organizar os computadores em cluster dá suporte a diversas finalidades, como suporte de serviço na Web cálculos científicos, elaboração de chave para criptomoedas etc.

Como foi detalhado na disciplina Arquitetura Orientada a Serviços, os clusters podem ser utilizados para duas principais funções, Alta Disponibilidade (HA – High Availability) ou Alta Performance (HPC – High Performance Computing), com a finalidade de fornecer um poder computacional maior do que aquele fornecido por um simples computador.

Alguns autores dividem os clusters em classes:

---

####  Classe 1

Os clusters de Classe 1 são construídos utilizando, em sua maioria, tecnologias e peças padrão de mercado ou de fácil acesso, como interfaces de Discos SCSI, SSD, serial e placas de rede Gigabit Ethernet. O que torna seu preço mais viável que o de Classe 2.

#### Classe 2

O que diferencia os clusters de Classe 2 são os hardwares utilizados em sua construção. Nele são utilizados equipamentos Blade, processadores de alta performance, normalmente menos acessíveis aos entusiastas e empresas de pequeno porte.

---

### Aplicações e benefícios

Os benefícios que os clusters proporcionam são inúmeros. Por exemplo, sabendo que cada nó da rede do cluster é independente, a falha de um deles não significa perda de serviço.

>Um único nó é um computador independente e esse nó pode ser desativado para manutenção, enquanto o restante dos clusters assume a carga desse nó individual. Normalmente, são projetados para melhorar o desempenho e a disponibilidade dos seus serviços, além de serem muito mais econômicos do que computadores individuais com velocidade ou disponibilidade comparáveis. “A tolerância a falhas é muito utilizada em servidores web ou servidores de banco de dados em Intranets. (MORIMOTO, 2003)

Outro exemplo seria o balanceamento de carga, também poderá ser utilizado em servidores web, onde sua arquitetura é composta por pelo menos três computadores, em que um é o mestre e se encarrega de distribuir as tarefas. Esse metre não precisa, necessariamente, ser um computador com grande capacidade, o que torna essa arquitetura viável economicamente.

Para processamento paralelo existe uma tecnologia interessante chamada Beowulf. Segundo Geist et al. (1994):

>os clusters Beowulf são clusters de desempenho escalonáveis baseados em hardware comum, em uma rede de sistema privada, com infraestrutura de software de código aberto (Linux). Ele consiste em um cluster de PCs comuns ou estações de trabalho dedicadas à execução de tarefas de computação de alto processamento. A visualização dos nós no cluster não ficam acessíveis para os usuários, ou seja, sua única função é se dedicar à execução de trabalhos de cluster, normalmente, seu painel de configuração é exposto ao mundo externo através de apenas um nó. Alguns clusters do Linux são criados para oferecer confiabilidade e não velocidade.

Não existe um software, um pacoteou uma instalação ou um sistema operacional chamado "Beowulf". No entanto, existem vários softwares considerados úteis para a construção de Beowulfs que incluem os pacotes PVM e MPI, o kernel Linux etc.

O princípio de funcionamento de um cluster Beowulf é bastante simples: o servidor mestre, definido como front-end, coordena o escalonamento das tarefas entre os clientes, back-end, auxiliado pelas bibliotecas de troca de mensagens, como a MPI11 e PVM12 instaladas nos clientes e no servidor mestre. São as bibliotecas PVM e MPI que definem a arquitetura como sendo computação paralela.

### PVM - Parallel Virtual Machine 

O PVM é um conjunto integrado de ferramentas e bibliotecas de software que emula uma estrutura de computação paralela, de uso geral, flexível e heterogênea em computadores interconectados de diversas arquiteturas. O objetivo do sistema PVM é permitir que esse agrupamento de computadores interconectados seja usada cooperativamente para computação simultânea ou paralela. Segundo Geist et al. (1994), algumas de suas funcionalidades são, basicamente:

---

####  Pool de hosts configurado pelo usuário:

As tarefas computacionais do aplicativo são executadas em um conjunto de máquinas que são selecionadas pelo usuário para uma determinada execução do programa PVM. Máquinas de CPU única e multiprocessadores de hardware, incluindo computadores de memória compartilhada e de memória distribuída, podem fazer parte do pool de hosts. Após devidamente configurado, o pool de hosts pode ser alterado adicionando e excluindo máquinas durante a operação. Esse recurso é muito utilizado em projetos failover, ou seja, tolerância a falhas.

#### Acesso translúcido ao hardware:

Os programas aplicativos podem exibir o ambiente de hardware como uma coleção sem atributos, de elementos, de processamento virtual ou podem optar por explorar os recursos de máquinas específicas no pool de hosts, posicionando determinadas tarefas computacionais nos computadores mais apropriados.


#### Computação baseada em processos:

Em particular, várias tarefas podem ser executadas em um único processador, ou seja, a unidade de paralelismo no PVM é uma tarefa um encadeamento sequencial independente de controle que alterna entre comunicação e computação. Nenhum mapeamento de processo para processador é implícito ou imposto pelo PVM.

#### Modelo explícito de transmissão de mensagens:

Coleções de tarefas computacionais, cada uma executando uma parte da carga de trabalho de um aplicativo usando decomposição de dados, funcional ou híbrida, cooperam enviando e recebendo mensagens explicitamente. O tamanho da mensagem é limitado apenas pela quantidade de memória disponível.


#### Suporte à heterogeneidade:

O sistema PVM suporta a heterogeneidade em termos de máquinas, redes e aplicativos. No que diz respeito à passagem de mensagens, o PVM permite que mensagens contendo mais de um tipo de dados sejam trocadas entre máquinas com diferentes representações de dados.


####  Suporte ao multiprocessador:

O PVM usa os recursos nativos de passagem de mensagens nos multiprocessadores para aproveitar o hardware subjacente. Os fornecedores geralmente fornecem seu próprio PVM otimizado para seus sistemas, que ainda podem se comunicar com a versão pública do PVM.


---


O sistema PVM é composto de duas partes:

A primeira parte é o daemon executado em segundo plano, instalando e rodando em todos os computadores que compõem a máquina virtual, projetado para que qualquer usuário autorizado possa instalá-lo em uma máquina e, quando for executado, através de um prompt, ele cria uma máquina virtual iniciando o PVM. Um exemplo de programa daemon é o programa de correio que é executado em segundo plano e lida com todo o correio eletrônico de entrada e saída em um computador. Vários usuários podem configurar máquinas virtuais sobrepostas e cada usuário pode executar vários aplicativos PVM simultaneamente.

A segunda parte do sistema é uma biblioteca de rotinas de interface PVM, que contém um repertório funcional e completo de primitivas necessárias para a cooperação entre as tarefas de um aplicativo. Essa biblioteca contém rotinas que podem ser chamadas pelo usuário para passagem de mensagens, processos de geração, coordenação de tarefas e modificação da máquina virtual.

O modelo de computação PVM é baseado em Threads. Quando se programa em threads é possível que um aplicativo execute várias tarefas e, cada uma dessas tarefas, é responsável por uma parte da carga de trabalho computacional do aplicativo. Aplicando paralelismo, cada tarefa executa uma função diferente, por exemplo, entrada, configuração do problema, solução, saída e exibição. Esse processo costuma ser chamado de paralelismo funcional. Um método mais comum de paralelizar um aplicativo é chamado paralelismo de dados. Dependendo de suas funções, as tarefas podem ser executadas em paralelo e podem precisar sincronizar ou trocar dados.

As linguagens de programação que o PVM suporta são C, C++ e Fortran, pois seguiu a convenção de que a maioria dos aplicativos são escritos nessas linguagens, porém com uma tendência emergente na experimentação de linguagens e metodologias baseadas em objetos.

As tarefas seguem o padrão do sistema operacional, no caso, o Linux. Elas são identificadas como um TID (task identifier), das quais são utilizados para o reconhecimento no envio de mensagens. Por serem únicas nas máquinas virtuais do cluster, elas são sustentadas pelo daemon do nó local (pvmd) e não podem ser configuradas pelo usuário. O PVM contém várias rotinas que retornam um valor tid e, assim, a aplicação do usuário pode identificar outras tarefas no sistema.

Veja o código fonte e a explicação de um programa escrito em C, disponível em

```c
<http://www.netlib.org/pvm3/book/node17.html>. 

 

main()

{

int cc, tid, msgtag;

char buf[100];

printf("i'm t%x\n", pvm_mytid());

cc = pvm_spawn("hello_other", (char**)0, 0, "", 1, &tid);

 

if (cc == 1) {

msgtag = 1;

pvm_recv(tid, msgtag);

pvm_upkstr(buf);

printf("from t%x: %s\n", tid, buf);

}

else

printf("can't start hello_other\n");

 

pvm_exit();

}
```

Este programa deve ser chamado manualmente através de um terminal Linux, começa imprimindo o número da tarefa (tid), obtido da função pvm_mytid(). Dispara a cópia de outro programa chamado de hello_other (localizado em um nó “escravo”) usando a função pvm_spawn(). Se for bem-sucedido, faz com que o programa execute uma recepção de bloqueio usando pvm_recv. Depois de receber a mensagem, o programa imprime a mensagem enviada por sua contraparte, bem como seu ID de tarefa; o buffer é extraído da mensagem usando pvm_upkstr. A chamada final pvm_exit desassocia o programa do sistema PVM.

Em seguida, veja o código do programa escravo:

```c
#include "pvm3.h"

main()

{

int ptid, msgtag;

char buf[100];

ptid = pvm_parent();

strcpy(buf, "hello, world from ");

gethostname(buf + strlen(buf), 64);

msgtag = 1;

pvm_initsend(PvmDataDefault);

pvm_pkstr(buf);

pvm_send(ptid, msgtag);

pvm_exit();

}
```

Sua primeira rotina é obter a tid do “mestre” chamando a função pvm_parent(). Em seguida, com seu hostname obtido, o programa transmite para o mestre utilizando a chamada de árvore pvm_initsend() para a transmissão do buffer, colocando uma string através da função pvm_pkstr(), que será transmitida de uma maneira robusta e independente da infraestrutura e arquitetura. Isso é feito pela função pvm_send(),  que o envia ao processo de destino especificado pela ptid. Dessa forma, a mensagem é enviada e sua identificação alterada para uma tag de valor 1.


### MPI – Message Passing Interface

A MPI (Message Passing Interface) é uma biblioteca composta por métodos para troca de mensagens, que será responsável pela comunicação e sincronização de processos em um cluster paralelo. Em relação à programação, os processos de um programa paralelo podem ser escritos em uma linguagem de programação sequencial, tal como C, C++ ou Fortran. O objetivo principal da MPI é expor uma interface que seja largamente utilizada no desenvolvimento de programas com o propósito de troca de mensagens, garantindo sua portabilidade em qualquer arquitetura, mas sem a intenção de fornecer uma infraestrutura completa de software para a computação distribuída. Isso a torna recomendável para o desenvolvimento de programas paralelos de alta performance, ou seja, supercomputadores, que possuem milhares de processadores paralelos em apenas uma máquina.

Em termos simples, o objetivo da Interface de Passagem de Mensagens é fornecer um padrão amplamente usado para escrever programas de passagem de mensagens. A interface tenta ser:

- Prático.
- Portátil.
- Eficiente.
- Flexível.

Hoje, o MPI é executado em praticamente qualquer plataforma de hardware:

- Memória distribuída.
- Memória compartilhada.
- Híbrido.

No entanto, o modelo de programação permanece claramente um modelo de memória distribuída, independentemente da arquitetura física subjacente da máquina. Todo paralelismo é explícito: o programador é responsável por identificar corretamente o paralelismo e implementar algoritmos paralelos usando construções MPI.

Razões para usar o MPI:

---

#### Padronização

MPI é a única biblioteca que tem a função de troca de mensagens. É suportado em praticamente todas as plataformas HPC. Praticamente substituiu todas as bibliotecas anteriores.

#### Portabilidade

Há pouca ou nenhuma necessidade de modificar seu código-fonte quando você move o aplicativo para uma plataforma diferente que suporta o padrão MPI.

#### Oportunidades de desempenho

As implementações de fornecedores devem poder explorar os recursos de hardware nativo para otimizar o desempenho. Qualquer implementação é livre para desenvolver algoritmos otimizados.


#### Funcionalidade

Existem mais de 430 rotinas definidas no MPI-3, que incluem a maioria daquelas no MPI-2 e MPI-1. A maioria dos programas MPI pode ser escrita usando uma dúzia ou menos de rotinas.

#### Disponibilidade

Diversas implementações estão disponíveis, tanto de fornecedor quanto de domínio público.

---

### História e evolução

O MPI resultou dos esforços de numerosos indivíduos e grupos que começaram em 1992.

- Década de 1980 – início dos anos 90: a memória distribuída e a computação paralela se desenvolvem, assim como várias ferramentas de software incompatíveis para a criação de tais programas. Surgiu o reconhecimento da necessidade de um padrão.
- Abril de 1992: os recursos básicos essenciais para uma interface de passagem de mensagens padrão foram discutidos e um grupo de trabalho foi estabelecido para continuar o processo de padronização.
- Novembro de 1992: a proposta preliminar do MPI (MPI1) do ORNL é apresentada. Com o tempo, compreendeu cerca de 175 indivíduos de 40 organizações, incluindo fornecedores de computadores paralelos, criadores de software, acadêmicos e cientistas de aplicativos.
- Novembro de 1993: Supercomputing 93 conference – rascunho do padrão MPI.
- Maio de 1994: versão final do MPI-1.0 lançada.
- Atual: o padrão MPI-4.0 está em desenvolvimento.






