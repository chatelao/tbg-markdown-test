# BulkPaymentInitiationWithStatusResponse
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**batchBookingPreferred** | [**Boolean**](boolean.md) | If this element equals &#39;true&#39;, the PSU prefers only one booking entry. If this element equals &#39;false&#39;, the PSU prefers individual booking of all contained individual transactions.  The ASPSP will follow this preference according to contracts agreed on with the PSU.  | [optional] [default to null]
**requestedExecutionDate** | [**date**](date.md) |  | [optional] [default to null]
**debtorAccount** | [**accountReference16-CH**](accountReference16-CH.md) |  | [default to null]
**payments** | [**List**](paymentInitiationBulkElement_json.md) | A list of generic JSON bodies payment initations for bulk payments via JSON.  Note: Some fields from single payments do not occcur in a bulk payment element  | [default to null]
**transactionStatus** | [**transactionStatus**](transactionStatus.md) |  | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

