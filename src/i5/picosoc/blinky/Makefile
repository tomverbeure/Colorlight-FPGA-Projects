all: firmware.hex

clean:
	rm -f firmware.hex firmware.elf

firmware.elf: sections.lds firmware.s
	/opt/riscv/bin/riscv64-unknown-elf-gcc -mabi=ilp32 -march=rv32i -Wl,-Bstatic,-T,sections.lds,--strip-debug -ffreestanding -nostdlib -o firmware.elf firmware.s

firmware.hex: firmware.elf
	/opt/riscv/bin/riscv64-unknown-elf-objcopy -O verilog firmware.elf firmware.hex

.PHONY: clean
