# Balance
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**balanceAmount** | [**amount**](amount.md) |  | [default to null]
**balanceType** | [**balanceType**](balanceType.md) |  | [default to null]
**creditLimitIncluded** | [**Boolean**](boolean.md) | A flag indicating if the credit limit of the corresponding account is included in the calculation of the balance, where applicable.  | [optional] [default to null]
**lastChangeDateTime** | [**Date**](DateTime.md) | This data element might be used to indicate e.g. with the expected or booked balance that no action is known on the account, which is not yet booked.  | [optional] [default to null]
**referenceDate** | [**date**](date.md) | Reference date of the balance | [optional] [default to null]
**lastCommittedTransaction** | [**String**](string.md) | \&quot;entryReference\&quot; of the last commited transaction to support the TPP in identifying whether all PSU transactions are already known.  | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

