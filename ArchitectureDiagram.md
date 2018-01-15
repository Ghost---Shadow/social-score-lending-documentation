# Social Score Lending

## Architecture Diagram

![ArchitectureDiagram](/images/ArchitectureDiagram.png)

**1. User Interface:**
These are the different applications for the type of user.

- Customer Application:
The customer application gives the user, access to screens like get social score, apply for loan, etc,.

- Administrator Application:
The administrator application allows for maintenance of the lending book and looking up entries in the lending book.

**2. Middleware:**
The APIs that are used in the interfaces listed above. This is a Node.js Server App that contains all the APIs discussed below.
- Loan API: Used for applying for a loan by the user.
- Loan Status API: Once a loan is applied for, the user will be able to view the status of the loan, monthly payments, and how many payments are left.
- Social Score API: The user's social score is calculated with the help of this API. It makes requests to external sources like:
    - Facebook
    - Twitter
    - Instagram
- Lending Book API: The administrator application uses the lending book API to view, and search specific details in the lending book.

**3. Database:**
The database storage (a MySQL database) will hold all the tables necessary for the operation of the user and the administrator applications.
