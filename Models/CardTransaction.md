# CardTransaction
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**cardTransactionId** | [**String**](string.md) | Unique end to end identity. | [optional] [default to null]
**terminalId** | [**String**](string.md) | Identification of the Terminal, where the card has been used. | [optional] [default to null]
**transactionDate** | [**date**](date.md) | Date of the actual card transaction | [optional] [default to null]
**bookingDate** | [**date**](date.md) | The Date when an entry is posted to an account on the ASPSPs books.  | [optional] [default to null]
**transactionAmount** | [**amount**](amount.md) |  | [default to null]
**currencyExchange** | [**List**](reportExchangeRate.md) | Array of exchange rates | [optional] [default to null]
**originalAmount** | [**amount**](amount.md) |  | [optional] [default to null]
**markupFee** | [**amount**](amount.md) |  | [optional] [default to null]
**markupFeePercentage** | [**String**](string.md) |  | [optional] [default to null]
**cardAcceptorId** | [**String**](string.md) |  | [optional] [default to null]
**cardAcceptorAddress** | [**address**](address.md) |  | [optional] [default to null]
**merchantCategoryCode** | [**String**](string.md) | Merchant category code | [optional] [default to null]
**maskedPAN** | [**String**](string.md) | Masked Primary Account Number  | [optional] [default to null]
**transactionDetails** | [**String**](string.md) |  | [optional] [default to null]
**invoiced** | [**Boolean**](boolean.md) |  | [optional] [default to null]
**proprietaryBankTransactionCode** | [**String**](string.md) | Proprietary bank transaction code as used within a community or within an ASPSP e.g. for MT94x based transaction reports.  | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

