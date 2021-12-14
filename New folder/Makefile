


# PROJ_NAME = Project

# BUILD_DIR = Build

# # All Source code files
# SRC = main.c\
# src/fire.c alcohol.c buz.c delay.c led.c relay.c sms.c uart.c lcd.c motor.c

# # All header file paths
# INC = inc

# # Find out the OS and configure the variables accordingly
# ifdef OS	# All configurations for Windwos OS
# # Correct the path based on OS
#    FixPath = $(subst /,\,$1)
# # Name of the compiler used
#    CC = avr-gcc.exe
# # Name of the elf to hex file converter used
#    AVR_OBJ_CPY = avr-objcopy.exe
# else #All configurations for Linux OS
#    ifeq ($(shell uname), Linux)
# # Correct the path based on OS
#       FixPath = $1				
# # Name of the compiler used
# 	  CC = avr-gcc
# # Name of the elf to hex file converter used
# 	  AVR_OBJ_CPY = avr-objcopy 
#    endif
# endif

# # Command to make to consider these names as targets and not as file names in folder
# .PHONY:all analysis clean doc

# all:$(BUILD_DIR)
# # Compile the code and generate the ELF file
# 	$(CC) -g -Wall -Os -mmcu=atmega32  $(INC) $(SRC) -o $(call FixPath,$(BUILD_DIR)/$(PROJ_NAME).elf)

# $(BUILD_DIR):
# # Create directory to store the built files
# 	mkdir $(BUILD_DIR)

# analysis: $(SRC)
# # Analyse the code using Cppcheck command line utility
# 	cppcheck --enable=all $^

# doc:
# # Build the code code documentation using Doxygen command line utility
# 	make -C documentation

# clean:
# # Remove all the build files and generated document files
# 	rm -rf $(call FixPath,$(BUILD_DIR)/*)
# 	make -C documentation clean
# 	*/
#Main application file name
MAIN_APP = main
#Main hex file path in windows format
# MAIN_HEX_PATH = E:\LTTS\GEA_Learn\M4\M4_GitHubRepo\Drowsy-Driver-Detection\Program\App$(MAIN_APP).hex

# Compiler and other Section
CC = avr-gcc
OBJCOPY = avr-objcopy.exe
AVRDUDE := avrdude

#Options for avr-gcc
CFLAGS = -g -Os -o

#Linking options for avr-gcc
LFLAGS = -Os -mmcu=atmega32 -o

#Options for HEX file generation
HFLAGS = -j .text -j .data -O ihex

#Options for avrdude to burn the hex file
#MMCU model here according to avrdude options
DUDEFLAGS = -c
DUDEFLAGS += arduino 
DUDEFLAGS += -p
DUDEFLAGS += m8  
DUDEFLAGS += -P 
DUDEFLAGS += COM3 
DUDEFLAGS += -b 
DUDEFLAGS += 19200 
DUDEFLAGS += -U flash:w:$(MAIN_HEX_PATH):i

# Sources files needed for building the application 
SRC = main.c
SRC += 

# The headers files needed for building the application
INCLUDE = -I. 
INCLUDE += #add user defined application

# commands Section
Burn : Build
	$(AVRDUDE) $(DUDEFLAGS)

Build : $(MAIN_APP).elf
	$(OBJCOPY) $(HFLAGS) $< $(MAIN_APP).hex
	
$(MAIN_APP).elf: $(MAIN_APP).o
	$(CC) $(SRC) $(INCLUDE) $(LFLAGS) $@
	
$(MAIN_APP).o:$(SRC)
	$(CC) $^ $(INCLUDE) $(CFLAGS) $@
