# Social Score Lending

## Data Model Diagram

![Data Model Diagram](/images/DataModelDiagram.png)

**1. Customer :**
This table stores basic details about customer, like name, email, address, etc and the calculated Social score.

**2. Social :**
This table stores platform name(Facebook, Twitter, Instagram) and the associated userid.

**3. Loan :**
This table stores total amount a person is eligible for, amount lended, number of installments and dates of first and last installment.

**4. Payment :**
This table stores data about loan repayments, like payment amount, date, number of the installment, etc.
