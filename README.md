<div align="center">

# Levi Mackay

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&size=20&pause=1800&color=00FF9D&center=true&vCenter=true&width=580&lines=Built+a+compiler+in+C%2C+source+to+native+binary;Building+a+database+engine+from+the+bytes+up;CS+at+BYU-Idaho+%C2%B7+3.98+GPA;Open+to+SWE+Internships+%C2%B7+Summer+2027" alt="Typing SVG" />

[![Portfolio](https://img.shields.io/badge/portfolio-000000?style=for-the-badge&logo=googlechrome&logoColor=00ff9d)](https://levimackay.com/)
[![Resume](https://img.shields.io/badge/resume-000000?style=for-the-badge&logo=readthedocs&logoColor=00ff9d)](https://levimackay.com/resume.pdf)
[![LinkedIn](https://img.shields.io/badge/linkedin-000000?style=for-the-badge&logo=linkedin&logoColor=0a66c2)](https://www.linkedin.com/in/levi-mackay-217380396/)
[![Contact](https://img.shields.io/badge/contact-000000?style=for-the-badge&logo=maildotru&logoColor=00ff9d)](https://levimackay.com/#contact)

</div>

<br>

```
> whoami
```

I build systems from the inside out: a programming language in C, a local developer tool in Python, and software for real customers.

- Computer Science at BYU-Idaho, 3.98 GPA, graduating December 2027
- Teaching assistant in the CS department
- Open to **Summer 2027** software engineering internships

<br>

```
> tech.stack
```

**Languages**
<hr>
<img src="https://skillicons.dev/icons?i=c,swift,python,ts,js,cs,html,css" />

**Frameworks & Tools**
<hr>
<img src="https://skillicons.dev/icons?i=react,nextjs,tailwind,express,dotnet,postgres,git,github,githubactions,vscode,linux" />

[![Xcode](https://img.shields.io/badge/Xcode-000000?style=for-the-badge&logo=xcode&logoColor=147EFB)](https://developer.apple.com/xcode/)
[![Ollama](https://img.shields.io/badge/Ollama-000000?style=for-the-badge&logo=ollama&logoColor=white)](https://ollama.com)
[![Tailscale](https://img.shields.io/badge/Tailscale-000000?style=for-the-badge&logo=tailscale&logoColor=white)](https://tailscale.com)

<br>

```
> featured.project
```

### [Izvor](https://github.com/levimackay/izvor): source code to native executable

A statically typed programming language with a complete path from `.iz` source to a native binary. The compiler is written in C11 with no third-party dependencies, parser generator, or LLVM.

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

[![Stars](https://img.shields.io/github/stars/levimackay/izvor?style=flat-square&color=00FF9D&labelColor=000000)](https://github.com/levimackay/izvor/stargazers)

<br>

```
> other.work
```

| Project | Description | Stack |
|---|---|---|
| [Lydia](https://github.com/levimackay/lydia-cli) | A local coding agent that reads and edits code, runs commands, and uses Ollama without cloud API keys. Open source, with merged contributions from developers outside the project | `Python` `Ollama` |
| [minidb](https://github.com/levimackay/minidb) | A single-file database engine written by hand in C: binary formats, paging, B-trees, cursors, a SQL parser. Roadmap done, Phases 0 and 1 scaffolded with tests | `C` |
| [FORGE](https://github.com/levimackay/forge) | A native iOS Duolingo for CS fundamentals: DSA practice for students prepping technical interviews, with a skill tree that recommends against what you actually complete. Xcode project and package split in place, domain model and persistence next | `Swift 6` `iOS 26` |

<br>

```
> github.stats
```

<div align="center">

![Streak stats](./profile/streak.svg)

<picture>
  <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/levimackay/levimackay/output/github-contribution-grid-snake-dark.svg" />
  <source media="(prefers-color-scheme: light)" srcset="https://raw.githubusercontent.com/levimackay/levimackay/output/github-contribution-grid-snake.svg" />
  <img alt="contribution grid snake animation" src="https://raw.githubusercontent.com/levimackay/levimackay/output/github-contribution-grid-snake-dark.svg" />
</picture>

</div>

<br>

```
> leetcode.grind
```

<div align="center">

[![LeetCode stats for lmack03](https://leetcard.jacoblin.cool/lmack03?font=Fira_Code&ext=heatmap&border=0&radius=8)](https://leetcode.com/u/lmack03/)

</div>
