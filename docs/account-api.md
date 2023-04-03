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

### Response

Sending a valid request to this API will result in an object similar to this:
```
{
  "account": {
    "acctNum”:”XXXXXXXXX”,”acctType": "Brokerage",
    "acctSubType": "L2Cash",
    "isOptionAgrmntSigned": false,
    "isMultiMrgnSummaryView": "false",
    "isHardToBorrow": false,
    "isManagedAccount": false,
    "isSpreadTradingType": false
  },
  "balance": {
    "acctNum”:”XXXXXXXXX”,”brokBalDetail": {
      "trustDetail": {
        "isTrustAcct": false
      },
      "mrgnDetail": {
        "hasMrgnCalls": false,
        "mrgnCreditDebitLabel": "credit/debit"
      },
      "indicatorDetail": {
        "hasUnpricedOrders": false,
        "hasUnpricedPositions": false
      },
      "availToWithdrawDetail": {
        "cashAvailToWithdraw”:500.00,”cashOnlyAvailToWithdraw”:500.00},”cashDetail": {
          "coreCash”:2000.00,”cashCreditDebit”:-1500.00,”cashCreditDebitChg": 0,
          "cashSettled”:500.0”,cashCreditDebitLabel": "debit"
        },
        "buyingPowerDetail": {
          "dayTradeMinimumEquityCallLabel": "",
          "dayTradeIndicator": false
        },
        "simplifiedMarginDetail": {
          "netMarketValue”:2250.00,”cashAndCredits”:500.00,”isMarginDebtInGoodOrder": true
        },
        "bondDetail": {},
        "additionalBalDetail": {
          "houseCallSurplusLabel": "Surplus",
          "houseCallSurplusLabelV2": "surplus",
          "exchgCallSurplusLabel": "Surplus",
          "exchgCallSurplusLabelV2": "surplus",
          "federalSpecialMemorandumAmtLabel": "SMA",
          "federalSpecialMemorandumAmtLabelV2": "SMA"
        },
        "availToTradeDetail": {
          "cashAvailForTrade”:500.00,”cashAvailForTradeChg": 0,
          "cashCmtdToOpenOrder": 0
        },
        "optionsDetail": {},
        "shortDetail": {
          "shortCreditDebitLabel": "credit/debit"
        },
        "multiMrgnAcctRelDetails": {},
        "isLimitedMgnAcct": false,
        "isPortfolioMrgnAcct": false,
        "isMrgnAcct": false,
        "isMultiMrgnAcct": false,
        "acctEqtyPct": 100,
        "acctEqtyPctV2": "100%",
        "uncollectedDeposit": 0,
        "cashMktVal”:2250.00,”cashMktValChg": 0
      },
      "annuityBalDetail": {
        "singlePremiumDeferredAnnuityDetail": {
          "withdrawBenifit": {}
        },
        "costBasisDetail": {},
        "guarntdMinimumAccumulationBenefitDetail": {},
        "guarntdMinimumWithdrawalBenefitDetail": {},
        "singlePremiumImmediateAnnuityDetail": {}
      },
      "asOfDateTime": 1680481458,
      "totalAcctVal”:2500.00,”totalAcctValChg": 0,
      "totalAcctMktVal”:2250.00,”totalAcctMktValChgAmt": 0,
      "totalAcctMktValChgPct": 0,
      "formattedAsOfDateTime": "04/02/2023 8:30 PM ET"
    },
    "acctFeatureDetail": {
      "optionDetail": {
        "isOptionLevel2": false,
        "isOptionEstb": false
      },
      "hasMsla": false,
      "isMarginAgreementSigned": false,
      "isMarginDebtProtection": false
    },
    "nasdaqInd": true,
    "config": {
      "isProcessMissingFields": true,
      "missedFieldValue": "$0.00"
    },
    "isMarginApplnEligible": false
  }
}
```
