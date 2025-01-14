# Questionário Sistemas Embarcados I

## 1. Explique brevemente o que é compilação cruzada (***cross-compiling***) e para que ela serve.
   Compilação cruzada (Cross Compiling): É o processo de compilar o código para que rode em uma plataforma diferente da que está sendo desenvolvida, sendo útil para criar software de diferentes dispositivos ou sistemas com arquiteturas diferentes, economizando tempo e recurso.
   
## 2. O que é um código de inicialização ou ***startup*** e qual sua finalidade?
   O código startup é um conjunto de instruções básicas que são executadas quando um sistema é ligado ou um programa é iniciado. Ele é responsável por configurar o hardware e preparar o sistema para a execução do software.
   
## 3. Sobre o utilitário **make** e o arquivo **Makefile responda**:
   
#### (a) Explique com suas palavras o que é e para que serve o **Makefile**.
   Makefile -> arquivo de configuração utilizado para automatizar a compilação de programas definindo regras para compilar e gerenciando dependências entre os componentes do projeto. Em suma, o Makefile simplifica o processo de compilação e execução de projetos de software.

#### (b) Descreva brevemente o processo realizado pelo utilitário **make** para compilar um programa.
   O Make usa um arquivo Makefile para automatizar o processo de compilação de um programa. A descrição do processo seria:
- Make lê o Makefile (que determina as regras de compilação e dependências)
- Make identifica arquivos executáveis ou outros artefatos localizados no Makefile
- Make verifica se os arquivos de origem foram modificados desde a última compilação
- Make executa as regras do Makefile para gerar os arquivos objeto ou executáveis
- Make atualiza os arquivos se necessário, garantindo que sempre estejam em sua versão mais atual
Make então garante que somente arquivos relevantes sejam compilados e que rode corretamente.

#### (c) Qual é a sintaxe utilizada para criar um novo **target**?
   alvo: dependência
       Comandos

meu_programa: main.c funcoes.c
gcc -o meu_programa main.c funcoes.c

gcc -> utilizado para compilar os arquivos e gerar um executável, nesse caso chamado de "meu_programa".

#### (d) Como são definidas as dependências de um **target**, para que elas são utilizadas?
   São definidas listando os arquivos ou outros alvos dos quais o alvo depende, dependências essas que determinam pelo Make se o target precisa ser reconstruído.

#### (e) O que são as regras do **Makefile**, qual a diferença entre regras implícitas e explícitas?
   Regras do Makefile definem como os target's são construídos a partir de suas dependências, sendo as regras implícitas definidas e aplicadas automaticamente pelo Make, enquanto as explicitas são definidas pelo usuário.

## 4. Sobre a arquitetura **ARM Cortex-M** responda:

### (a) Explique o conjunto de instruções ***Thumb*** e suas principais vantagens na arquitetura ARM. Como o conjunto de instruções ***Thumb*** opera em conjunto com o conjunto de instruções ARM?
   Thumb é uma extensão do conjunto ARM e oferece maior eficiência de código e economia de espaço assim como de energ. Estando no modo thumb, há a possibilidade de alternar para ARM e essa flexibilidade permite que o desempenho e tamanho do código sejam mais otimizados, utilizando das instruções que forem mais adequadas.
ARM -> Alta performance, partes mais críticas.
Thumb -> Maior economia de espaço, partes menos críticas.

### (b) Explique as diferenças entre as arquiteturas ***ARM Load/Store*** e ***Register/Register***.
   A Load/Store acessa diretamente a memória, carregando e armazenando dados.
   A Register/Memory não tem acesso direto a memória para operações aritméticas, porém tem suas ações realizadas entre registradores internos.

### (c) Os processadores **ARM Cortex-M** oferecem diversos recursos que podem ser explorados por sistemas baseados em **RTOS** (***Real Time Operating Systems***). Por exemplo, a separação da execução do código em níveis de acesso e diferentes modos de operação. Explique detalhadamente como funciona os níveis de acesso de execução de código e os modos de operação nos processadores **ARM Cortex-M**.
   Há dois tipos de nível de acesso de execução de código, sendo eles o Modo Privilegiado e o Não Privilegiado.
Em suma, o Modo Privilegiado tem acesso total aos recursos do sistema e o Não Privilegiado tem um acesso mais restrito.
Já no modo de operação há o Modo de Manipulador (lida com interrupções e exceções) e o Modo de Thread (execução de código de usuário). Todos esses recursos tem como função deixar o ambiente flexível para os sistemas, permitindo maior controle sobre o acesso ao hardware e a execução de tarefas em tempo real.

### (d) Explique como os processadores ARM tratam as exceções e as interrupções. Quais são os diferentes tipos de exceção e como elas são priorizadas? Descreva a estratégia de **group priority** e **sub-priority** presente nesse processo.
   O ARM utiliza de seu mecanismo de vetores de exceção e prioridade de interrupção.
Tipos de exceções: 
-Reiniciar
-Interrupção externa
-Falha de instrução
-Interrupção de sistema
-Interrupção de software
e etc.
O processador tende a atender primeiro as exceções de maior prioridade definidos pelo próprio sistema operacional ou pelo firmware.

### (e) Qual a diferença entre os registradores **CPSR** (***Current Program Status Register***) e **SPSR** (***Saved Program Status Register***)?
   O SPSR é usado para salvar temporariamente o estado do CPSR durante o tratamento de exceções ou interrupções, o que garante que o processador consiga retornar ao estado anterior corretamente. Já o CPSR se trata de um registrador que contém o estado atual do processador durante a execução do programa.

### (f) Qual a finalidade do **LR** (***Link Register***)?
   O LR é um registrador que permite com que o programa retorne ao ponto de origem após a conclusão da sub-rotina ou função, voltando ao seu ponto de origem utilizando o endereço armazenado no LR, garantindo com que o prograna funcione normalmente após a execução dessas chamadas sub-rotinas.

### (g) Qual o propósito do Program Status Register (PSR) nos processadores ARM?
   

### (h) O que é a tabela de vetores de interrupção?

### (i) Qual a finalidade do NVIC (**Nested Vectored Interrupt Controller**) nos microcontroladores ARM e como ele pode ser utilizado em aplicações de tempo real?

### (j) Em modo de execução normal, o Cortex-M pode fazer uma chamada de função usando a instrução **BL**, que muda o **PC** para o endereço de destino e salva o ponto de execução atual no registador **LR**. Ao final da função, é possível recuperar esse contexto usando uma instrução **BX LR**, por exemplo, que atualiza o **PC** para o ponto anterior. No entanto, quando acontece uma interrupção, o **LR** é preenchido com um valor completamente  diferente,  chamado  de  **EXC_RETURN**.  Explique  o  funcionamento  desse  mecanismo  e especifique como o **Cortex-M** consegue fazer o retorno da interrupção. 

### (k) Qual  a  diferença  no  salvamento  de  contexto,  durante  a  chegada  de  uma  interrupção,  entre  os processadores Cortex-M3 e Cortex M4F (com ponto flutuante)? Descreva em termos de tempo e também de uso da pilha. Explique também o que é ***lazy stack*** e como ele é configurado. 


## Referências

### Básicas

[1] [STM32F411xC Datasheet](https://www.st.com/resource/en/datasheet/stm32f411ce.pdf)

[2] [RM0383 Reference Manual](https://www.st.com/resource/en/reference_manual/rm0383-stm32f411xce-advanced-armbased-32bit-mcus-stmicroelectronics.pdf)

[3] [Using the GNU Compiler Collection (GCC)](https://gcc.gnu.org/onlinedocs/gcc/index.html)

[4] [GNU Make](https://www.gnu.org/software/make/manual/html_node/index.html)

### Vídeos Microsoft Teams

[5] [05 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[6] [06 - Arquitetura Cortex-M Parte 1/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[7] [07 - Arquitetura Cortex-M Parte 2/2](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[8] [08 - Microcontroladores STM32](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

[9] [10 - Introdução à arquitetura de computadores](https://web.microsoftstream.com/embed/channel/f6b3a0de-e6f3-4652-b2d5-f1164032498a?app=microsoftteams&sort=undefined&l=pt-br#)

### Material Suplementar

[5] [A General Overview of What Happens Before main()](https://embeddedartistry.com/blog/2019/04/08/a-general-overview-of-what-happens-before-main/)
 
[6] [Bare metal embedded lecture-1: Build process](https://youtu.be/qWqlkCLmZoE?si=mn5yDnJYudQ1PpZH)
 
[7] [Bare metal embedded lecture-2: Makefile and analyzing relocatable obj file](https://youtu.be/Bsq6P1B8JqI?si=yuNLPj3JQ-2IT1yo)
 
[8] [Bare metal embedded lecture-3: Writing MCU startup file from scratch](https://youtu.be/2Hm8eEHsgls?si=c27MpZ47ApiMSwHR)
 
[9] [Lecture 15: Booting Process](https://youtu.be/3brOzLJmeek?si=MsHRUEJP8zofjwJQ)
