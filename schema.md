# Table Schema

## `users` Table

| Field Name | Type | Additional Property | Description |
|------------|------|---------------------|-------------|
| id | INTEGER | PRIMARY KEY | Primary key for users table |
| firstName | STRING |  | First name of the user |
| lastName | STRING | | Last name of the user |
| socialScore | FLOAT | NOT NULL | Social score of the user |
| maxLoanAmount | FLOAT | NOT NULL | Maximum amount of loan eligible |

## `loans` Table

| Field Name | Type | Additional Property | Description |
|------------|------|---------------------|-------------|
| id | INTEGER | PRIMARY KEY | Primary key for loans |
| outstandingAmount | FLOAT | NOT NULL | Amount of unpaid loan |
| totalAmount | FLOAT |  NOT NULL | Total amount of loan taken by user |
| outstandingInstallments | INTEGER | NOT NULL | Number of remaining installments |
| totalInstallments | INTEGER | NOT NULL | Total number of installments |
| userId | INTEGER | FOREIGN KEY | Foregin key to the id of the `users` table |

## `emis` Table

| Field Name | Type | Additional Property | Description |
|------------|------|---------------------|-------------|
| id | INTEGER | PRIMARY KEY | Primary key for each emi paid |
| userId | INTEGER | FOREIGN KEY | Foreign key to the id of the `users` table |
| loanId | INTEGER | FOREIGN KEY  | Foreign key to the id of the `loans` table |

## `facebooks` Table

| Field Name | Type | Additional Property | Description |
|------------|------|---------------------|-------------|
| id | STRING | PRIMARY KEY | FB user auth token |
| userId | INTEGER | FOREIGN KEY | Foregin key to the id of the `users` table |

## `banks` Table

| Field Name | Type | Additional Property | Description |
|------------|------|---------------------|-------------|
| id | INTEGER | PRIMARY KEY |  |
| amount | FLOAT | NOT NULL | Current balance of the bank |
| currency | STRING | NOT NULL | Currency type of `amount` column |
