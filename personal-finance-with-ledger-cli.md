# personal finance with ledger cli

https://www.youtube.com/watch?v=FJtaM43PgXQ

-   budgeting != bookkeeping
-   In general, account names depend on the situation
-   But, one usually has the following main accounts:
    -   Expenses
    -   Income
    -   Assets
    -   Liabilities
    -   Receivables
    -   Equity
-   The level of detail needed for the subcategories (“Expenses” -> “Groceries” -> “Fruits” -> “Bananas”) is up to the requirements.
-   why accounting ? to know what you have

```
  what you can access immediately
            + what others owe you
            - what you owe others
---------------------------------
                    what you have
```

-   benefits of tracking :
    -   personal - know what you have:
        -   accross all acounts
        -   at some point in the past
        -   owe and are owed
        -   **can spend**
    -   business - required - called bookkeeping :

*   double-entry accounting :
    -   terminology :
        -   account
        -   debit
        -   credit
        -   transaction

1.  account : a label describing an amount of something

    -   5 common categories of accounts(for personal finance)
        1. assets :
            - bank account
            - wallet
            - investment
            - loans credited
        2. income :
            - paychecks
            - gifts received
            - devidends
            - interest
        3. expenses :
            - groceries
            - taxes
            - gifts given
            - donations
        4. liabilities :
            - mortgage
            - credit cards
            - student loans
            - loans owed
        5. equity :
            - for everything else
            - most often use to capture things like :
                - opening balances
                - bin for rewards(cash back)

2.  credit :
    -   the addition of value to an account
    -   increase value of an account
3.  debit :
    -   the deduction of value to an account
    -   decrease value of an account
4.  transaction :
    -   a collection of credits and debits with a timestamp
    -   to describe when the transaction is effective
    -   one transaction contains credit(+) and debit(-)
    -   most transaction debit one account and credit another
    -   but there can include multiple credits and multiple debits
    *   all transaction must always be balanced :
        -   debit + credit = 0

-   everything in ledger is just commodities :

    -   USD? commodity
    -   BTC? commodity
    -   VSTAX? commodity
    -   TSLA? commodity
    -   House? commodity

*   ledger format :
*   -   timestamp
    -   payee
    -   accounts with positive numbers for credit
    -   accounts with negative numbers for debit
    -   optional : comments

```ledger
2017-06-26 Commonplace Coffee
Expenses:Restaurants:Coffee     3.00
Assets:Cash:Wallet             -3.00
```

-   ledger lets the user emit one accounts amount
-   this signifies the ledger that
-   any imbalance in the transaction should be
    -   assigned to the account that
    -   doesn't have an explicit amount

```ledger
2017-06-26 Commonplace Coffee
Expenses:Restaurants:Coffee     3.00
Assets:Cash:Wallet
```

- balance and register alone aren't really useful
- cashflow -> useful
