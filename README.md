

```markdown
# 💸 Cash Flow Minimizer System

A C++ console-based application to minimize the number of transactions among multiple banks by intelligently matching their net dues, considering their supported payment modes.

---

## 🧠 About the Project

In financial systems where **multiple banks** interact, each bank may owe or be owed money by others. This program reduces the **total number of money transfers** required to settle all transactions — a process called **cash flow minimization**.

However, there's a **twist**:  
Each bank only supports certain **payment modes** (like Google Pay, AliPay, Paytm). A transaction can only occur if both banks support a **common payment mode**. To handle cases where no common mode exists, a special **World Bank** acts as an intermediary, supporting all modes.

---

## 💼 Problem Statement

Given:

- A set of **banks**, each supporting certain **payment modes**
- A list of **transactions** between banks (debtor → creditor → amount)

You must:

- Compute the **minimum number of transactions** required to settle all dues
- Ensure payments only happen via **shared modes**
- Use the **World Bank** only when necessary

---


### 🏦 Banks Involved

- `Bank_of_America` (World Bank)
- `Wells_Fargo`
- `Royal_Bank_of_Canada`
- `Westpac`
- `National_Australia_Bank`
- `Goldman_Sachs`

### 💰 Transactions

| Debtor                | Creditor               | Amount |
|-----------------------|------------------------|--------|
| Goldman_Sachs         | Bank_of_America        | Rs 100 |
| Goldman_Sachs         | Wells_Fargo            | Rs 300 |
| Goldman_Sachs         | Royal_Bank_of_Canada   | Rs 100 |
| Goldman_Sachs         | Westpac                | Rs 100 |
| National_Australia_Bank | Bank_of_America      | Rs 300 |
| National_Australia_Bank | Royal_Bank_of_Canada | Rs 100 |
| Bank_of_America       | Wells_Fargo            | Rs 400 |
| Wells_Fargo           | Royal_Bank_of_Canada   | Rs 200 |
| Royal_Bank_of_Canada  | Westpac                | Rs 500 |

### 📲 Supported Payment Modes

| Bank                   | Modes                    |
|------------------------|--------------------------|
| Bank_of_America        | Google_Pay, AliPay, Paytm|
| Wells_Fargo            | Google_Pay, AliPay       |
| Royal_Bank_of_Canada   | AliPay                   |
| Westpac                | Google_Pay, Paytm        |
| Goldman_Sachs          | Paytm                    |
| National_Australia_Bank| AliPay, Paytm            |

---

## 📈 Algorithm Summary

1. Compute the **net amount** for each bank:  
```

Net = Total Incoming - Total Outgoing

````

2. Find:
- The bank with the **highest debit** (most negative net)
- The bank with the **highest credit** (most positive net)  
→ Also ensure both share a **common payment mode**

3. Transact the **minimum of both amounts**

4. **Update net amounts** and repeat until all values become 0.

5. If no shared mode exists, use the **World Bank** as an intermediary.

---

## ▶️ How to Run

### 🛠 Prerequisites

- C++ Compiler (e.g. `g++`)
- VS Code / Terminal

### 🧾 Steps

1. **Clone or copy the code into a file** named `cashflow.cpp`
2. Open terminal and navigate to the folder
3. Compile:
```bash
g++ -std=c++11 -o cashflow cashflow.cpp
````

4. Run:

   ```bash
   ./cashflow         # On Linux/macOS
   cashflow.exe       # On Windows CMD
   ```

5. Enter inputs as prompted, or use sample inputs mentioned above.

---

## 📸 Sample Execution

> Below is a simplified illustration of the output:

```
The transactions for minimum cash flow are as follows:

Goldman_Sachs pays Rs 300 to Wells_Fargo via Paytm
Goldman_Sachs pays Rs 100 to Royal_Bank_of_Canada via Paytm
National_Australia_Bank pays Rs 200 to Bank_of_America via Paytm
...
```

---

## 🙌 Contributions

Pull requests and feedback are welcome! Feel free to fork the repository and improve upon it.

---


