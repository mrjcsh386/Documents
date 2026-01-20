## About the 'Languages' branch of documents:
To provide instructions to a computer, you first have to have a shared language that shares properties with your intended results. It should also have capabilities that support what you're trying to do, as well as make it easier to figure out what's going on.

## What to expect
It's an best effort to layout a directory structure that operates with respect to shared traits between languages. Not all languages have control flow, such html or markdown. However, they do have annotation, and abstraction. This by no means should serve as a guide on how to do things. It should be treated as reference material. Basic examples, and terse verbiage will be used much as man pages, more granular. **You** should not expect tutorials, or guide work here. This is designed from the ground up to be referential material and either have an idea of what you're doing, or already have a guide on using a language already.

---

## Synopsis:

├── 1_About.md
├── 2_Environment
├── 3_Deployment
├── 4_Assertions
│   ├── 01_Names_And_Identity
│   ├── 02_Values_and_Types
│   ├── 03_Structure_and_Scope
│   ├── 04_Control_and_Flow
│   ├── 05_Conditions_and_Decisions
│   ├── 06_Algorithms
│   ├── 07_IO_sockets_and_pipes
│   ├── 08_Exit_Codes
│   ├── 09_Abstraction_and_ReUse
│   └── 10_Metadata_and_Annotation
├── 5_Errors
├── 6_Debugging
└── 7_Help
    └── Cheat-Sheet

---

### 1_About.txt:
This document, in the flesh!

### 2_Environment/:
Before you try anything here, here's what needs to be installed, running, or configured. Some examples, such as C require a compiler, where as html et al require a web-browser. Please, remember these are not solutions to help you create server class environments. The information found here is to help you digest the language in and of themselves.

### 3_Deployment/:
Basic step-by-step instructions for making use of each language. To compile *this* language, interpret *that* language within their own contexts.

### 4_Assertions/:
This is where you will find the system's rules, behaviors, and structures are explained.
- **01_Names_and_Identity/:**
  Every named thing lives here: variables, IDs, selectors, headings. "What exists and how we distinguish it."
- **02_Values_and_Types/:**
  Constants, literals, types, and bindings, "What can a thing hold and what kinds of things exist?"
- **03_Structure_and_Scope/:**
  Nesting, block organization, visibility rules. "How things are organized and where they are valid."
- **04_Control_and_Flow/:**
  Loops, statements, execution paths. "How a system decides what happens next."
- **05_Conditions_and_Decisions/:**
  Boolean logic, conditionals, branching. "How the system chooses between options."
- **06_Algorithms/:**
  Step-by-step procedures and patterns of reasoning. "How complex actions are broken into repeatable steps."
- **07_IO_sockets_and_pipes/:**
  Input/Output operations, including files, networks, streams. "Where systems interact with the outside world."
- **08_Exit_Codes/:**
  Reference material to assist in debugging, or boolean operation for control flow, etc.
- **09_Abstraction_and_ReUse/:**
  Functions, modules, templates, macros. "How we reduce repetition and reuse concepts."
- **10_Metadata_and_Annotation/:**
  Comments, documentation, attributes, IDs, front matter. "Information about the information."

### 5_Errors/:
Here is how the system can break and what those signals mean.

### 6_Debugging/:
Here's how to investigate problems, what tools to use, and how to think about them.

### 7_Help/:
Lists of online resources so that you can find help from someone you're willing to trust. You should also find cheat-sheets with 0 fluff!