# CardAccountDetails
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**resourceId** | [**String**](string.md) | This is the data element to be used in the path when retrieving data from a dedicated account. This shall be filled, if addressable resource are created by the ASPSP on the /card-accounts endpoint.  | [optional] [default to null]
**maskedPan** | [**String**](string.md) | Masked Primary Account Number  | [default to null]
**currency** | [**String**](string.md) | ISO 4217 Alpha 3 currency code  | [default to null]
**name** | [**String**](string.md) | Name of the account given by the bank or the PSU in online-banking. | [optional] [default to null]
**product** | [**String**](string.md) | Product name of the bank for this account, proprietary definition. | [optional] [default to null]
**status** | [**accountStatus**](accountStatus.md) |  | [optional] [default to null]
**usage** | [**String**](string.md) | Specifies the usage of the account   * PRIV: private personal account   * ORGA: professional account  | [optional] [default to null]
**details** | [**String**](string.md) | Specifications that might be provided by the ASPSP   - characteristics of the account   - characteristics of the relevant card  | [optional] [default to null]
**creditLimit** | [**amount**](amount.md) |  | [optional] [default to null]
**balances** | [**List**](balance.md) | A list of balances regarding this account, e.g. the current balance, the last booked balance. The list might be restricted to the current balance.  | [optional] [default to null]
**\_links** | [**_linksAccountDetails**](_linksAccountDetails.md) |  | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

