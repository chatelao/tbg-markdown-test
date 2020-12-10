# AccountDetails
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**resourceId** | [**String**](string.md) | This shall be filled, if addressable resource are created by the ASPSP on the /accounts or /card-accounts endpoint. | [optional] [default to null]
**iban** | [**String**](string.md) | IBAN of an account | [optional] [default to null]
**bban** | [**String**](string.md) | Basic Bank Account Number (BBAN) Identifier  This data element can be used in the body of the Consent Request   Message for retrieving Account access Consent from this Account. This   data elements is used for payment Accounts which have no IBAN.   ISO20022: Basic Bank Account Number (BBAN).    Identifier used nationally by financial institutions, i.e., in individual countries,   generally as part of a National Account Numbering Scheme(s),   which uniquely identifies the account of a customer.  | [optional] [default to null]
**msisdn** | [**String**](string.md) | Mobile phone number. | [optional] [default to null]
**currency** | [**String**](string.md) | ISO 4217 Alpha 3 currency code  | [default to null]
**name** | [**String**](string.md) | Name of the account given by the bank or the PSU in online-banking. | [optional] [default to null]
**product** | [**String**](string.md) | Product name of the bank for this account, proprietary definition. | [optional] [default to null]
**cashAccountType** | [**String**](string.md) | ExternalCashAccountType1Code from ISO 20022.  | [optional] [default to null]
**status** | [**accountStatus**](accountStatus.md) |  | [optional] [default to null]
**bic** | [**String**](string.md) | BICFI  | [optional] [default to null]
**linkedAccounts** | [**String**](string.md) | Case of a set of pending card transactions, the APSP will provide the relevant cash account the card is set up on. | [optional] [default to null]
**usage** | [**String**](string.md) | Specifies the usage of the account   * PRIV: private personal account   * ORGA: professional account  | [optional] [default to null]
**details** | [**String**](string.md) | Specifications that might be provided by the ASPSP   - characteristics of the account   - characteristics of the relevant card  | [optional] [default to null]
**balances** | [**List**](balance.md) | A list of balances regarding this account, e.g. the current balance, the last booked balance. The list might be restricted to the current balance.  | [optional] [default to null]
**\_links** | [**_linksAccountDetails**](_linksAccountDetails.md) |  | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

