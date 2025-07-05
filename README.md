# https://www.programiz.com/online-compiler/98M0cAeP0DqlD
# this is the link for online rust code

# 🦀 Euler Method in Rust with Python Plotting (Colab + CSV)

This project solves an initial value problem (IVP) using the **Euler method** in **Rust**, and optionally compares the numerical solution with the analytical one using **Python in Google Colab**.

---

## 🧮 Problem Statement

Solve the ODE:

\[
\frac{dy}{dt} = \cos(t) - y,\quad y(0) = 1,\quad t \in [0, 5]
\]

---

## 📌 Parameters

- Initial condition: `y(0) = 1`
- Interval: `0 ≤ t ≤ 5`
- Step count: `n = 20` (can increase to `100` or `1000`)

---

## 🦀 Euler Method in Rust (Online Complier)

You can run this code directly in the [Rust online compiler] ([https://play.rust-lang.org](https://www.programiz.com/online-compiler/98M0cAeP0DqlD)):

```rust
fn f(t: f64, y: f64) -> f64 {
    t.cos() - y
}

fn exact_solution(t: f64) -> f64 {
    0.5 * (t.sin() + t.cos()) + 0.5 * (-t).exp()
}

fn main() {
    let a = 0.0;
    let b = 5.0;
    let n = 20;
    let h = (b - a) / n as f64;

    let mut t = a;
    let mut y = 1.0;

    println!("{:<8} {:<12} {:<12} {:<12}", "t", "Euler", "Exact", "Error");

    for _ in 0..=n {
        let exact = exact_solution(t);
        let error = (y - exact).abs();
        println!("{:<8.4} {:<12.6} {:<12.6} {:<12.6}", t, y, exact, error);

        y += h * f(t, y);
        t += h;
    }
}
📎 Output can be copied and saved as solution.csv.

📊 Plotting in Python (Google Colab Compatible)
Use the following code to plot the numerical vs analytical solutions and error.

▶️ Try it in Google Colab
python
Copy
Edit
import pandas as pd
import matplotlib.pyplot as plt

# Upload your CSV or load fixed CSV if already cleaned
df = pd.read_csv("solution_fixed.csv")
df.columns = df.columns.str.strip()  # Clean headers

# Plot Euler vs Exact
plt.plot(df['t'], df['Euler'], label='Euler Method', color='red', marker='o')
plt.plot(df['t'], df['Exact'], label='Exact Solution', color='blue', linestyle='--')
plt.plot(df['t'], df['Error'], label='Absolute Error', color='green', linestyle=':')

plt.xlabel("t")
plt.ylabel("y")
plt.title("Euler Method vs Exact Solution")
plt.grid(True)
plt.legend()
plt.tight_layout()
plt.show()
📁 Project Files
src/main.rs – Rust code (Euler + exact)

solution_fixed.csv – CSV with t, Euler, Exact, Error

plot_solution.py – Python plotting script

README.md – This file

🚀 How to Use
Run the Rust code online or locally to generate solution data.

Save the output as solution_fixed.csv

Plot using Python in Google Colab or locally.
