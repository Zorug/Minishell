# minishell

*This project has been created as part of the 42 curriculum by Carol Cortes, Cassiano Gross.*

## Description

**minishell** is a simple shell implementation written in C as part of the 42 curriculum. The project aims to recreate a minimal yet functional bash-like shell that properly handles command execution, I/O redirections, pipes, environment variables, and built-in commands. Through this project, we gain extensive knowledge about processes, file descriptors, signals, and the inner workings of shell interpreters.

### Features

- **Interactive prompt** with command history using readline
- **Command execution** supporting both absolute and relative paths, with PATH resolution
- **Built-in commands**: `echo` (with `-n` option), `cd`, `pwd`, `export`, `unset`, `env`, `exit`
- **I/O Redirections**: `<` (input), `>` (output), `>>` (append), `<<` (heredoc)
- **Pipes** (`|`) to chain commands together
- **Environment variable expansion** (`$VAR` and `$?` for exit status)
- **Quote handling**: Single quotes (`'`) and double quotes (`"`) with proper escaping
- **Signal handling**: `CTRL+C`, `CTRL+D`, and `CTRL+\` with bash-like behavior
- **Proper memory management** with no memory leaks

## Instructions

### Compilation

```bash
make          # Compile the project
make clean    # Remove object files
make fclean   # Remove all generated files
make re       # Clean and recompile
```

### Running

```bash
./minishell
```

Once launched, you'll see a prompt and can start entering commands just like in bash:

```bash
minishell> echo "Hello, World!"
Hello, World!
minishell> pwd
/path/to/current/directory
minishell> ls -la | grep minishell
minishell> export MY_VAR=42
minishell> echo $MY_VAR
42
```

### Requirements

- **OS**: Linux/Unix-like systems
- **Compiler**: `cc` (gcc/clang)
- **System Libraries**: readline library must be installed
- **libft**: A custom C library included in this project

### Project Structure

```
.
├── inc/                    # Header files
│   └── minishell.h        # Main header
├── src/                   # Source code
│   ├── main.c             # Entry point
│   ├── main_ext1.c        # Main extensions
│   ├── main_ext2.c
│   ├── signals.c          # Signal handling
│   ├── environment.c      # Environment management
│   ├── expand.c           # Variable expansion
│   ├── expand_ext*.c      # Expansion extensions
│   ├── utils.c            # Utility functions
│   ├── free.c             # Memory management
│   ├── builtins/          # Built-in commands
│   ├── execution/         # Command execution
│   └── parsing/           # Input parsing & tokenization
├── libft/                 # Custom C library
├── Makefile               # Build configuration
└── README.md              # This file
```

## Resources

### References

- [Bash Manual](https://www.gnu.org/software/bash/manual/)
- [Linux man pages online](https://man7.org/)
- [42 Libft Documentation](https://github.com/42School/libft)
- [readline(3) - GNU readline library](https://tiswww.case.edu/php/chet/readline/rltop.html)
- [Processes and File Descriptors](https://en.wikipedia.org/wiki/File_descriptor)
- [Pipes in C](https://www.geeksforgeeks.org/pipe-system-call/)

### AI Usage

AI tools were utilized for:
- **Code structure and architecture**: Guidance on organizing the parsing, execution, and built-in command modules
- **Memory management patterns**: Assistance with proper allocation and freeing strategies for complex data structures
- **Signal handling implementation**: Understanding signal handlers and their proper use with global variables
- **Testing and validation**: Creating test cases and edge case scenarios
- **Documentation and README**: Formatting and structuring project documentation

All AI-generated code was thoroughly reviewed, tested, and verified for correctness and compliance with the 42 Norm before being integrated into the project.

## Technical Notes

- The shell uses a single global variable to store signal numbers, ensuring safe signal handling
- Implements a custom tokenizer for proper command-line argument parsing
- Handles heredoc without updating shell history (as per requirements)
- Memory is properly freed to prevent leaks (readline library leaks are not the project's responsibility)
