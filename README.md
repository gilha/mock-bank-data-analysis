# Mock Bank Data Analysis
## Gil Harari - [LinkedIn](https://www.linkedin.com/in/gilharari/); [GitHub](https://github.com/gilha); [Mail](mailto:gil1996@gmail.com); Phone: +972-52-744-1568

---

#### Tasks I performed:
1. Created a dataset that mocks a banks database using Python and SQL (over PostgreSQL) (source code = `mock_bank_db_generation_and_deployment.ipynb`)
2. Deployed the database on the cloud (via an Amazon RDS instance, connection information below)
3. Used Power BI to create a dashboard (file = `mock_bank_dashboard.pbix`)

---

#### Connection Information for accessing the database (of type `PostgreSQL 15.2`):
* Endpoint/host: `insaitdb.cccnbalmnxxd.eu-north-1.rds.amazonaws.com`
* port: `5432`
* DB name: `insaitdb`
* username: `postgres`
* password: `postgres`

---

#### The database contains the following tables:
`clients`:

| Column Name   | Data Type     | Description                                     | Constraint Type |
|---------------|---------------|-------------------------------------------------|-------------|
| customer_id   | INT           | Unique identifier for each customer             | PRIMARY KEY |
| join_date     | DATE          | Date when the customer joined the bank           |             |
| age           | INT           | Age of the customer                              |             |
| gender        | VARCHAR(10)   | Gender of the customer                           |             |
| income        | DECIMAL(20,3) | Income of the customer                           |             |
| credit_score  | INT           | Credit score of the customer                     |             |
| education     | VARCHAR(280)  | Education level of the customer                  |             |
  
  

`financials`:

| Column Name            | Data Type     | Description                                             | Constraint Type |
|------------------------|---------------|---------------------------------------------------------|-------------|
| customer_id            | INT           | Unique identifier for each customer                     | FOREIGN KEY |
| date_id                | DATE          | Date for which the financial information is provided     |             |
| balance_amount         | DECIMAL(20,3) | Balance amount for the customer on the given date        |             |
| deposits_amount        | DECIMAL(20,3) | Total deposits made by the customer on the given date    |             |
| withdrawal_amount      | DECIMAL(20,3) | Total withdrawals made by the customer on the given date |             |
| credit_card_spending   | DECIMAL(20,3) | Total credit card spending by the customer on the given date |         |
| debit_card_spending    | DECIMAL(20,3) | Total debit card spending by the customer on the given date |          |
| cash_spending          | DECIMAL(20,3) | Total cash spending by the customer on the given date    |             |



`ledger`:

| Column Name   | Data Type     | Description                                    | Constraint Type |
|---------------|---------------|------------------------------------------------|-------------|
| customer_id   | INT           | Unique identifier for each customer            | FOREIGN KEY |
| loan_size     | DECIMAL(20,3) | Size of the loan taken by the customer          |             |
| loan_start_date | DATE         | Date when the loan was taken by the customer    |             |



#### And the following view:
`financial_status_on_loan_start`:
> "Financial status of all clients that took loans, in the day of the loan"

| Column Name          | Data Type     | Description                                                 |
|----------------------|---------------|-------------------------------------------------------------|
| customer_id          | INT           | Unique identifier for each customer                         |
| date_id              | DATE          | Date for which the financial information is provided         |
| balance_amount       | DECIMAL(20,3) | Balance amount for the customer on the given date            |
| deposits_amount      | DECIMAL(20,3) | Total deposits made by the customer on the given date        |
| withdrawal_amount    | DECIMAL(20,3) | Total withdrawals made by the customer on the given date     |
| credit_card_spending | DECIMAL(20,3) | Total credit card spending by the customer on the given date |
| debit_card_spending  | DECIMAL(20,3) | Total debit card spending by the customer on the given date  |
| cash_spending        | DECIMAL(20,3) | Total cash spending by the customer on the given date        |
| loan_size            | DECIMAL(20,3) | Size of the loan taken by the customer                       |

