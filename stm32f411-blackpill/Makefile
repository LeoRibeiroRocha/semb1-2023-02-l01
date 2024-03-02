CC = arm-none-eabi-gcc
RM = rm -rf

OBJDIR = build
DEPDIR = .deps
SRCS = src/startup.c \
       src/main.c

CFLAGS = -g -mcpu=cortex-m4 -mthumb -Wall -O0 -I./inc
DEPFLAGS = -MMD -MP -MF $(DEPDIR)/$*.d

OBJS = $(patsubst %, $(OBJDIR)/%.o, $(basename $(SRCS)))
$(shell mkdir -p $(dir $(OBJS)) > /dev/null)
DEPS = $(patsubst %, $(DEPDIR)/%.d, $(basename $(SRCS)))
$(shell mkdir -p $(dir $(DEPS)) > /dev/null)
all: $(OBJS)

$(OBJDIR)/%.o: %.c $(DEPDIR)/%.d
	$(CC) -c $(CFLAGS) $(DEPFLAGS) $< -o $@

$(DEPS):
-include $(DEPS)

.PHONY: clean
clean: $(OBJDIR) $(DEPDIR) $(RM)




CC = arm-none-eabi-gcc
RM = rm -rf
OBJDIR = build
DEPDIR = .deps
SRCS = src/startup.c \
       src/main.c
CFLAGS = -g -mcpu=cortex-m4 -mthumb -Wall -O0 -I./inc
DEPFLAGS = -MMD -MP -MF $(DEPDIR)/$*.d
OBJS = $(patsubst %, $(OBJDIR)/%.o, $(basename $(SRCS)))
DEPS = $(patsubst %, $(DEPDIR)/%.d, $(basename $(SRCS)))

# Cria o diretório de destino dos arquivos objetos e os diretórios de dependências
$(shell mkdir -p $(OBJDIR) > /dev/null)
$(shell mkdir -p $(DEPDIR) > /dev/null)

all: $(OBJS)

$(OBJDIR)/%.o: %.c $(DEPDIR)/%.d
	$(CC) -c $(CFLAGS) $(DEPFLAGS) $< -o $@

# Inclui as dependências dos arquivos
-include $(DEPS)

.PHONY: clean
clean:
	$(RM) $(OBJDIR) $(DEPDIR)
