
---

# Get Next Line

## Descrição

Get Next Line (GNL) é um projeto da 42 que tem como objetivo implementar uma função que lê uma linha de um descritor de arquivo (file descriptor). O desafio é lidar com várias chamadas de leitura de forma eficiente e correta, permitindo que o programa leia uma linha de cada vez de qualquer tipo de entrada (arquivos, entrada padrão, etc.).

## Estrutura do Projeto

O projeto está organizado da seguinte forma:

```
get_next_line/
├── includes/
│   └── get_next_line.h
├── srcs/
│   ├── get_next_line.c
│   └── get_next_line_utils.c
├── libft/
│   ├── (contém os arquivos da sua biblioteca Libft)
├── tests/
│   └── (contém arquivos para testar o GNL)
├── Makefile
└── README.md
```

- `includes/get_next_line.h`: Arquivo de cabeçalho com as declarações das funções e definições necessárias.
- `srcs/get_next_line.c`: Implementação da função `get_next_line`.
- `srcs/get_next_line_utils.c`: Implementação de funções utilitárias usadas pelo `get_next_line`.
- `libft/`: Diretório contendo sua biblioteca Libft, que pode ser usada pelo projeto GNL.
- `tests/`: Diretório contendo arquivos para testar a função GNL.
- `Makefile`: Arquivo para compilar a biblioteca.

## Funcionalidades

### Protótipo

```c
int get_next_line(int fd, char **line);
```

### Descrição

- **Parâmetros:**
  - `fd`: O descritor de arquivo de onde será lida a linha.
  - `line`: Ponteiro para onde a linha lida será armazenada.

- **Retorno:**
  - `1`: Uma linha foi lida com sucesso.
  - `0`: O final do arquivo foi alcançado.
  - `-1`: Ocorreu um erro.

### Funções Utilitárias

- `ft_strlen`: Calcula o comprimento de uma string.
- `ft_strchr`: Encontra a primeira ocorrência de um caractere em uma string.
- `ft_strdup`: Duplica uma string.
- `ft_strjoin`: Concatena duas strings.

## Como Compilar

Para compilar o projeto, use o comando:

```bash
make
```

Isso gerará o arquivo `get_next_line.a`, que pode ser incluído em outros projetos.

## Como Usar

Inclua o cabeçalho do GNL no seu projeto:

```c
#include "get_next_line.h"
```

E, ao compilar seu projeto, adicione a biblioteca GNL e a Libft:

```bash
gcc -o my_program my_program.c -L. -lgnl -lft
```

## Exemplo de Uso

```c
#include "get_next_line.h"
#include <fcntl.h>
#include <stdio.h>

int main()
{
    int fd = open("file.txt", O_RDONLY);
    char *line;
    while (get_next_line(fd, &line) > 0)
    {
        printf("%s\n", line);
        free(line);
    }
    close(fd);
    return 0;
}
```
