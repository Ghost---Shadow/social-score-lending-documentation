# Routes

## User routes

<hr>

### `/users/loginOrSignup` - POST - used for user login or signup

This route logs in using FB auth. If the returned userId does not exist then it creates a new account.

The server calculates the social score and uses it to calculate the maximum amount the user can borrow. It then sends that amount back to the client for client side validation.

**consumes**

```
FB-auth: userId
FB-auth: friend count
```

**emits**

```
{
  statusCode: Number,
  maxLoanAmount: Number
}
```
<hr>

### `/users/logout` - POST - used for user logout

On logout, the server deletes the session for that userId.

**consumes**

```
user-session: userId
```

**emits**

```
{
  statusCode: Number
}

```
<hr>

### `/users/history` - GET - used for getting loan history

Returns an array containing the details of all loans taken by the user.

**consumes**

```
user-session: userId
```

**emits**

```
{
  loans: [
    {
      installmentCount: Number,
      totalAmount: Number,
      outstandingAmount: Number
    }
  ]
}
```
<hr>

## Bank Routes

<hr>

### `/bank/takeLoan` - POST - used for requesting loan

The server checks if the user is eligible for the requested loan amount. The decision is then reflected on the returned status code.

**consumes**

```
user-session: userId
```

```
{
  requestAmount: Number
}
```

**emits**

```
{
  statusCode: Number
}
```
<hr>

### `/bank/payEmi` - POST - used for paying emi

Reduces the number of pending installments by one, if any.

**consumes**

```
user-session: userId
```

**emits**

```
{
  statusCode: Number
}
```
<hr>