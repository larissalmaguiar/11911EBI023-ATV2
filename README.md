# 11911EBI023-ATV2

## Objetivo

A partir do que foi feito na [ATIVIDADE 1](https://github.com/larissalmaguiar/11911EBI023-ATV1) configurei a placa para ter um pino de entrada adicional(PA0). De forma que a frequência de piscada do led agora irá mudar, a depender do estado desse pino de entrada.

## Vetor de interrupções 
No arquivo [startup](src/startup.c) foram definidas as funções para o vetor de interrupção do chip, já que arquitetura ARM Cortex-M não possui nenhum Sistema Operacional para realizar estas atividades.
Ainda nesse arquivo, definimos os endereços de inicio, final e o tamanho da memoria da STACK. 

## Endereço de registradores 

No arquivo [main](src/main.c), com base nas informações presentes no datasheet do chip, é possível definir os endereços dos registradores e ajustar o valores de acordo com o necessário para habilitar a porta GPIOC. O mesmo foi feito para o GPIOA. Para essa atividade, configurei o pino PA0 em pull-up, caso ele esteja pressionado o led piscará mais lentamente e caso contrário piscará mais rapidamente. 


## Automatizando a compilação 
Para compilar o programa de maneira automatica, foi feito um arquivo [Makefile](src/Makefile), de forma que ele é responsável por compilar o [startup](src/startup.c) e [main](src/main.c), chamar o arquivo [linker](src/stm32f411-rom.ld) e gerar o arquivo [BLINK](src/blinky.elfarm-none-eabi-objcopy)
