# Modular Exponentiation Solver

A lightweight, browser-based tool for solving **modular exponentiation problems** and showing the mathematical steps behind the solution.

Instead of simply returning the final remainder, the solver attempts to explain how the result is obtained through **base reduction, power-pattern discovery, and exponent simplification**.

### [→ Try the Modular Exponentiation Solver](https://yoyongler.github.io/Modulo-Calculator/)

---

## ✨ Features

* **Step-by-step solutions** for modular exponentiation
* **Base reduction** before computation
* **Power-pattern detection** to identify repeating remainders
* Handles powers that produce:

  * `1 mod m`
  * `-1 mod m`
  * repeating cycles
* **Exponent reduction** using discovered periods or cycles
* Uses JavaScript `BigInt` for large integer calculations
* Mathematical expressions rendered with **KaTeX**
* **Copy LaTeX** button for quickly copying the solution
* Handles common edge cases such as:

  * Modulo `1`
  * Exponent `0`
  * Reduced base `0`
  * Reduced base `1`
* Responsive dark-themed interface
* No installation or backend required

---

## 🧮 How It Works

Given a problem such as:

```text
5^2024 mod 9
```

the solver breaks the calculation into three main stages.

### 1. Base Reduction

The base is first reduced modulo `m`.

For example:

```text
5 ≡ 5 (mod 9)
```

This allows the remaining calculations to work with the smallest equivalent base.

---

### 2. Pattern Search

The solver calculates successive powers of the reduced base:

```text
5¹ mod 9
5² mod 9
5³ mod 9
...
```

It looks for useful patterns, such as a power that becomes:

```text
aᵖ ≡ 1 (mod m)
```

or:

```text
aᵖ ≡ -1 (mod m)
```

It also detects repeating remainder cycles when appropriate.

For example, if:

```text
5⁶ ≡ 1 (mod 9)
```

then the exponent can be reduced using the period of `6`.

---

### 3. Simplification & Substitution

Once a useful period has been found, the target exponent is divided by that period.

For example:

```text
2024 = 6 × 337 + 2
```

Therefore:

```text
5²⁰²⁴
= (5⁶)³³⁷ × 5²
```

Since:

```text
5⁶ ≡ 1 (mod 9)
```

the expression simplifies to:

```text
1³³⁷ × 5²
≡ 5²
≡ 7 (mod 9)
```

The solver presents these intermediate steps rather than only displaying the final answer.

---

## 🛠️ Built With

| Technology            | Purpose                           |
| --------------------- | --------------------------------- |
| **HTML5**             | Page structure                    |
| **JavaScript**        | Calculation logic and interaction |
| **Tailwind CSS**      | Styling and responsive layout     |
| **KaTeX**             | Mathematical expression rendering |
| **JavaScript BigInt** | Large integer arithmetic          |

The project is entirely client-side, meaning calculations happen directly in the browser.

---

## 📐 Calculation Approach

The project uses two complementary approaches.

### Pattern / Cycle Detection

The solver first attempts to find useful repeating patterns in the modular powers.

This makes the solution easier to understand mathematically and is particularly useful for learning concepts such as:

* Modular arithmetic
* Periodicity
* Congruences
* Exponent reduction
* Repeating power cycles

### Binary Modular Exponentiation

When a suitable pattern is not found, the solver falls back to **binary modular exponentiation**.

The implementation repeatedly:

1. Checks whether the current exponent is odd.
2. Multiplies the result when necessary.
3. Squares the current base.
4. Halves the exponent.

This allows very large exponents to be evaluated efficiently without calculating the enormous value of `bᵉ` directly.

---

## 🚀 Running Locally

No build system or package manager is required.

Simply clone the repository:

```bash
git clone https://github.com/yoyongler/Modulo-Calculator.git
cd Modulo-Calculator
```

Then open `index.html` in a browser.

Alternatively, use a local development server such as VS Code's **Live Server** extension.

---

## 🌐 Live Demo

The project is hosted using GitHub Pages:

**[yoyongler.github.io/Modulo-Calculator](https://yoyongler.github.io/Modulo-Calculator/)**

---

## 📋 Example

Try entering:

```text
Base:     5
Exponent: 2024
Modulo:   9
```

The solver will produce a structured solution containing:

```text
Step 1 → Base Reduction
Step 2 → Pattern Search
Step 3 → Simplification & Substitution
       → Final Answer
```

The final result is:

```text
5²⁰²⁴ ≡ 7 (mod 9)
```

The generated solution can also be copied as **LaTeX** for use in notes, assignments, or documentation.
