# Ferramentas do toolchain

CC = arm-none-eabi-gcc
RM = rm -rf

# Diretorios arquivos objeto e de lista de dependencias serao salvos

OBJDIR = build
DEPDIR = .deps

# Arquivos a serem compilados

SRCS = src/startup.c \
       src/main.c

#Flags do compilador

CFLAGS = -g -mcpu=cortex-m4 -mthumb -Wall -O0 -I./inc
DEPFLAGS = -MMD -MP -MF $(DEPDIR)/$*.d

# Gera lista de arquivos objeto e cria diretorio onde serao salvos

OBJS = $(patsubst %, $(OBJDIR)/%.o, $(basename $(SRCS)))
$(shell mkdir -p $(dir $(OBJS)) > /dev/null)

# Gera lista de arquivos de lista dependencia e cria diretorio onde serao salvos

DEPS = $(patsubst %, $(DEPDIR)/%.d, $(basename $(SRCS)))
$(shell mkdir -p $(dir $(DEPS)) > /dev/null)

all: $(OBJS)

$(OBJDIR)/%.o: %.c $(DEPDIR)/%.d
	$(CC) -c $(CFLAGS) $(DEPFLAGS) $< -o $@

# Cria um novo target para cada arquivo de dependencia possivel

$(DEPS):

# Inclui conteudo dos arquivos de dependencia

-include $(DEPS)

.PHONY: clean
clean:
	$(RM) $(OBJDIR) $(DEPDIR)




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
