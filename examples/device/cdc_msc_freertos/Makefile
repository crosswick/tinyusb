include ../../../tools/top.mk
include ../../make.mk

FREERTOS_SRC = lib/FreeRTOS-Kernel

INC += \
	src \
	$(TOP)/hw \
	$(TOP)/$(FREERTOS_SRC)/include \
	$(TOP)/$(FREERTOS_SRC)/portable/GCC/$(FREERTOS_PORT)
	
# Example source
EXAMPLE_SOURCE += $(wildcard src/*.c)
SRC_C += $(addprefix $(CURRENT_PATH)/, $(EXAMPLE_SOURCE))

# FreeRTOS source, all files in port folder
SRC_C += \
	$(FREERTOS_SRC)/list.c \
	$(FREERTOS_SRC)/queue.c \
	$(FREERTOS_SRC)/tasks.c \
	$(FREERTOS_SRC)/timers.c \
	$(subst ../../../,,$(wildcard ../../../$(FREERTOS_SRC)/portable/GCC/$(FREERTOS_PORT)/*.c))

# FreeRTOS (lto + Os) linker issue
LDFLAGS += -Wl,--undefined=vTaskSwitchContext

include ../../rules.mk
