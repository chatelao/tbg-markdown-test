# AccountAccess
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**accounts** | [**List**](accountReference16-CH.md) | Is asking for detailed account information.  If the array is empty, the TPP is asking for an accessible account list. This may be restricted in a PSU/ASPSP authorization dialogue. If the array is empty, also the arrays for balances or transactions shall be empty, if used.  | [optional] [default to null]
**balances** | [**List**](accountReference16-CH.md) | Is asking for balances of the addressed accounts.  If the array is empty, the TPP is asking for the balances of all accessible account lists. This may be restricted in a PSU/ASPSP authorization dialogue. If the array is empty, also the arrays for accounts or transactions shall be empty, if used.  | [optional] [default to null]
**transactions** | [**List**](accountReference16-CH.md) | Is asking for transactions of the addressed accounts.  If the array is empty, the TPP is asking for the transactions of all accessible account lists. This may be restricted in a PSU/ASPSP authorization dialogue. If the array is empty, also the arrays for accounts or balances shall be empty, if used.  | [optional] [default to null]
**availableAccounts** | [**String**](string.md) | Optional if supported by API provider.  Only the value \&quot;allAccounts\&quot; is admitted.  | [optional] [default to null]
**availableAccountsWithBalance** | [**String**](string.md) | Optional if supported by API provider. Only the value \&quot;allAccounts\&quot; is admitted.  | [optional] [default to null]
**allPsd2** | [**String**](string.md) | Optional if supported by API provider.  Only the value \&quot;allAccounts\&quot; is admitted.  | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

