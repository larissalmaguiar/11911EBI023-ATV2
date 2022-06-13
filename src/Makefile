PROG=blinky
CC = arm-none-eabi-gcc
LD = arm-none-eabi-gcc
CP = arm-none-eabi-objcopy
CFLAGS = -c -mcpu=cortex-m4 -mthumb -Wall -O0#VARIAVEIS DE COMPILAÇÃO 
LFLAGS = -nostdlib -T stm32f411-rom.ld

#podemos substituir o nome do executavel por $@ que copia o nome do .c e faz a extensão .o
#$< utiliza o nome do .c que é a primeira dependencia do .o
# podemos substituir o nome do arquivo por $ qnd há uma regra implicita de compilação 
# o % pega na ordem de dependencia de all

OBJS = startup.o \
	main.o
all: $(PROG).elf
$(PROG).elf: $(OBJS)
	$(LD) $(LFLAGS) $^ -o $@$(CP) 
	$(PROG).elf -O binary $(PROG).bin
%.o: %.c
	$(CC) -c $(CFLAGS) $< -o $@
#remove todos os arquivos com final .o 
#-rf força a execução 
clean: 
	rm -f $(OBJS) $(PROG).elf