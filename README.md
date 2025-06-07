
# Cash Flow Minimizer System

## Overview

The Cash Flow Minimizer System is a C++ application designed to optimize financial transactions between multiple banks by minimizing the number of money transfers required to settle all dues. The program considers each bank's supported payment modes and introduces a central "World Bank" to facilitate transactions between incompatible banks.

This project demonstrates the use of greedy algorithms, graph theory, and mode-based constraints in a real-world financial simulation.

---

## Problem Statement

In global financial systems, different banks often operate using various payment modes (e.g., Google Pay, AliPay, Paytm). This system handles:

- A set of banks, each supporting specific payment modes.
- A list of financial obligations (debts) between these banks.
- The presence of a central "World Bank" that supports all modes and acts as an intermediary when two banks do not share a common mode.

The objective is to compute a series of transactions that settle all debts using the minimum number of transfers, while adhering to payment mode compatibility constraints.

---

## Example Setup

### List of Banks

- Bank_of_America (World Bank)
- Wells_Fargo
- Royal_Bank_of_Canada
- Westpac
- National_Australia_Bank
- Goldman_Sachs

### Transactions

| Debtor                  | Creditor                | Amount (Rs) |
|-------------------------|-------------------------|-------------|
| Goldman_Sachs           | Bank_of_America         | 100         |
| Goldman_Sachs           | Wells_Fargo             | 300         |
| Goldman_Sachs           | Royal_Bank_of_Canada    | 100         |
| Goldman_Sachs           | Westpac                 | 100         |
| National_Australia_Bank | Bank_of_America         | 300         |
| National_Australia_Bank | Royal_Bank_of_Canada    | 100         |
| Bank_of_America         | Wells_Fargo             | 400         |
| Wells_Fargo             | Royal_Bank_of_Canada    | 200         |
| Royal_Bank_of_Canada    | Westpac                 | 500         |

### Supported Payment Modes

| Bank                    | Supported Modes         |
|-------------------------|--------------------------|
| Bank_of_America         | Google_Pay, AliPay, Paytm|
| Wells_Fargo             | Google_Pay, AliPay       |
| Royal_Bank_of_Canada    | AliPay                   |
| Westpac                 | Google_Pay, Paytm        |
| Goldman_Sachs           | Paytm                    |
| National_Australia_Bank | AliPay, Paytm            |

---

## Algorithm Description

1. **Calculate Net Amounts**  
   For each bank, compute:  
```

Net Amount = (Sum of credits received) - (Sum of debits paid)

````

2. **Find Extremes**  
- Identify the bank with the maximum debt (most negative net amount).
- Identify the bank with the maximum credit (most positive net amount).
- Check for shared payment modes. If none, use the World Bank as an intermediary.

3. **Transfer Settlement**  
Transfer the minimum of the debtor's and creditor's amounts between the two banks.

4. **Update Balances**  
Adjust the net amounts. If a bank is fully settled (net amount becomes zero), remove it from consideration.

5. **Repeat**  
Continue until all bank balances are settled (net amount becomes zero).

---


### Requirements

- C++ compiler (e.g., `g++`)
- Command line or terminal access
- Optionally, Visual Studio Code or any IDE

### Compilation

For Windows (using CMD or PowerShell):

```bash
g++ -std=c++11 -o cashflow cashflow.cpp
````

For Linux/macOS:

```bash
g++ -std=c++11 -o cashflow cashflow.cpp
```

### Execution

For Windows:

```bash
cashflow.exe
```

For Linux/macOS:

```bash
./cashflow
```

---

## Features

* Menu-driven command-line interface
* Bank-wise and mode-wise transaction compatibility check
* Net balance calculation for optimal pairing
* Efficient resolution of financial transactions with minimum steps
* Realistic simulation of intermediary banking through a world bank

---

## Sample Output

The system outputs a series of transactions such as:

```
Goldman_Sachs pays Rs 300 to Wells_Fargo via Paytm
Goldman_Sachs pays Rs 100 to Royal_Bank_of_Canada via Paytm
National_Australia_Bank pays Rs 200 to Bank_of_America via Paytm
...
```


