# Opensource toolchain tutorial for CSM32RV20

CSM32RV20 is a low-power MCU chip based on RISC-V core, made by Nanjing zhongke microelectronics .
- Built-in RISC-V RV32IMAC core (2.6 CoreMark/MHz);
- Up to 32MHz working frequency;
- Built-in 4kB SRAM;
- Built-in 8B ALWAYS register, which can save data in power-down mode 2;
- Built-in 40kB embedded FLASH, 512B NVM, which can be erased and written at least 10,000 times;
- Built-in 2 SPI MASTER;
- Built-in 1 I2C MASTER;
- Built-in 4 UARTs support up to 1Mbps;
- Built-in 2 TIMERs, each TIMER supports 4 complementary PWM outputs;
- Built-in a fast high-precision 13/14/15/16bit ADC, integrated 1.2V high-precision reference;
- Wide ADC input voltage range: 0 ~ VDD (VDD ≤ 4.8V);
- ADC supports 11 input channels and supports up to 9 touch keys;
- Built-in 3 fast comparators;
- Built-in low voltage detection module;
- Built-in RF detection module;
- Support up to 30 GPIOs, of which the PA port supports external interrupts (up to 16 external interrupts);
- Built-in hardware watchdog;
- Built-in 1 RTC, does not work in power-down mode 2;
- Support 4 low power consumption modes, the lowest power consumption is less than 1uA (watchdog working);
- Built-in 32-bit true random number generator;
- Support serial port and wireless ISP online upgrade (wireless ISP needs an external Si24R1);
- Support cJTAG 2-wire debug interface;
- Operating voltage range: 1.8 ~ 5.5V;
- Supports 4x4mm QFN32, TSSOP20 and 3x3mm QFN20 packages.

It provide limited Linux support with CSMStudio linux version, but comparing with CSMStudio window version, the linux version is outdated, can not run due to compatibility, lack cjlink support, JLink not works, close source, etc. In short, it not worked as expected.

**NOTE :** There is another firmware library provided in CSMStudio for 'Shanghai WestBerry WB32F030', after diff with CSM32RV20 firmware library v1.2.0, both are exactly identical, these two MCUs are same with different brand.

# Hardware prerequiest
- Official EVB
- Any JLink adapter(above v10)

# Toolchain overview
- Compiler : RISC-V GNU Toolchain
- SDK : official firemware library
- Programming : JLink
- Debugging : JLink GDB Server / gdb

# Compiler

As other RV32IMAC based RISC-V MCU, there are a lot of prebuilt riscv toolchains you can download and use it directly.

## XPack RISCV toolchain

[xpack-dev-tools](https://github.com/xpack-dev-tools/riscv-none-elf-gcc-xpack/) provde a prebuilt toolchain for riscv. you can download it from https://github.com/xpack-dev-tools/riscv-none-elf-gcc-xpack/. The lastest version is '12.2.0', Download and extract it:

```
sudo mkdir -p /opt/xpack-riscv-toolchain
sudo tar xf xpack-riscv-none-elf-gcc-12.2.0-3-linux-x64.tar.gz -C /opt/xpack-riscv-toolchain --strip-components=1
```

And add `/opt/xpack-riscv-toolchain/bin` to PATH env according to your shell.

**NOTE**, the target triplet of xpack riscv toolchain is **`riscv-none-elf`**.

You can also use the deprecated `riscv-none-embed` toolchain from XPack, the installation is same as `riscv-none-elf` toolchain, both work good.

# SDK
The 

