# Table Schema

## `users` Table

| Field Name | Type | Additional Property | Description |
|------------|------|---------------------|-------------|
| id | INTEGER | PRIMARY KEY | Primary key for users table |
| first_name | STRING |  | First name of the user |
| last_name | STRING | | Last name of the user |
| social_score | FLOAT | NOT NULL | Social score of the user |
| max_loan_amount | FLOAT | NOT NULL | Maximum amount of loan eligible |

## `loans` Table

| Field Name | Type | Additional Property | Description |
|------------|------|---------------------|-------------|
| id | INTEGER | PRIMARY KEY | Primary key for loans |
| outstanding_amount | FLOAT | NOT NULL | Amount of unpaid loan |
| total_amount | FLOAT |  NOT NULL | Total amount of loan taken by user |
| outstanding_installments | INTEGER | NOT NULL | Number of remaining installments |
| total_installments | INTEGER | NOT NULL | Total number of installments |
| user_id | INTEGER | FOREIGN KEY | Foregin key to the id of the `users` table |

## `emi` Table

| Field Name | Type | Additional Property | Description |
|------------|------|---------------------|-------------|
| id | INTEGER | PRIMARY KEY | Primary key for each emi paid |
| user_id | INTEGER | FOREIGN KEY | Foreign key to the id of the `users` table |
| loan_id | INTEGER | FOREIGN KEY  | Foreign key to the id of the `loans` table |

## `facebook` Table

| Field Name | Type | Additional Property | Description |
|------------|------|---------------------|-------------|
| id | STRING | PRIMARY KEY | FB user auth token |
| user_id | INTEGER | FOREIGN KEY | Foregin key to the id of the `users` table |

## `bank` Table

| Field Name | Type | Additional Property | Description |
|------------|------|---------------------|-------------|
| id | INTEGER | PRIMARY KEY |  |
| amount | FLOAT | NOT NULL | Current balance of the bank |
| currency | STRING | NOT NULL | Currency type of `amount` column |