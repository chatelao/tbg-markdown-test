# ConsentsResponse201
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**consentStatus** | [**consentStatus**](consentStatus.md) |  | [default to null]
**consentId** | [**String**](string.md) | ID of the corresponding consent object as returned by an Account Information Consent Request.  | [default to null]
**scaMethods** | [**List**](authenticationObject.md) | This data element might be contained, if SCA is required and if the PSU has a choice between different authentication methods.  Depending on the risk management of the ASPSP this choice might be offered before or after the PSU has been identified with the first relevant factor, or if an access token is transported.  If this data element is contained, then there is also an hyperlink of type &#39;startAuthorisationWithAuthenticationMethodSelection&#39; contained in the response body.  These methods shall be presented towards the PSU for selection by the TPP.  | [optional] [default to null]
**chosenScaMethod** | [**authenticationObject**](authenticationObject.md) |  | [optional] [default to null]
**challengeData** | [**challengeData**](challengeData.md) |  | [optional] [default to null]
**\_links** | [**_linksConsents**](_linksConsents.md) |  | [default to null]
**message** | [**String**](string.md) | Text to be displayed to the PSU, e.g. in a Decoupled SCA Approach. | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

