# 🖥️ Nand2Tetris — From NAND to Tetris in Python

> Building a modern computer from first principles, one gate at a time.

---

## 📂 Quick Start

```bash
# 1. Clone the repo
git clone https://github.com/harshchikorde/NAND2TETRIS.git
cd NAND2TETRIS

# 2. Install dependencies
pip install -r requirements.txt

# 3. Configure your paths
cp .env.example .env   # then edit .env with your file paths
```

---

## 📖 About Nand2Tetris

**Nand2Tetris** (officially titled *From Nand to Tetris: Building a Modern Computer From First Principles*) is a landmark computer science course and textbook created by **[Noam Nisan](http://www.cs.huji.ac.il/~noam/)** and **[Shimon Schocken](http://www.shimonschocken.com)**.

The course was born from a simple but profound question:

> *"Can we build a complete, working computer — from the most primitive logic gate all the way up to a high-level programming language and operating system — from scratch?"*

The answer is yes, and this course shows you exactly how.

### 🏛️ History

- The course was originally developed at the **Hebrew University of Jerusalem** and the **Interdisciplinary Center Herzliya** in Israel.
- The accompanying book, **"The Elements of Computing Systems"**, was published by **MIT Press** (now freely available in its 2nd edition).
- The course is taught at **400+ universities, high schools, and bootcamps** worldwide, with students ranging from high schoolers to Ph.D. students to senior software engineers.
- It is freely available at [nand2tetris.org](https://www.nand2tetris.org) and on [Coursera](https://www.coursera.org/learn/build-a-computer).
- A landmark CACM article about the course is available [here](https://dl.acm.org/doi/10.1145/3626513).

### 🎯 What the Course Covers

The journey spans **12 projects** divided into two parts:

#### Part I — Hardware
| Project | Topic |
|---------|-------|
| Project 1 | Boolean Logic (elementary logic gates) |
| Project 2 | Boolean Arithmetic (ALU) |
| Project 3 | Memory (RAM, registers, program counter) |
| Project 4 | Machine Language (Hack assembly programming) |
| Project 5 | Computer Architecture (the Hack computer) |
| Project 6 | **Assembler** ← implemented here as `asm.py` |

#### Part II — Software
| Project | Topic |
|---------|-------|
| Project 7 | VM I: Stack Arithmetic |
| Project 8 | VM II: Program Control |
| Project 9 | High-Level Language (Jack) |
| Project 10 | Compiler I: Parsing (Tokenizer + Parse Tree) |
| Project 11 | **Compiler II: Code Generation** ← implemented here as `comp.py` / `comp2.py` |
| Project 12 | Operating System |

---

## 📁 Project Structure

```
NAND2TETRIS/
├── asm.py       # Hack Assembler   — translates .asm → .hack (binary machine code)
├── vm.py        # VM Translator    — translates .vm  → .asm  (Hack assembly)
├── comp.py      # Jack Compiler I  — tokenizer + parse tree generator → XML
├── comp2.py     # Jack Compiler II — full compilation engine → VM code
└── rough.py     # Scratch / helper file
```

### Tool Descriptions

| File | Role | Input | Output |
|------|------|-------|--------|
| `asm.py` | **Hack Assembler** | `.asm` (Hack assembly) | `.hack` (16-bit binary) |
| `vm.py` | **VM Translator** | `.vm` (Jack VM bytecode) | `.asm` (Hack assembly) |
| `comp.py` | **Jack Compiler (Tokenizer)** | `.jack` (Jack language) | `token.xml` (token stream) |
| `comp2.py` | **Jack Compiler (Full)** | `.jack` (Jack language) | `.vm` (VM bytecode) |

---

## ⚙️ Prerequisites

- Python 3.x
- All dependencies listed in `requirements.txt`

Install all dependencies at once:
```bash
pip install -r requirements.txt
```

### `requirements.txt` contents

| Package | Version | Used by | Purpose |
|---------|---------|---------|--------|
| `colorama` | `>=0.4.6` | `comp2.py` | Coloured terminal output |
| `python-dotenv` | `>=1.0.0` | All scripts | Loads `.env` config into `os.environ` |

---

## 🗺️ Hardcoded Paths & `.env` Configuration

All scripts originally contained hardcoded Windows paths. These are now documented in the `.env` file so you can configure them in one place without touching source code.

### All Hardcoded Paths Found

| Variable | Default Value | File | Line | Description |
|----------|--------------|------|------|-------------|
| `ASM_INPUT_PATH` | `D:/nand2tetris/projects/06/max/Max.asm` | `asm.py` | 244 | Input `.asm` file for the assembler |
| `TEMP_PARSED_FILE` | `D:/nand2tetris/projects/sampleparsed.txt` | `asm.py` | 17, 252, 263 | Temporary cleaned-up instruction file |
| `VM_INPUT_PATH` | `D:/nand2tetris/projects/08/FunctionCalls/StaticsTest/Class2.vm` | `vm.py` | 352 | Input `.vm` file for the VM translator |
| `TEMP_PARSED_FILE` | `D:/nand2tetris/projects/sampleparsed.txt` | `vm.py` | 360, 370 | Temporary cleaned-up instruction file |
| `COMP_INPUT_PATH` | `D:/nand2tetris/projects/10/ExpressionLessSquare/SquareGame.jack` | `comp.py` | 1026 | Input `.jack` file for Compiler I |
| `TEMP_PARSED_FILE` | `D:/nand2tetris/projects/sampleparsed.txt` | `comp.py` | 10, 1033 | Temporary cleaned-up source file |
| `TEMP_TOKEN_XML` | `D:/nand2tetris/projects/token.xml` | `comp.py` | 64, 1037 | Token stream XML output |
| `TEMP_TTOKEN_XML` | `D:/nand2tetris/projects/ttoken.xml` | `comp.py` | 130 | Final parse tree XML output |
| `COMP2_INPUT_PATH` | `D:/nand2tetris/projects/10/ExpressionLessSquare/SquareGame.jack` | `comp2.py` | 1391 | Input `.jack` file for Compiler II |
| `TEMP_PARSED_FILE` | `D:/nand2tetris/projects/sampleparsed.txt` | `comp2.py` | 13, 1398 | Temporary cleaned-up source file |
| `TEMP_TOKEN_XML` | `D:/nand2tetris/projects/token.xml` | `comp2.py` | 69, 1402 | Token stream XML output |
| `TEMP_TTOKEN_XML` | `D:/nand2tetris/projects/ttoken.xml` | `comp2.py` | 203 | Final parse tree XML output |
| `TEMP_VM_CODE` | `D:/nand2tetris/projects/vm_code.vm` | `comp2.py` | 527 | VM code output from compiler |

### Setting Up `.env`

1. Copy the example file:
   ```bash
   cp .env.example .env
   ```

2. Open `.env` and update every path to match your system:
   ```dotenv
   # Linux / macOS example
   NAND2TETRIS_PROJECTS_DIR=/home/yourname/nand2tetris/projects
   ASM_INPUT_PATH=/home/yourname/nand2tetris/projects/06/max/Max.asm
   VM_INPUT_PATH=/home/yourname/nand2tetris/projects/08/FunctionCalls/StaticsTest/Class2.vm
   COMP_INPUT_PATH=/home/yourname/nand2tetris/projects/10/ExpressionLessSquare/SquareGame.jack
   COMP2_INPUT_PATH=/home/yourname/nand2tetris/projects/10/ExpressionLessSquare/SquareGame.jack
   TEMP_PARSED_FILE=/home/yourname/nand2tetris/projects/sampleparsed.txt
   TEMP_TOKEN_XML=/home/yourname/nand2tetris/projects/token.xml
   TEMP_TTOKEN_XML=/home/yourname/nand2tetris/projects/ttoken.xml
   TEMP_VM_CODE=/home/yourname/nand2tetris/projects/vm_code.vm
   VM_BOOTSTRAP=False
   ```

3. Add `.env` to `.gitignore` to keep your local paths out of version control:
   ```bash
   echo ".env" >> .gitignore
   ```

> **Note:** Until the scripts are updated to read from `.env` via `python-dotenv`, you still need to manually update the `path` variable inside each script's `if __name__ == "__main__":` block. The `.env` file serves as the authoritative reference for what all the paths should be.

---

## 🚀 How to Run

---

### 1️⃣ Assembler — `asm.py`

Translates Hack **assembly language** (`.asm`) into **binary machine code** (`.hack`).

**Edit `asm.py`** (line ~244), set the path to your `.asm` file:
```python
path = '/path/to/your/Program.asm'
```

Then run:
```bash
python asm.py asm
```

**Output:** A `.hack` file containing 16-bit binary instructions, saved alongside the input file.

---

### 2️⃣ VM Translator — `vm.py`

Translates **VM bytecode** (`.vm`) generated by the Jack compiler into **Hack assembly** (`.asm`).

**Edit `vm.py`** (line ~352), set the path to your `.vm` file:
```python
path = '/path/to/your/Program.vm'
bootstrap_switch = False   # Set to True if translating a multi-file program that needs Sys.init
```

Then run:
```bash
python vm.py vm
```

**Output:** A `.asm` file ready to be assembled with `asm.py`.

---

### 3️⃣ Jack Compiler — `comp.py` (Tokenizer / Parser)

Tokenizes and parses a **Jack language** source file (`.jack`) and outputs an XML token stream.

**Edit `comp.py`** (near the bottom), set the path to your `.jack` file:
```python
path = '/path/to/your/Program.jack'
```

Then run:
```bash
python comp.py comp
```

**Output:** A `token.xml` file showing the token classification for each element.

---

### 4️⃣ Full Jack Compiler — `comp2.py` (Code Generation)

Compiles **Jack source code** all the way to **VM bytecode** via tokenization, parsing, and code generation.

**Edit `comp2.py`** (near the bottom), set the path to your `.jack` file:
```python
path = '/path/to/your/Program.jack'
```

Then run:
```bash
python comp2.py comp2
```

**Output:** A `token.xml` parse tree and VM code written via the `CompilationEngine`.

---

## 🧪 Sample Programs to Test

### Sample 1 — Hack Assembly: Add Two Numbers

Create a file called `Add.asm`:
```asm
// Computes R0 = 2 + 3
// (Using the Hack assembly language)

@2
D=A       // D = 2

@3
D=D+A     // D = 2 + 3 = 5

@R0
M=D       // RAM[0] = 5
```

Set `path = '/path/to/Add.asm'` in `asm.py`, then run:
```bash
python asm.py asm
```
**Expected output:** `Addhack.hack` with binary instructions. RAM[0] holds the value `5` when run in the CPU emulator.

---

### Sample 2 — Hack Assembly: Max of Two Numbers

Create a file called `Max.asm`:
```asm
// Computes R2 = max(R0, R1)
// Assumes R0 and R1 have been initialized

   @R0
   D=M        // D = RAM[0]

   @R1
   D=D-M      // D = RAM[0] - RAM[1]

   @OUTPUT_FIRST
   D;JGT      // if D > 0 (R0 > R1), goto OUTPUT_FIRST

   @R1
   D=M        // D = RAM[1]

   @OUTPUT_D
   0;JMP

(OUTPUT_FIRST)
   @R0
   D=M        // D = RAM[0]

(OUTPUT_D)
   @R2
   M=D        // RAM[2] = D

(INFINITE_LOOP)
   @INFINITE_LOOP
   0;JMP
```

Set `path = '/path/to/Max.asm'` in `asm.py`, then run:
```bash
python asm.py asm
```
**Expected output:** `Maxhack.hack`. Load in the CPU emulator with RAM[0]=3, RAM[1]=5 → RAM[2] should equal `5`.

---

### Sample 3 — VM Bytecode: Stack Arithmetic

Create a file called `SimpleAdd.vm`:
```
// Pushes two constants and adds them
push constant 7
push constant 8
add
```

Set `path = '/path/to/SimpleAdd.vm'` in `vm.py`, then run:
```bash
python vm.py vm
```
**Expected output:** `SimpleAdd.asm`. Load in the CPU emulator — the top of the stack (RAM[256]) should equal `15`.

---

### Sample 4 — VM Bytecode: Boolean Logic

Create a file called `BasicTest.vm`:
```
// Tests push/pop and arithmetic VM commands
push constant 10
push constant 10
eq           // pushes -1 (true) onto stack: 10 == 10

push constant 57
push constant 31
gt           // pushes -1 (true): 57 > 31

push constant 17
push constant 14
lt           // pushes 0 (false): 17 is NOT < 14
```

Set `path = '/path/to/BasicTest.vm'` in `vm.py`, then run:
```bash
python vm.py vm
```

---

### Sample 5 — Jack Language: Hello World

Create a file called `Main.jack`:
```jack
class Main {
    function void main() {
        do Output.printString("Hello, Nand2Tetris!");
        do Output.println();
        return;
    }
}
```

Run through the full compilation pipeline:
1. Compile with `comp2.py` → produces VM code
2. Translate with `vm.py` → produces `.asm`
3. Assemble with `asm.py` → produces `.hack`
4. Load `.hack` in the **Nand2Tetris VM Emulator** to see output on screen.

---

## 🔄 Full Pipeline Overview

```
  .jack (Jack source code)
      │
      ▼  comp2.py (Jack Compiler)
  .vm   (Virtual Machine bytecode)
      │
      ▼  vm.py (VM Translator)
  .asm  (Hack Assembly)
      │
      ▼  asm.py (Assembler)
  .hack (Binary Machine Code)
      │
      ▼  CPU Emulator / Hardware
  💻  Output on Hack Computer
```

---

## 📚 Resources

| Resource | Link |
|----------|------|
| Official Website | [nand2tetris.org](https://www.nand2tetris.org) |
| Coursera Course (Part 1) | [Build a Modern Computer - Part I](https://www.coursera.org/learn/build-a-computer) |
| The Book (MIT Press) | [The Elements of Computing Systems](https://www.amazon.com/Elements-Computing-Systems-Building-Principles/dp/0262640686) |
| Nand2Tetris Software Suite | [Download Tools](https://www.nand2tetris.org/software) |
| Q&A Forum | [Community Forum](http://nand2tetris-questions-and-answers-forum.52.s1.nabble.com/) |
| CACM Article | [Read the Paper](https://dl.acm.org/doi/10.1145/3626513) |

---

## 🙌 Acknowledgements

This project was built as part of the **Nand2Tetris** course by:
- **Noam Nisan** — Hebrew University of Jerusalem
- **Shimon Schocken** — Interdisciplinary Center Herzliya

> *"The best way to understand something is to build it yourself."*

---

*© Course materials: Noam Nisan & Shimon Schocken. This implementation is for educational purposes.*