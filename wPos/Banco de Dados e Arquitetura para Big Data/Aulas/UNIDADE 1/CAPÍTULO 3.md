UNIDADE 1 | CAPÍTULO 3 Partes	

# INFRAESTRUTURA E ARQUITETURA DE SISTEMAS DISTRIBUÍDOS


## 1 INFRAESTRUTURA E ARQUITETURA DE SISTEMAS DISTRIBUÍDOS

Um projeto em que os dados derivam de diversas fontes e em que o controle de sua produção está nas mãos de usuários da Internet, por exemplo, poderá crescer assustadoramente e necessitar de um aumento rápido de recurso. Para isso, existem formas de escalonar a disponibilidade desses recursos: a escalabilidade vertical e a escalabilidade horizontal.

A escalabilidade vertical possui uma desvantagem muito grande em relação a sua concorrente direta e sua forma de concepção está ligada, normalmente, aos limites físicos de uma arquitetura de hardware única. Ou seja, quando for necessário aumentar a capacidade de armazenamento ou de processamento, será necessário adquirir peças e componentes e acoplá-los nesse hardware.

Já a escalabilidade horizontal está ligada diretamente à quantidade de equipamentos de hardware que uma estrutura lógica e distribuída tem capacidade de receber. Ou seja, não são adquiridos peças e componentes para os equipamentos existentes, e sim novos equipamentos ligados a uma matriz de processamento. Pensando nessas estruturas distribuídas, porém gerenciada como um único modelo, algumas ferramentas foram criadas para atender o rápido crescimento que um projeto de Big Data necessita.

Entretanto, um fator muito importante para definirmos como o projeto irá crescer é escolher bem sua arquitetura. Segundo Tanenbaum (2007, p. 20), “os sistemas distribuídos são complexas peças de software das quais os componentes estão espalhados por vários computadores e, para que haja um controle eficiente, é necessário fazer a distinção lógica e física do conjunto desses componentes”.

Um bom parâmetro sugerido por Tanenbaum (2007, p. 21) para iniciar os estudos sobre arquiteturas de software distribuídos é usar seus componentes e conectores:

