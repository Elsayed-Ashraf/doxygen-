################################################################################
# Automatically-generated file. Do not edit!
################################################################################

-include ../makefile.init

RM := rm -rf

# All of the sources participating in the build are defined here
-include sources.mk
-include MCAL/subdir.mk
-include HAL/subdir.mk
-include subdir.mk
-include objects.mk

ifneq ($(MAKECMDGOALS),clean)
ifneq ($(strip $(ASM_DEPS)),)
-include $(ASM_DEPS)
endif
ifneq ($(strip $(S_DEPS)),)
-include $(S_DEPS)
endif
ifneq ($(strip $(S_UPPER_DEPS)),)
-include $(S_UPPER_DEPS)
endif
ifneq ($(strip $(C_DEPS)),)
-include $(C_DEPS)
endif
endif

-include ../makefile.defs

# Add inputs and outputs from these tool invocations to the build variables 
LSS += \
TrafficLights.lss \

FLASH_IMAGE += \
TrafficLights.hex \

EEPROM_IMAGE += \
TrafficLights.eep \

SIZEDUMMY += \
sizedummy \


# All Target
all: TrafficLights.elf secondary-outputs

# Tool invocations
TrafficLights.elf: $(OBJS) $(USER_OBJS)
	@echo 'Building target: $@'
	@echo 'Invoking: AVR C Linker'
	avr-gcc -Wl,-Map,TrafficLights.map -mmcu=atmega32 -o "TrafficLights.elf" $(OBJS) $(USER_OBJS) $(LIBS)
	@echo 'Finished building target: $@'
	@echo ' '

TrafficLights.lss: TrafficLights.elf
	@echo 'Invoking: AVR Create Extended Listing'
	-avr-objdump -h -S TrafficLights.elf  >"TrafficLights.lss"
	@echo 'Finished building: $@'
	@echo ' '

TrafficLights.hex: TrafficLights.elf
	@echo 'Create Flash image (ihex format)'
	-avr-objcopy -R .eeprom -R .fuse -R .lock -R .signature -O ihex TrafficLights.elf  "TrafficLights.hex"
	@echo 'Finished building: $@'
	@echo ' '

TrafficLights.eep: TrafficLights.elf
	@echo 'Create eeprom image (ihex format)'
	-avr-objcopy -j .eeprom --no-change-warnings --change-section-lma .eeprom=0 -O ihex TrafficLights.elf  "TrafficLights.eep"
	@echo 'Finished building: $@'
	@echo ' '

sizedummy: TrafficLights.elf
	@echo 'Invoking: Print Size'
	-avr-size --format=avr --mcu=atmega32 TrafficLights.elf
	@echo 'Finished building: $@'
	@echo ' '

# Other Targets
clean:
	-$(RM) $(FLASH_IMAGE)$(ELFS)$(OBJS)$(ASM_DEPS)$(EEPROM_IMAGE)$(S_DEPS)$(SIZEDUMMY)$(S_UPPER_DEPS)$(LSS)$(C_DEPS) TrafficLights.elf
	-@echo ' '

secondary-outputs: $(LSS) $(FLASH_IMAGE) $(EEPROM_IMAGE) $(SIZEDUMMY)

.PHONY: all clean dependents
.SECONDARY:

-include ../makefile.targets
