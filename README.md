<div align="center">

# Levi Mackay

**Computer Science at BYU-Idaho, looking for a Summer 2027 software engineering internship**

3.98 GPA · Minor in AI Engineering · CS teaching assistant · Graduating December 2027

[Resume](https://levimackay.com/resume.pdf) · [Portfolio](https://levimackay.com/) · [LinkedIn](https://www.linkedin.com/in/levi-mackay-217380396/) · [Contact](https://levimackay.com/#contact)

</div>

I write C by hand to learn how the machine works. I direct AI coding agents to build the rest, in Swift, Go, Python and TypeScript, including a live site for my university department and a site for a paying client. Both kinds of work are below, labeled.

## Written by hand

I wrote most of Izvor by hand, and all of lsh.

### [Izvor](https://github.com/levimackay/izvor): a compiler and interpreter in C

Izvor is a small statically typed language. Its implementation is about 2,800 lines of C11: a lexer, a recursive-descent parser, a type checker, a tree-walking interpreter, and a code generator that emits C, which the system C compiler turns into a native binary. It has no third-party dependencies and no parser generator.

- 41 [golden programs](https://github.com/levimackay/izvor/tree/main/tests/golden) must print byte-for-byte identical output interpreted and compiled, errors included.
- A fixed-seed fuzzer pushes 20,000 inputs through the lexer and parser, through the type checker when they parse, and through the code generator when they type-check.
- CI runs on Linux and macOS under UndefinedBehaviorSanitizer, with a separate AddressSanitizer job on Linux.

The language has integers, booleans, typed functions, recursion and loops, with checked arithmetic and a defined evaluation order. It does not have strings, arrays or structs yet. [Try it in the browser](https://levimackay.com/) or read the [architecture notes](https://github.com/levimackay/izvor/blob/main/docs/ARCHITECTURE.md).

<a href="https://github.com/levimackay/izvor"><img src="https://raw.githubusercontent.com/levimackay/izvor/main/docs/img/hero.svg" width="100%" alt="Actual Izvor compiler output tracing a Fibonacci expression through tokens, typed syntax tree, generated C, and the compiled program's output"></a>

**[lsh](https://github.com/levimackay/lsh)** is the Unix shell I am writing in C. It follows Stephen Brennan's [Write a Shell in C](https://brennan.io/2015/01/16/write-a-shell-in-c/) tutorial and is about 80 lines so far: it reads a line with `getline`, runs programs with `fork`, `execvp` and `waitpid`, and has `cd`, `help` and `exit` built in. Pipes, redirects and a real parser are next.

## Built with AI coding agents

I built these by directing AI coding agents. The agent writes the code, tests included. The spec, the architecture, what gets tested and the review are mine. I want to be good at both: writing the code myself, and getting software I can vouch for out of an agent.

- **[CSE Videos](https://byui-cse.github.io/cse-videos/)** is the video library of the BYU-Idaho Department of Computer Science and Engineering. It is live and sits in the department's GitHub organization. A faculty member set the requirements and I am the only developer on the [repo](https://github.com/byui-cse/cse-videos). Pages are static HTML built ahead of time, so every page renders without JavaScript. CI runs data validation, unit tests and Playwright end-to-end tests on every pull request.
- **[beacon](https://github.com/levimackay/beacon)** is a native macOS menu bar app and WidgetKit widget in SwiftUI (about 2,150 lines of Swift) that monitors my own machines and websites. A Go hub collects host metrics and website checks into SQLite. CI runs 235 Go tests under the race detector. The design doc, an agent-run security audit and the fixes it led to are all in the repo.
- **[Lydia](https://github.com/levimackay/lydia-cli)** is a local AI coding agent for the terminal. It runs on local Ollama models with no API keys needed, reads code, proposes edits as diffs to confirm, runs commands and drives git. It is on [PyPI](https://pypi.org/project/lydia-cli/), has 413 tests with CI on Python 3.11 to 3.13, and has two merged pull requests from outside developers.
- **[McKay Jewelers](https://mckayjewelersmagicvalley.com)** is a jewelry store in Twin Falls, Idaho, and my first paying client. I wrote the contract, then designed, built and launched the site on Cloudflare, including the domain and DNS. [Case study](https://levimackay.com/work/mckay-jewelers/).
- **[contrail](https://github.com/levimackay/contrail)** is a prototype Claude Code plugin in TypeScript. It shows the trail behind an agent's edits and commands and grades each link by the evidence for it. 302 tests.

## Experience

- **CS Teaching Assistant, BYU-Idaho** (April 2026 to present). I coach about 100 students a semester on programming and debugging, and I promote internships and employer visits alongside CS faculty.
- **Fellow, Sandbox at BYU-Idaho** (September 2026 to present). A year-long venture program where student teams build a tech startup. I run customer discovery interviews and build prototypes with my team.
- **Founder and Developer, Main Street Sites** (May 2026 to present). A one-person web studio. McKay Jewelers is its first paying client.

I speak Serbian, Croatian and Bosnian, and compiled a 301-page [Serbo-Croatian dictionary](https://github.com/levimackay/srpsko-hrvatski) from two years of my own handwritten field notes.

I am looking for a Summer 2027 software engineering internship. My [resume](https://levimackay.com/resume.pdf) has the details, and you can reach me through [my portfolio](https://levimackay.com/#contact) or [LinkedIn](https://www.linkedin.com/in/levi-mackay-217380396/).
