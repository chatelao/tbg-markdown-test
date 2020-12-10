# ConsentInformationResponse200Json
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**access** | [**accountAccess**](accountAccess.md) |  | [default to null]
**recurringIndicator** | [**Boolean**](boolean.md) | \&quot;true\&quot;, if the consent is for recurring access to the account data.  \&quot;false\&quot;, if the consent is for one access to the account data.  | [default to null]
**validUntil** | [**date**](date.md) | This parameter is requesting a valid until date for the requested consent. The content is the local ASPSP date in ISO-Date Format, e.g. 2017-10-30.  Future dates might get adjusted by ASPSP.  If a maximal available date is requested, a date in far future is to be used: \&quot;9999-12-31\&quot;.  In both cases the consent object to be retrieved by the GET Consent Request will contain the adjusted date.  | [default to null]
**frequencyPerDay** | [**Integer**](integer.md) | This field indicates the requested maximum frequency for an access without PSU involvement per day. For a one-off access, this attribute is set to \&quot;1\&quot;.  The frequency needs to be greater equal to one.  If not otherwise agreed bilaterally between TPP and ASPSP, the frequency is less equal to 4.  | [default to null]
**lastActionDate** | [**date**](date.md) | This date is containing the date of the last action on the consent object either through the XS2A interface or the PSU/ASPSP interface having an impact on the status.  | [default to null]
**consentStatus** | [**consentStatus**](consentStatus.md) |  | [default to null]
**\_links** | [**_linksGetConsent**](_linksGetConsent.md) |  | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

