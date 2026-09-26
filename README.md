# Levi Mackay

I build systems from the inside out: a programming language in C, a local developer tool in Python, and software for real customers.

Computer Science at BYU–Idaho · CS teaching assistant · 3.98 GPA · graduating December 2027  
Open to Summer 2027 software engineering internships.

[Portfolio](https://levimackay.com) · [Résumé](https://levimackay.com/resume.pdf) · [LinkedIn](https://www.linkedin.com/in/levi-mackay-217380396/) · [Contact](https://levimackay.com/#contact)

## Izvor: source code to native executable

I built [Izvor](https://github.com/levimackay/izvor), a statically typed programming language with a complete path from `.iz` source to a native binary. The compiler is written in C11 with no third-party dependencies, parser generator, or LLVM.

<a href="https://github.com/levimackay/izvor"><img src="https://raw.githubusercontent.com/levimackay/izvor/main/docs/img/hero.svg" width="100%" alt="Actual Izvor compiler output tracing a Fibonacci expression through tokens, typed syntax tree, generated C, and the compiled program's output"></a>

The lexer, recursive-descent parser, type checker, interpreter, and C code generator form one working pipeline. Izvor handles typed functions, recursion, mutable and immutable bindings, control flow, and checked arithmetic. It reports errors with the file, line, column, and a caret under the offending expression.

The interpreter and compiled binary must produce byte-for-byte identical output for all **36 golden programs**, including errors. A fixed-seed fuzzer runs **20,000 inputs** through the front end; CI also runs the tests on Linux and macOS with sanitizers.

```sh
git clone https://github.com/levimackay/izvor && cd izvor && make
./build/izvor run examples/fib.iz    # interpret
./build/izvor build examples/fib.iz  # build a native executable
./examples/fib
```

[Read the architecture](https://github.com/levimackay/izvor/blob/main/docs/ARCHITECTURE.md) · [See the tests](https://github.com/levimackay/izvor/tree/main/tests/golden) · [Explore the language](https://github.com/levimackay/izvor)

## Other work

- **[Lydia](https://github.com/levimackay/lydia-cli)** — A local coding agent that reads and edits code, runs commands, and uses Ollama without cloud API keys. Open source, with merged contributions from developers outside the project.
- **[Main Street Sites](https://levimackay.com/projects/#mainstreet)** — My web design studio for eastern Idaho businesses, built around real client work.
- **[Srpsko-Hrvatski](https://github.com/levimackay/srpsko-hrvatski)** — A 301-page Serbo-Croatian dictionary assembled in Croatia, Serbia, and Bosnia from 5,709 field entries.

I teach in BYU–Idaho's CS department and work on software where the implementation details matter. [Get in touch](https://levimackay.com/#contact).
