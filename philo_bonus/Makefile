# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: dimioui <dimioui@student.42.fr>            +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2022/02/10 12:23:41 by dimioui           #+#    #+#              #
#    Updated: 2022/04/04 15:21:53 by dimioui          ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

define compiling
	@printf '$(shell tput setaf 69)Compiling$(shell tput sgr0) %s\n' $1
	@$(CC) $(CFLAGS) -c $1 -o $2
endef

define removing
	@printf '$(shell tput setaf 59)Removing$(shell tput sgr0) %s\n' $1
	@$(RM) $1 > /dev/null
endef

SRCS		=	$(addprefix srcs/, \
							main.c \
							error.c \
							parsing.c \
							utils.c \
							philo_actions.c \
				)

OBJS		= $(SRCS:.c=.o)

INC			= includes/philo.h

NAME		= philo_bonus

RM			= rm -f

CC			= cc

CFLAGS		= -Wall -Wextra -Werror -Iincludes

INCLUDE		= -pthread -g #-fsanitize=thread

%.o : %.c
			$(call compiling,$<,$(<:.c=.o),0)

${NAME}:	$(OBJS) $(INC)
			@printf '$(shell tput setaf 29)Finished Compiling √ %s\n$(shell tput sgr0)' $1
			@printf '$(shell tput setaf 69)Linking objs...\n$(shell tput sgr0)'
			$(CC) $(INCLUDE) -o $(NAME) $(OBJS)
			@printf '$(shell tput setaf 29)Finished linking √ %s\n$(shell tput sgr0)' $1
			@make -s norminette

norminette:
			@if norminette $(SRCS) $(INC) >/dev/null; then\
				echo "$(shell tput setaf 35)Norminette check √$(shell tput sgr0)";\
			else\
				echo "$(shell tput setaf 1)Norminette check ✕$(shell tput sgr0)";\
			fi

all:		$(NAME)

clean:
			$(call removing,$(OBJS))

fclean:		clean
			$(RM) $(NAME)

re:			fclean all

.PHONY: re clean fclean
