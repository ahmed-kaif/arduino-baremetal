CC = avr-gcc
CFLAGS = -Os -DF_CPU=16000000UL
OFLAGS = -O ihex -R .eeprom
DFLAGS = -F -V -c arduino -p ATMEGA328P -P /dev/ttyACM0 -b 115200 -U

all: main.o main.bin main.hex flash

main.o: main.c 
	$(CC) $(CFLAGS) -c -o $@ $^
main.bin: main.o
	$(CC) -o $@ $^
main.hex: main.bin
	avr-objcopy $(OFLAGS) $^ $@
flash: main.hex
	sudo avrdude $(DFLAGS) flash:w:$^

clean:
	rm -f *.o *.bin *.hex

