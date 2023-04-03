# Account API

All the API endpoints for accessing your Fidelity account.

## `https://digital.fidelity.com/ftgw/digital/balances/api`

This API endpoint gives you some basic info about the balance of your account.

### Requirements

It requires the `ATC`, `FC`, `RC`, and `SC` cookies to be set (TODO: Reverse engineer Fidelity's cookies).

It also requires the `Content-Type` header to be set to `application/x-www-form-urlencoded;charset=UTF-8`.

The body of the request is set to:
```
accountNumber=XXXXXXXXX&accountType=Brokerage&isMultiMrgnSummaryView=false&systemOfRecord=
```
Make sure to fill in your Fidelity's account number (can be found on [your portfolio page](https://digital.fidelity.com/ftgw/digital/portfolio/summary)).
