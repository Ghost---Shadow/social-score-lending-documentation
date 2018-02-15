# Routes

## Authorization

With every request, the Facebook accessToken must be passed. 

```
accessToken: String
```

## User routes

<hr>

### `/users/login` - POST - used for user login or signup

This route logs in using FB auth. If the returned userId does not exist then it creates a new account.

The server calculates the social score and uses it to calculate the maximum amount the user can borrow.

**emits**

```
{
  statusCode: Number
}
```
<hr>

### `/users/info` - GET - used for getting user information

Returns an object containing user specific information namely, name, email, and social score.

**emits**

```
{
  firstName: String,
  lastName: String,
  socialScore: Number,
  maxLoanAmount: Number
}
```
<hr>

### `/users/loans` - GET - used for getting loan history

Returns an array containing the details of all loans taken by the user.

**emits**

```
{
  loans: [
    {
      outstandingAmount: Number,
      totalAmount: Number,
      outstandingInstallments: Number,
      totalInstallments: Number
    }
  ]
}
```
<hr>

### `/users/loan` - POST - used for requesting loan

The server checks if the user is eligible for the requested loan amount. The decision is then reflected on the returned status code.

**consumes**

```
{
  amount: Number
}
```

**emits**

```
{
  statusCode: Number,
  message: String
}
```
<hr>

### `/users/emi` - POST - used for paying emi

Reduces the number of pending installments by one, if any.

**emits**

```
{
  statusCode: Number
}
```
<hr>

## Admin routes

### `/admin/loans` - GET - used by admin to view the loan ledger

Returns an array containing loan information for all users.

**emits**

```
{
  loans:
  [
    {
      loanId: Number,
      outstandingAmount: Number,
      totalAmount: Number,
      outstandingInstallments: Number,
      totalInstallments: Number,
      userId: Number,
      userName: String,
    }
  ]
}
```
<hr>

### `/admin/max_amount` - POST - used by admin to set the funds in the bank

The result of the operation is then reflected on the returned status code.

**consumes**
```
{
  amount: Number, 
  currency: String
}
```

**emits**

```
{
  statusCode: Number
}
```
<hr>

### `/admin/max_amount` - GET - used by admin to get the funds in the bank

Returns an object containing current funds and the currency information of the bank.

**emits**

```
{
  amount: Number, 
  currency: String
}
```
<hr>
