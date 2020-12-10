# UpdatePsuAuthenticationResponse
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**chosenScaMethod** | [**authenticationObject**](authenticationObject.md) |  | [optional] [default to null]
**challengeData** | [**challengeData**](challengeData.md) |  | [optional] [default to null]
**scaMethods** | [**List**](authenticationObject.md) | This data element might be contained, if SCA is required and if the PSU has a choice between different authentication methods.  Depending on the risk management of the ASPSP this choice might be offered before or after the PSU has been identified with the first relevant factor, or if an access token is transported.  If this data element is contained, then there is also an hyperlink of type &#39;startAuthorisationWithAuthenticationMethodSelection&#39; contained in the response body.  These methods shall be presented towards the PSU for selection by the TPP.  | [optional] [default to null]
**\_links** | [**_linksUpdatePsuAuthentication**](_linksUpdatePsuAuthentication.md) |  | [optional] [default to null]
**scaStatus** | [**scaStatus**](scaStatus.md) |  | [default to null]
**psuMessage** | [**String**](string.md) | Text to be displayed to the PSU | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

