UNIDADE 1 | CAPÍTULO 3 Partes	

# INFRAESTRUTURA E ARQUITETURA DE SISTEMAS DISTRIBUÍDOS


## 1 INFRAESTRUTURA E ARQUITETURA DE SISTEMAS DISTRIBUÍDOS

Um projeto em que os dados derivam de diversas fontes e em que o controle de sua produção está nas mãos de usuários da Internet, por exemplo, poderá crescer assustadoramente e necessitar de um aumento rápido de recurso. Para isso, existem formas de escalonar a disponibilidade desses recursos: a escalabilidade vertical e a escalabilidade horizontal.

A escalabilidade vertical possui uma desvantagem muito grande em relação a sua concorrente direta e sua forma de concepção está ligada, normalmente, aos limites físicos de uma arquitetura de hardware única. Ou seja, quando for necessário aumentar a capacidade de armazenamento ou de processamento, será necessário adquirir peças e componentes e acoplá-los nesse hardware.

Já a escalabilidade horizontal está ligada diretamente à quantidade de equipamentos de hardware que uma estrutura lógica e distribuída tem capacidade de receber. Ou seja, não são adquiridos peças e componentes para os equipamentos existentes, e sim novos equipamentos ligados a uma matriz de processamento. Pensando nessas estruturas distribuídas, porém gerenciada como um único modelo, algumas ferramentas foram criadas para atender o rápido crescimento que um projeto de Big Data necessita.

Entretanto, um fator muito importante para definirmos como o projeto irá crescer é escolher bem sua arquitetura. Segundo Tanenbaum (2007, p. 20), “os sistemas distribuídos são complexas peças de software das quais os componentes estão espalhados por vários computadores e, para que haja um controle eficiente, é necessário fazer a distinção lógica e física do conjunto desses componentes”.

Um bom parâmetro sugerido por Tanenbaum (2007, p. 21) para iniciar os estudos sobre arquiteturas de software distribuídos é usar seus componentes e conectores:

>Um componente é uma unidade modular com interfaces bem definidas; substituível; reutilizável.

>Um conector é um link de comunicação entre módulos e efetua a mediação entre a coordenação ou cooperação entre os componentes.

Segundo Tanenbaum (2007, p. 21), é possível classificar os quatro mais importantes estilos arquitetônicos:

### Arquitetura em camadas

A ideia básica para o estilo em camadas é simples: os componentes são organizados de uma maneira em camadas, na qual um componente na camada Lx pode chamar componentes na camada subjacente Lx -1, mas não o contrário. Esse modelo foi amplamente adotado pela comunidade de redes. Uma observação importante é que o controle geralmente flui de camada para camada: as solicitações descem na hierarquia, enquanto os resultados fluem para cima.

### Arquitetura baseada em objetos

Uma organização muito mais flexível é seguida nas arquiteturas baseadas em objetos, na qual, em essência, cada objeto corresponde ao que definimos como componente, e esses componentes são conectados através de um mecanismo de chamada de procedimento remoto (RPC).


### Arquiteturas centradas em dados

As arquiteturas centradas em dados evoluem em torno da ideia de que os processos se comunicam por meio de um repositório comum (passivo ou ativo). Pode-se argumentar que, para sistemas distribuídos, essas arquiteturas são tão importantes quanto as arquiteturas em camadas e baseadas em objetos. Os sistemas distribuídos baseados na Web são amplamente centrados nos dados: os processos se comunicam através do uso de serviços de dados compartilhados baseados na Web.

### Arquiteturas baseadas em eventos

Nas arquiteturas baseadas em eventos, os processos se comunicam essencialmente por meio da propagação de eventos, que opcionalmente também carregam dados. Para sistemas distribuídos, a propagação de eventos geralmente tem sido associada aos sistemas de publicação / assinatura.

---


## Arquiteturas de sistemas

Outra forma de enxergar a arquitetura distribuída é analisar como eles são organizados em componentes, considerando sua localização. Segundo Tanenbaum (2007, p. 22), “a decisão sobre os componentes de software, sua interação e posicionamento leva a uma instância de uma arquitetura de software, também chamada de arquitetura de sistema e que está dividida em quatro arquiteturas:"

### Arquiteturas centralizadas

Não existe um consenso para a arquitetura centralizada, porém uma solução foi elaborada em uma referência de estudo baseado na arquitetura cliente-servidor. Um servidor é um processo que implementa um serviço específico, por exemplo, um serviço de sistema de arquivos ou um serviço de banco de dados. Um cliente é um processo que solicita um serviço de um servidor enviando uma solicitação e, posteriormente, aguardando a resposta do servidor. A comunicação entre um cliente e um servidor pode ser implementada por meio de um protocolo simples sem conexão quando a rede subjacente é razoavelmente confiável, como em muitas redes locais. As arquiteturas cliente-servidor com várias camadas são uma consequência direta da divisão de aplicativos em uma interface com o usuário, componentes de processamento e um nível de dados. As diferentes camadas correspondem diretamente à organização lógica dos aplicativos.


### Arquiteturas descentralizadas

Em muitos ambientes de negócios, o processamento distribuído é equivalente a organizar um aplicativo cliente-servidor como uma arquitetura de várias camadas, ou seja, uma distribuição vertical. A característica da distribuição vertical é que ela é obtida colocando componentes logicamente diferentes em máquinas diferentes. O termo está relacionado ao conceito de fragmentação vertical conforme usado em bancos de dados relacionais distribuídos, onde significa que as tabelas são divididas em colunas e subsequentemente distribuídas em várias máquinas.” (TANENBAUM, 2007 p. 22)


### Comunicação RPC

Segundo a IBM, em seu manual “Communication Programming Concepts”:

>a Chamada de Procedimento Remoto (RPC) é um protocolo que fornece o paradigma de comunicação de alto nível usado no sistema operacional. O RPC pressupõe a existência de um protocolo de transporte de baixo nível, como o TCP / IP ou o UDP, para transportar os dados da mensagem entre os programas em comunicação. O RPC implementa um sistema lógico de comunicação cliente-servidor projetado especificamente para o suporte de aplicativos de rede.

O protocolo RPC permite que os usuários trabalhem com procedimentos remotos como se os procedimentos fossem locais. As chamadas de procedimento remoto são definidas através de rotinas contidas no protocolo RPC. Cada mensagem de chamada é correspondida com uma mensagem de resposta. O protocolo RPC é um protocolo de passagem de mensagens que implementa outros protocolos não-RPC, como lote e transmissão de chamadas remotas. O protocolo RPC também suporta procedimentos de retorno de chamada e a sub-rotina de seleção no lado do servidor.

Entendendo a comunicação RPC, é possível facilitar o entendimento da arquitetura cliente-servidor, proposta por Tanenbaum (2007, p. 22). A IBM esclarece o conceito no mesmo manual “Communication Programming Concepts”:

>um cliente é um computador ou processo que acessa os serviços ou recursos de outro processo ou computador na rede. Um servidor é um computador que fornece serviços e recursos e implementa serviços de rede. Cada serviço de rede é uma coleção de programas remotos. Um programa remoto implementa procedimentos remotos. Os procedimentos, seus parâmetros e resultados estão todos documentados no protocolo do programa específico.

No RPC, cada servidor fornece um conjunto de procedimentos de serviço remoto baseado em programa e é combinado um endereço host, um PID e os parâmetros de entrada e saída. O cliente faz uma chamada de procedimento para enviar um pacote de dados ao servidor, quando o pacote chega, o servidor chama uma rotina de despacho, executa qualquer serviço solicitado e envia uma resposta de volta ao cliente.

Em relação ao desenvolvimento de aplicativos de comunicação RPC, o desenvolvedor precisa possuir conhecimento às teorias, bibliotecas de rede, também é útil um entendimento dos mecanismos RPC geralmente ocultos pelo compilador de protocolo do comando rpcgen. Entretatno, o uso do comando rpcgen contorna a necessidade de entender os detalhes do RPC. Várias rotinas de exemplo, APIs e códigos, poderão ser acessados no manual “Communication Programming Concepts”, mencionado anteriormente.



