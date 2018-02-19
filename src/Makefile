#Muuta #include <****> muotoon #include "****" jos ei toimi kääntö
BIN= salama
OBJS=salama.o vilkutus.o
MCU=attiny861

CC=avr-gcc
OBJCOPY=avr-objcopy
CFLAGS=-Os -DF_CPU=8000000UL -mmcu=${MCU} -Wall -std=c99
PORT=/dev/ttyUSB0

${BIN}.hex: ${BIN}.elf
	${OBJCOPY} -O ihex $< $@

${BIN}.elf: ${OBJS}
	${CC} -mmcu=${MCU} -o $@ $^

install: ${BIN}.hex
	avrdude -v -c arduino -p ${MCU} -P ${PORT} -b 19200 -U flash:w:$< -F
fuse:
	avrdude -c avrisp -p t861 -B3 -P /dev/ttyUSB0 -b 19200 -U lfuse:w:0xe2:m -U hfuse:w:0xdf:m
clean:
	rm -f ${BIN}.elf ${BIN}.hex ${OBJS}

