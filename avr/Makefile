ISP ?= usbasp
#ISP ?= avrisp2
SRC := main.c keyboard.c usb.c
OUTPUT := keyboard2

all: $(SRC)
	avr-gcc -Os -mmcu=atmega32u4 -Wall $(SRC) -o bin/$(OUTPUT)
	avr-objcopy -Oihex bin/$(OUTPUT) bin/$(OUTPUT).hex
	size -A -d bin/$(OUTPUT)

fuse:
	avrdude -c${ISP} -pm32u4 -U lfuse:w:0x5f:m -U hfuse:w:0xd9:m

install:
	avrdude -c${ISP} -pm32u4 -U flash:w:bin/$(OUTPUT).hex:i

clean:
	rm -f bin/*
