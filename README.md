# 11911EBI023-ATV1

## Objetivo

Nessa atividade foram construidos os arquivos de partida para processo de compilação de comandos para um sistema Cortex-M. Além disso, também foi feito um código para possibilitar que um led do chip STM32F411 acendesse. 
## Configuração do ambiente 
Para que os códidos rodem no computador é necessária a instalação de um ambiente Linux, como já utilizo esse sistema operacional não foi necessário instala-lo. Apenas baixar o compilador e a toolchain, e ambiente de edição de texto VS Code, seguindo os passos do Roteiro de Atividades 1. 

## Vetor de interrupções 
No arquivo [startup](src/startup.c) foram definidas as funções para o vetor de interrupção do chip, já que arquitetura ARM Cortex-M não possui nenhum Sistema Operacional para realizar estas atividades.
Ainda nesse arquivo, definimos os endereços de inicio, final e o tamanho da memoria da STACK. 
## Endereço de registradores 

No arquivo [main](src/main.c), com base nas informações presentes no datasheet do chip, é possível definir os endereços dos registradores e ajustar o valores de acordo com o necessário para habilitar a porta GPIOC.
Além disso, as portas do chip também são vistas como um periférico mapeado em memória, possuindo um endereço base e um conjunto de registros de configuração. São esses registros que irão permitir a configuração dos pino. No STM32F411 o led está no pino 13, então realizamos as configurações dele por meio do GPIOC.



## LINKER

O arquvio [linker](src/stm32f411-rom.ld) tem o objetivo juntar o código objeto em um local e gerar um único arquivo executável. Ainda, o principal objetivo do linker script é descrever como as seções dos arquivos objeto de entrada devem ser mapeados e controlar o layout da memória no arquivo de saída.

## Automatizando a compilação 
Para compilar o programa de maneira automatica, foi feito um arquivo [Makefile](src/Makefile), de forma que ele é responsável por compilar o [startup](src/startup.c) e [main](src/main.c), chamar o arquivo [linker](src/stm32f411-rom.ld) e gerar o arquivo [BLINK](src/blinky.elfarm-none-eabi-objcopy)
