NAMEC = client
NAMES = server
printf = minilibft.a

SRC_DIR = src/
SRCC_FILES = client.c
SRCS_FILES = server.c
SRCC = $(addprefix $(SRC_DIR), $(SRCC_FILES))
SRCS = $(addprefix $(SRC_DIR), $(SRCS_FILES))
OBJC = ${SRCC:.c=.o}
OBJS = ${SRCS:.c=.o}

CC			= cc
CFLAGS		= -Wall -Werror -Wextra
INCLUDE = -I include
RM = rm -rf

all: $(NAMEC) $(NAMES)

$(NAMEC): $(OBJC)
	@make -C minilibft -s
	@echo "Compiling $(NAMEC)..."
	@$(CC) $(CFLAGS) $(INCLUDE) -c $(SRCC) -o $(OBJC)
	@$(CC) $(CFLAGS) $(OBJC) minilibft/$(printf) -o $(NAMEC)
	@echo "$(NAMEC) compiled successfully!"

$(NAMES): $(OBJS)
	@make -C minilibft -s
	@echo "Compiling $(NAMES)..."
	@$(CC) $(CFLAGS) $(INCLUDE) -c $(SRCS) -o $(OBJS)
	@$(CC) $(CFLAGS) $(OBJS) minilibft/$(printf) -o $(NAMES)
	@echo "$(NAMES) compiled successfully!"

clean:
	@make -C minilibft clean -s
	@echo "Cleaning object files..."
	@$(RM) $(OBJC)
	@$(RM) $(OBJS)

fclean: clean
	@make -C minilibft fclean -s
	@echo "Cleaning executables..."
	@$(RM) $(NAMEC)
	@$(RM) $(NAMES)
	@$(RM) $(printf)

re: fclean all

.PHONY: all clean fclean re
