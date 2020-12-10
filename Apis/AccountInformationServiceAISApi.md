# AccountInformationServiceAISApi

All URIs are relative to *https://api.dev.openbankingproject.ch*

Method | HTTP request | Description
------------- | ------------- | -------------
[**createConsent**](AccountInformationServiceAISApi.md#createConsent) | **POST** /v1/consents | Create consent
[**deleteConsent**](AccountInformationServiceAISApi.md#deleteConsent) | **DELETE** /v1/consents/{consentId} | Delete Consent
[**getAccountList**](AccountInformationServiceAISApi.md#getAccountList) | **GET** /v1/accounts | Read Account List
[**getBalances**](AccountInformationServiceAISApi.md#getBalances) | **GET** /v1/accounts/{account-id}/balances | Read Balance
[**getConsentAuthorisation**](AccountInformationServiceAISApi.md#getConsentAuthorisation) | **GET** /v1/consents/{consentId}/authorisations | Get Consent Authorisation Sub-Resources Request
[**getConsentInformation**](AccountInformationServiceAISApi.md#getConsentInformation) | **GET** /v1/consents/{consentId} | Get Consent Request
[**getConsentScaStatus**](AccountInformationServiceAISApi.md#getConsentScaStatus) | **GET** /v1/consents/{consentId}/authorisations/{authorisationId} | Read the SCA status of the consent authorisation.
[**getConsentStatus**](AccountInformationServiceAISApi.md#getConsentStatus) | **GET** /v1/consents/{consentId}/status | Consent status request
[**getTransactionDetails**](AccountInformationServiceAISApi.md#getTransactionDetails) | **GET** /v1/accounts/{account-id}/transactions/{transactionId} | Read Transaction Details
[**getTransactionList**](AccountInformationServiceAISApi.md#getTransactionList) | **GET** /v1/accounts/{account-id}/transactions | Read transaction list of an account
[**readAccountDetails**](AccountInformationServiceAISApi.md#readAccountDetails) | **GET** /v1/accounts/{account-id} | Read Account Details
[**startConsentAuthorisation**](AccountInformationServiceAISApi.md#startConsentAuthorisation) | **POST** /v1/consents/{consentId}/authorisations | Start the authorisation process for a consent
[**updateConsentsPsuData**](AccountInformationServiceAISApi.md#updateConsentsPsuData) | **PUT** /v1/consents/{consentId}/authorisations/{authorisationId} | Update PSU Data for consents


<a name="createConsent"></a>
# **createConsent**
> consentsResponse-201 createConsent(X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-ID, PSU-ID-Type, PSU-Corporate-ID, PSU-Corporate-ID-Type, TPP-Redirect-Preferred, TPP-Redirect-URI, TPP-Nok-Redirect-URI, TPP-Explicit-Authorisation-Preferred, TPP-Notification-URI, TPP-Notification-Content-Preferred, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location, Consents)

Create consent

    This method create a consent resource, defining access rights to dedicated accounts of a given PSU-ID. These accounts are addressed explicitly in the method as parameters as a core function.  **Side Effects** When this Consent Request is a request where the \&quot;recurringIndicator\&quot; equals \&quot;true\&quot;, and if it exists already a former consent for recurring access on account information for the addressed PSU, then the former consent automatically expires as soon as the new consent request is authorised by the PSU.  Optional Extension: As an option, an ASPSP might optionally accept a specific access right on the access on all related services for all available accounts.  As another option an ASPSP might optionally also accept a command, where only access rights are inserted without mentioning the addressed account. The relation to accounts is then handled afterwards between PSU and ASPSP. This option is not supported for the Embedded SCA Approach. As a last option, an ASPSP might in addition accept a command with access rights   * to see the list of available payment accounts or   * to see the list of available payment accounts with balances. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-ID** | **String**| Client ID of the PSU in the ASPSP client interface.  Might be mandated in the ASPSP&#39;s documentation.  It might be contained even if an OAuth2 based authentication was performed in a pre-step or an OAuth2 based SCA was performed in an preceding AIS service in the same session. In this case the ASPSP might check whether PSU-ID and token match, according to ASPSP documentation.  | [optional] [default to null]
 **PSU-ID-Type** | **String**| Type of the PSU-ID, needed in scenarios where PSUs have several PSU-IDs as access possibility.  In this case, the mean and use are then defined in the ASPSP&#39;s documentation.  | [optional] [default to null]
 **PSU-Corporate-ID** | **String**| Might be mandated in the ASPSP&#39;s documentation. Only used in a corporate context.  | [optional] [default to null]
 **PSU-Corporate-ID-Type** | **String**| Might be mandated in the ASPSP&#39;s documentation. Only used in a corporate context.  | [optional] [default to null]
 **TPP-Redirect-Preferred** | **String**| If it equals \&quot;true\&quot;, the TPP prefers a redirect over an embedded SCA approach. If it equals \&quot;false\&quot;, the TPP prefers not to be redirected for SCA. The ASPSP will then choose between the Embedded or the Decoupled SCA approach, depending on the choice of the SCA procedure by the TPP/PSU. If the parameter is not used, the ASPSP will choose the SCA approach to be applied depending on the SCA method chosen by the TPP/PSU.  | [optional] [default to null] [enum: true, false]
 **TPP-Redirect-URI** | **URI**| URI of the TPP, where the transaction flow shall be redirected to after a Redirect.  Mandated for the Redirect SCA Approach, specifically when TPP-Redirect-Preferred equals \&quot;true\&quot;. It is recommended to always use this header field.  **Remark for Future:** This field might be changed to mandatory in the next version of the specification.  | [optional] [default to null]
 **TPP-Nok-Redirect-URI** | **URI**| If this URI is contained, the TPP is asking to redirect the transaction flow to this address instead of the TPP-Redirect-URI in case of a negative result of the redirect SCA method. This might be ignored by the ASPSP.  | [optional] [default to null]
 **TPP-Explicit-Authorisation-Preferred** | **String**| If it equals \&quot;true\&quot;, the TPP prefers to start the authorisation process separately, e.g. because of the usage of a signing basket. This preference might be ignored by the ASPSP, if a signing basket is not supported as functionality.  If it equals \&quot;false\&quot; or if the parameter is not used, there is no preference of the TPP. This especially indicates that the TPP assumes a direct authorisation of the transaction in the next step, without using a signing basket.  | [optional] [default to null] [enum: true, false]
 **TPP-Notification-URI** | **String**| URI for the Endpoint of the TPP-API to which the status of the payment initiation should be sent. This header field may by ignored by the ASPSP.  For security reasons, it shall be ensured that the TPP-Notification-URI as introduced above is secured by the TPP eIDAS QWAC used for identification of the TPP. The following applies:  URIs which are provided by TPPs in TPP-Notification-URI shall comply with the domain secured by the eIDAS QWAC certificate of the TPP in the field CN or SubjectAltName of the certificate. Please note that in case of example-TPP.com as certificate entry TPP- Notification-URI like www.example-TPP.com/xs2a-client/v1/ASPSPidentifcation/mytransaction- id/notifications or notifications.example-TPP.com/xs2a-client/v1/ASPSPidentifcation/mytransaction- id/notifications would be compliant.  Wildcard definitions shall be taken into account for compliance checks by the ASPSP.  ASPSPs may respond with ASPSP-Notification-Support set to false, if the provided URIs do not comply.  | [optional] [default to null]
 **TPP-Notification-Content-Preferred** | **String**| The string has the form  status&#x3D;X1, ..., Xn  where Xi is one of the constants SCA, PROCESS, LAST and where constants are not repeated. The usage of the constants supports the of following semantics:    SCA: A notification on every change of the scaStatus attribute for all related authorisation processes is preferred by the TPP.    PROCESS: A notification on all changes of consentStatus or transactionStatus attributes is preferred by the TPP.   LAST: Only a notification on the last consentStatus or transactionStatus as available in the XS2A interface is preferred by the TPP.  This header field may be ignored, if the ASPSP does not support resource notification services for the related TPP.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding HTTP request IP Address field between PSU and TPP. It shall be contained if and only if this request was actively initiated by the PSU.  | [optional] [default to null]
 **PSU-IP-Port** | **String**| The forwarded IP Port header field consists of the corresponding HTTP request IP Port field between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Charset** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Encoding** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Language** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-User-Agent** | **String**| The forwarded Agent header field of the HTTP request between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Http-Method** | **String**| HTTP method used at the PSU ? TPP interface, if available. Valid values are: * GET * POST * PUT * PATCH * DELETE  | [optional] [default to null] [enum: GET, POST, PUT, PATCH, DELETE]
 **PSU-Device-ID** | **String**| UUID (Universally Unique Identifier) for a device, which is used by the PSU, if available. UUID identifies either a device or a device dependant application installation. In case of an installation identification this ID need to be unaltered until removal from device.  | [optional] [default to null]
 **PSU-Geo-Location** | **String**| The forwarded Geo Location of the corresponding http request between PSU and TPP if available.  | [optional] [default to null]
 **Consents** | [**Consents**](../Models/Consents.md)| Requestbody for a consents request  | [optional]

### Return type

[**consentsResponse-201**](../Models/consentsResponse-201.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json, application/problem+json

<a name="deleteConsent"></a>
# **deleteConsent**
> deleteConsent(consentId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Delete Consent

    The TPP can delete an account information consent object if needed.

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **consentId** | **String**| ID of the corresponding consent object as returned by an Account Information Consent Request.  | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding HTTP request IP Address field between PSU and TPP. It shall be contained if and only if this request was actively initiated by the PSU.  | [optional] [default to null]
 **PSU-IP-Port** | **String**| The forwarded IP Port header field consists of the corresponding HTTP request IP Port field between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Charset** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Encoding** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Language** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-User-Agent** | **String**| The forwarded Agent header field of the HTTP request between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Http-Method** | **String**| HTTP method used at the PSU ? TPP interface, if available. Valid values are: * GET * POST * PUT * PATCH * DELETE  | [optional] [default to null] [enum: GET, POST, PUT, PATCH, DELETE]
 **PSU-Device-ID** | **String**| UUID (Universally Unique Identifier) for a device, which is used by the PSU, if available. UUID identifies either a device or a device dependant application installation. In case of an installation identification this ID need to be unaltered until removal from device.  | [optional] [default to null]
 **PSU-Geo-Location** | **String**| The forwarded Geo Location of the corresponding http request between PSU and TPP if available.  | [optional] [default to null]

### Return type

null (empty response body)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/problem+json

<a name="getAccountList"></a>
# **getAccountList**
> accountList getAccountList(X-Request-ID, Consent-ID, withBalance, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Read Account List

    Read the identifiers of the available payment account together with booking balance information, depending on the consent granted.  It is assumed that a consent of the PSU to this access is already given and stored on the ASPSP system. The addressed list of accounts depends then on the PSU ID and the stored consent addressed by consentId, respectively the OAuth2 access token.  Returns all identifiers of the accounts, to which an account access has been granted to through the /consents endpoint by the PSU. In addition, relevant information about the accounts and hyperlinks to corresponding account information resources are provided if a related consent has been already granted.  Remark: Note that the /consents endpoint optionally offers to grant an access on all available payment accounts of a PSU. In this case, this endpoint will deliver the information about all available payment accounts of the PSU at this ASPSP. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Consent-ID** | **String**| This then contains the consentId of the related AIS consent, which was performed prior to this payment initiation.  | [default to null]
 **withBalance** | **Boolean**| If contained, this function reads the list of accessible payment accounts including the booking balance, if granted by the PSU in the related consent and available by the ASPSP. This parameter might be ignored by the ASPSP.  | [optional] [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding HTTP request IP Address field between PSU and TPP. It shall be contained if and only if this request was actively initiated by the PSU.  | [optional] [default to null]
 **PSU-IP-Port** | **String**| The forwarded IP Port header field consists of the corresponding HTTP request IP Port field between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Charset** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Encoding** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Language** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-User-Agent** | **String**| The forwarded Agent header field of the HTTP request between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Http-Method** | **String**| HTTP method used at the PSU ? TPP interface, if available. Valid values are: * GET * POST * PUT * PATCH * DELETE  | [optional] [default to null] [enum: GET, POST, PUT, PATCH, DELETE]
 **PSU-Device-ID** | **String**| UUID (Universally Unique Identifier) for a device, which is used by the PSU, if available. UUID identifies either a device or a device dependant application installation. In case of an installation identification this ID need to be unaltered until removal from device.  | [optional] [default to null]
 **PSU-Geo-Location** | **String**| The forwarded Geo Location of the corresponding http request between PSU and TPP if available.  | [optional] [default to null]

### Return type

[**accountList**](../Models/accountList.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/problem+json

<a name="getBalances"></a>
# **getBalances**
> readAccountBalanceResponse-200 getBalances(account-id, X-Request-ID, Consent-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Read Balance

    Reads account data from a given account addressed by \&quot;account-id\&quot;.  **Remark:** This account-id can be a tokenised identification due to data protection reason since the path information might be logged on intermediary servers within the ASPSP sphere. This account-id then can be retrieved by the \&quot;GET Account List\&quot; call.  The account-id is constant at least throughout the lifecycle of a given consent. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **account-id** | **String**| This identification is denoting the addressed account. The account-id is retrieved by using a \&quot;Read Account List\&quot; call. The account-id is the \&quot;id\&quot; attribute of the account structure. Its value is constant at least throughout the lifecycle of a given consent.  | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Consent-ID** | **String**| This then contains the consentId of the related AIS consent, which was performed prior to this payment initiation.  | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding HTTP request IP Address field between PSU and TPP. It shall be contained if and only if this request was actively initiated by the PSU.  | [optional] [default to null]
 **PSU-IP-Port** | **String**| The forwarded IP Port header field consists of the corresponding HTTP request IP Port field between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Charset** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Encoding** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Language** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-User-Agent** | **String**| The forwarded Agent header field of the HTTP request between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Http-Method** | **String**| HTTP method used at the PSU ? TPP interface, if available. Valid values are: * GET * POST * PUT * PATCH * DELETE  | [optional] [default to null] [enum: GET, POST, PUT, PATCH, DELETE]
 **PSU-Device-ID** | **String**| UUID (Universally Unique Identifier) for a device, which is used by the PSU, if available. UUID identifies either a device or a device dependant application installation. In case of an installation identification this ID need to be unaltered until removal from device.  | [optional] [default to null]
 **PSU-Geo-Location** | **String**| The forwarded Geo Location of the corresponding http request between PSU and TPP if available.  | [optional] [default to null]

### Return type

[**readAccountBalanceResponse-200**](../Models/readAccountBalanceResponse-200.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/problem+json

<a name="getConsentAuthorisation"></a>
# **getConsentAuthorisation**
> authorisations getConsentAuthorisation(consentId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Get Consent Authorisation Sub-Resources Request

    Return a list of all authorisation subresources IDs which have been created.  This function returns an array of hyperlinks to all generated authorisation sub-resources. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **consentId** | **String**| ID of the corresponding consent object as returned by an Account Information Consent Request.  | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding HTTP request IP Address field between PSU and TPP. It shall be contained if and only if this request was actively initiated by the PSU.  | [optional] [default to null]
 **PSU-IP-Port** | **String**| The forwarded IP Port header field consists of the corresponding HTTP request IP Port field between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Charset** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Encoding** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Language** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-User-Agent** | **String**| The forwarded Agent header field of the HTTP request between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Http-Method** | **String**| HTTP method used at the PSU ? TPP interface, if available. Valid values are: * GET * POST * PUT * PATCH * DELETE  | [optional] [default to null] [enum: GET, POST, PUT, PATCH, DELETE]
 **PSU-Device-ID** | **String**| UUID (Universally Unique Identifier) for a device, which is used by the PSU, if available. UUID identifies either a device or a device dependant application installation. In case of an installation identification this ID need to be unaltered until removal from device.  | [optional] [default to null]
 **PSU-Geo-Location** | **String**| The forwarded Geo Location of the corresponding http request between PSU and TPP if available.  | [optional] [default to null]

### Return type

[**authorisations**](../Models/authorisations.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/problem+json

<a name="getConsentInformation"></a>
# **getConsentInformation**
> consentInformationResponse-200_json getConsentInformation(consentId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Get Consent Request

    Returns the content of an account information consent object. This is returning the data for the TPP especially in cases, where the consent was directly managed between ASPSP and PSU e.g. in a re-direct SCA Approach. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **consentId** | **String**| ID of the corresponding consent object as returned by an Account Information Consent Request.  | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding HTTP request IP Address field between PSU and TPP. It shall be contained if and only if this request was actively initiated by the PSU.  | [optional] [default to null]
 **PSU-IP-Port** | **String**| The forwarded IP Port header field consists of the corresponding HTTP request IP Port field between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Charset** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Encoding** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Language** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-User-Agent** | **String**| The forwarded Agent header field of the HTTP request between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Http-Method** | **String**| HTTP method used at the PSU ? TPP interface, if available. Valid values are: * GET * POST * PUT * PATCH * DELETE  | [optional] [default to null] [enum: GET, POST, PUT, PATCH, DELETE]
 **PSU-Device-ID** | **String**| UUID (Universally Unique Identifier) for a device, which is used by the PSU, if available. UUID identifies either a device or a device dependant application installation. In case of an installation identification this ID need to be unaltered until removal from device.  | [optional] [default to null]
 **PSU-Geo-Location** | **String**| The forwarded Geo Location of the corresponding http request between PSU and TPP if available.  | [optional] [default to null]

### Return type

[**consentInformationResponse-200_json**](../Models/consentInformationResponse-200_json.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/problem+json

<a name="getConsentScaStatus"></a>
# **getConsentScaStatus**
> scaStatusResponse getConsentScaStatus(consentId, authorisationId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Read the SCA status of the consent authorisation.

    This method returns the SCA status of a consent initiation&#39;s authorisation sub-resource. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **consentId** | **String**| ID of the corresponding consent object as returned by an Account Information Consent Request.  | [default to null]
 **authorisationId** | **String**| Resource identification of the related SCA. | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding HTTP request IP Address field between PSU and TPP. It shall be contained if and only if this request was actively initiated by the PSU.  | [optional] [default to null]
 **PSU-IP-Port** | **String**| The forwarded IP Port header field consists of the corresponding HTTP request IP Port field between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Charset** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Encoding** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Language** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-User-Agent** | **String**| The forwarded Agent header field of the HTTP request between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Http-Method** | **String**| HTTP method used at the PSU ? TPP interface, if available. Valid values are: * GET * POST * PUT * PATCH * DELETE  | [optional] [default to null] [enum: GET, POST, PUT, PATCH, DELETE]
 **PSU-Device-ID** | **String**| UUID (Universally Unique Identifier) for a device, which is used by the PSU, if available. UUID identifies either a device or a device dependant application installation. In case of an installation identification this ID need to be unaltered until removal from device.  | [optional] [default to null]
 **PSU-Geo-Location** | **String**| The forwarded Geo Location of the corresponding http request between PSU and TPP if available.  | [optional] [default to null]

### Return type

[**scaStatusResponse**](../Models/scaStatusResponse.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/problem+json

<a name="getConsentStatus"></a>
# **getConsentStatus**
> consentStatusResponse-200 getConsentStatus(consentId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Consent status request

    Read the status of an account information consent resource.

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **consentId** | **String**| ID of the corresponding consent object as returned by an Account Information Consent Request.  | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding HTTP request IP Address field between PSU and TPP. It shall be contained if and only if this request was actively initiated by the PSU.  | [optional] [default to null]
 **PSU-IP-Port** | **String**| The forwarded IP Port header field consists of the corresponding HTTP request IP Port field between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Charset** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Encoding** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Language** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-User-Agent** | **String**| The forwarded Agent header field of the HTTP request between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Http-Method** | **String**| HTTP method used at the PSU ? TPP interface, if available. Valid values are: * GET * POST * PUT * PATCH * DELETE  | [optional] [default to null] [enum: GET, POST, PUT, PATCH, DELETE]
 **PSU-Device-ID** | **String**| UUID (Universally Unique Identifier) for a device, which is used by the PSU, if available. UUID identifies either a device or a device dependant application installation. In case of an installation identification this ID need to be unaltered until removal from device.  | [optional] [default to null]
 **PSU-Geo-Location** | **String**| The forwarded Geo Location of the corresponding http request between PSU and TPP if available.  | [optional] [default to null]

### Return type

[**consentStatusResponse-200**](../Models/consentStatusResponse-200.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/problem+json

<a name="getTransactionDetails"></a>
# **getTransactionDetails**
> transactionDetails getTransactionDetails(account-id, transactionId, X-Request-ID, Consent-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Read Transaction Details

    Reads transaction details from a given transaction addressed by \&quot;transactionId\&quot; on a given account addressed by \&quot;account-id\&quot;. This call is only available on transactions as reported in a JSON format.  **Remark:** Please note that the PATH might be already given in detail by the corresponding entry of the response of the \&quot;Read Transaction List\&quot; call within the _links subfield. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **account-id** | **String**| This identification is denoting the addressed account. The account-id is retrieved by using a \&quot;Read Account List\&quot; call. The account-id is the \&quot;id\&quot; attribute of the account structure. Its value is constant at least throughout the lifecycle of a given consent.  | [default to null]
 **transactionId** | **String**| This identification is given by the attribute transactionId of the corresponding entry of a transaction list.  | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Consent-ID** | **String**| This then contains the consentId of the related AIS consent, which was performed prior to this payment initiation.  | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding HTTP request IP Address field between PSU and TPP. It shall be contained if and only if this request was actively initiated by the PSU.  | [optional] [default to null]
 **PSU-IP-Port** | **String**| The forwarded IP Port header field consists of the corresponding HTTP request IP Port field between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Charset** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Encoding** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Language** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-User-Agent** | **String**| The forwarded Agent header field of the HTTP request between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Http-Method** | **String**| HTTP method used at the PSU ? TPP interface, if available. Valid values are: * GET * POST * PUT * PATCH * DELETE  | [optional] [default to null] [enum: GET, POST, PUT, PATCH, DELETE]
 **PSU-Device-ID** | **String**| UUID (Universally Unique Identifier) for a device, which is used by the PSU, if available. UUID identifies either a device or a device dependant application installation. In case of an installation identification this ID need to be unaltered until removal from device.  | [optional] [default to null]
 **PSU-Geo-Location** | **String**| The forwarded Geo Location of the corresponding http request between PSU and TPP if available.  | [optional] [default to null]

### Return type

[**transactionDetails**](../Models/transactionDetails.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/problem+json

<a name="getTransactionList"></a>
# **getTransactionList**
> transactionsResponse-200_json getTransactionList(account-id, bookingStatus, X-Request-ID, Consent-ID, dateFrom, dateTo, entryReferenceFrom, deltaList, withBalance, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Read transaction list of an account

    Read transaction reports or transaction lists of a given account ddressed by \&quot;account-id\&quot;, depending on the steering parameter \&quot;bookingStatus\&quot; together with balances.  For a given account, additional parameters are e.g. the attributes \&quot;dateFrom\&quot; and \&quot;dateTo\&quot;. The ASPSP might add balance information, if transaction lists without balances are not supported. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **account-id** | **String**| This identification is denoting the addressed account. The account-id is retrieved by using a \&quot;Read Account List\&quot; call. The account-id is the \&quot;id\&quot; attribute of the account structure. Its value is constant at least throughout the lifecycle of a given consent.  | [default to null]
 **bookingStatus** | **String**| Permitted codes are   * \&quot;booked\&quot;,   * \&quot;pending\&quot; and   * \&quot;both\&quot; \&quot;booked\&quot; shall be supported by the ASPSP. To support the \&quot;pending\&quot; and \&quot;both\&quot; feature is optional for the ASPSP, Error code if not supported in the online banking frontend  | [default to null] [enum: booked, pending, both]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Consent-ID** | **String**| This then contains the consentId of the related AIS consent, which was performed prior to this payment initiation.  | [default to null]
 **dateFrom** | **date**| Conditional: Starting date (inclusive the date dateFrom) of the transaction list, mandated if no delta access is required.  For booked transactions, the relevant date is the booking date.  For pending transactions, the relevant date is the entry date, which may not be transparent neither in this API nor other channels of the ASPSP.  | [optional] [default to null]
 **dateTo** | **date**| End date (inclusive the data dateTo) of the transaction list, default is \&quot;now\&quot; if not given.  Might be ignored if a delta function is used.  For booked transactions, the relevant date is the booking date.  For pending transactions, the relevant date is the entry date, which may not be transparent neither in this API nor other channels of the ASPSP.  | [optional] [default to null]
 **entryReferenceFrom** | **String**| This data attribute is indicating that the AISP is in favour to get all transactions after the transaction with identification entryReferenceFrom alternatively to the above defined period. This is a implementation of a delta access. If this data element is contained, the entries \&quot;dateFrom\&quot; and \&quot;dateTo\&quot; might be ignored by the ASPSP if a delta report is supported.  Optional if supported by API provider.  | [optional] [default to null]
 **deltaList** | **Boolean**| This data attribute is indicating that the AISP is in favour to get all transactions after the last report access for this PSU on the addressed account. This is another implementation of a delta access-report. This delta indicator might be rejected by the ASPSP if this function is not supported. Optional if supported by API provider | [optional] [default to null]
 **withBalance** | **Boolean**| If contained, this function reads the list of accessible payment accounts including the booking balance, if granted by the PSU in the related consent and available by the ASPSP. This parameter might be ignored by the ASPSP.  | [optional] [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding HTTP request IP Address field between PSU and TPP. It shall be contained if and only if this request was actively initiated by the PSU.  | [optional] [default to null]
 **PSU-IP-Port** | **String**| The forwarded IP Port header field consists of the corresponding HTTP request IP Port field between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Charset** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Encoding** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Language** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-User-Agent** | **String**| The forwarded Agent header field of the HTTP request between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Http-Method** | **String**| HTTP method used at the PSU ? TPP interface, if available. Valid values are: * GET * POST * PUT * PATCH * DELETE  | [optional] [default to null] [enum: GET, POST, PUT, PATCH, DELETE]
 **PSU-Device-ID** | **String**| UUID (Universally Unique Identifier) for a device, which is used by the PSU, if available. UUID identifies either a device or a device dependant application installation. In case of an installation identification this ID need to be unaltered until removal from device.  | [optional] [default to null]
 **PSU-Geo-Location** | **String**| The forwarded Geo Location of the corresponding http request between PSU and TPP if available.  | [optional] [default to null]

### Return type

[**transactionsResponse-200_json**](../Models/transactionsResponse-200_json.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/xml, application/text, application/problem+json

<a name="readAccountDetails"></a>
# **readAccountDetails**
> accountDetails readAccountDetails(account-id, X-Request-ID, Consent-ID, withBalance, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Read Account Details

    Reads details about an account, with balances where required. It is assumed that a consent of the PSU to this access is already given and stored on the ASPSP system. The addressed details of this account depends then on the stored consent addressed by consentId, respectively the OAuth2 access token.  **NOTE:** The account-id can represent a multicurrency account. In this case the currency code is set to \&quot;XXX\&quot;.  Give detailed information about the addressed account.  Give detailed information about the addressed account together with balance information 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **account-id** | **String**| This identification is denoting the addressed account. The account-id is retrieved by using a \&quot;Read Account List\&quot; call. The account-id is the \&quot;id\&quot; attribute of the account structure. Its value is constant at least throughout the lifecycle of a given consent.  | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Consent-ID** | **String**| This then contains the consentId of the related AIS consent, which was performed prior to this payment initiation.  | [default to null]
 **withBalance** | **Boolean**| If contained, this function reads the list of accessible payment accounts including the booking balance, if granted by the PSU in the related consent and available by the ASPSP. This parameter might be ignored by the ASPSP.  | [optional] [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding HTTP request IP Address field between PSU and TPP. It shall be contained if and only if this request was actively initiated by the PSU.  | [optional] [default to null]
 **PSU-IP-Port** | **String**| The forwarded IP Port header field consists of the corresponding HTTP request IP Port field between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Charset** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Encoding** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Language** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-User-Agent** | **String**| The forwarded Agent header field of the HTTP request between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Http-Method** | **String**| HTTP method used at the PSU ? TPP interface, if available. Valid values are: * GET * POST * PUT * PATCH * DELETE  | [optional] [default to null] [enum: GET, POST, PUT, PATCH, DELETE]
 **PSU-Device-ID** | **String**| UUID (Universally Unique Identifier) for a device, which is used by the PSU, if available. UUID identifies either a device or a device dependant application installation. In case of an installation identification this ID need to be unaltered until removal from device.  | [optional] [default to null]
 **PSU-Geo-Location** | **String**| The forwarded Geo Location of the corresponding http request between PSU and TPP if available.  | [optional] [default to null]

### Return type

[**accountDetails**](../Models/accountDetails.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/problem+json

<a name="startConsentAuthorisation"></a>
# **startConsentAuthorisation**
> startScaprocessResponse startConsentAuthorisation(consentId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-ID, PSU-ID-Type, PSU-Corporate-ID, PSU-Corporate-ID-Type, TPP-Redirect-Preferred, TPP-Redirect-URI, TPP-Nok-Redirect-URI, TPP-Notification-URI, TPP-Notification-Content-Preferred, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location, UNKNOWN\_BASE\_TYPE)

Start the authorisation process for a consent

    Create an authorisation sub-resource and start the authorisation process of a consent. The message might in addition transmit authentication and authorisation related data.  his method is iterated n times for a n times SCA authorisation in a corporate context, each creating an own authorisation sub-endpoint for the corresponding PSU authorising the consent.  The ASPSP might make the usage of this access method unnecessary, since the related authorisation resource will be automatically created by the ASPSP after the submission of the consent data with the first POST consents call.  The start authorisation process is a process which is needed for creating a new authorisation or cancellation sub-resource.  This applies in the following scenarios:    * The ASPSP has indicated with an &#39;startAuthorisation&#39; hyperlink in the preceding Payment     Initiation Response that an explicit start of the authorisation process is needed by the TPP.     The &#39;startAuthorisation&#39; hyperlink can transport more information about data which needs to be     uploaded by using the extended forms.     * &#39;startAuthorisationWithPsuIdentfication&#39;,     * &#39;startAuthorisationWithPsuAuthentication&#39;     * &#39;startAuthorisationWithEncryptedPsuAuthentication&#39;     * &#39;startAuthorisationWithAuthentciationMethodSelection&#39;   * The related payment initiation cannot yet be executed since a multilevel SCA is mandated.   * The ASPSP has indicated with an &#39;startAuthorisation&#39; hyperlink in the preceding     Payment Cancellation Response that an explicit start of the authorisation process is needed by the TPP.     The &#39;startAuthorisation&#39; hyperlink can transport more information about data which needs to be uploaded     by using the extended forms as indicated above.   * The related payment cancellation request cannot be applied yet since a multilevel SCA is mandate for     executing the cancellation.   * The signing basket needs to be authorised yet. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **consentId** | **String**| ID of the corresponding consent object as returned by an Account Information Consent Request.  | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-ID** | **String**| Client ID of the PSU in the ASPSP client interface.  Might be mandated in the ASPSP&#39;s documentation.  It might be contained even if an OAuth2 based authentication was performed in a pre-step or an OAuth2 based SCA was performed in an preceding AIS service in the same session. In this case the ASPSP might check whether PSU-ID and token match, according to ASPSP documentation.  | [optional] [default to null]
 **PSU-ID-Type** | **String**| Type of the PSU-ID, needed in scenarios where PSUs have several PSU-IDs as access possibility.  In this case, the mean and use are then defined in the ASPSP&#39;s documentation.  | [optional] [default to null]
 **PSU-Corporate-ID** | **String**| Might be mandated in the ASPSP&#39;s documentation. Only used in a corporate context.  | [optional] [default to null]
 **PSU-Corporate-ID-Type** | **String**| Might be mandated in the ASPSP&#39;s documentation. Only used in a corporate context.  | [optional] [default to null]
 **TPP-Redirect-Preferred** | **String**| If it equals \&quot;true\&quot;, the TPP prefers a redirect over an embedded SCA approach. If it equals \&quot;false\&quot;, the TPP prefers not to be redirected for SCA. The ASPSP will then choose between the Embedded or the Decoupled SCA approach, depending on the choice of the SCA procedure by the TPP/PSU. If the parameter is not used, the ASPSP will choose the SCA approach to be applied depending on the SCA method chosen by the TPP/PSU.  | [optional] [default to null] [enum: true, false]
 **TPP-Redirect-URI** | **URI**| URI of the TPP, where the transaction flow shall be redirected to after a Redirect.  Mandated for the Redirect SCA Approach, specifically when TPP-Redirect-Preferred equals \&quot;true\&quot;. It is recommended to always use this header field.  **Remark for Future:** This field might be changed to mandatory in the next version of the specification.  | [optional] [default to null]
 **TPP-Nok-Redirect-URI** | **URI**| If this URI is contained, the TPP is asking to redirect the transaction flow to this address instead of the TPP-Redirect-URI in case of a negative result of the redirect SCA method. This might be ignored by the ASPSP.  | [optional] [default to null]
 **TPP-Notification-URI** | **String**| URI for the Endpoint of the TPP-API to which the status of the payment initiation should be sent. This header field may by ignored by the ASPSP.  For security reasons, it shall be ensured that the TPP-Notification-URI as introduced above is secured by the TPP eIDAS QWAC used for identification of the TPP. The following applies:  URIs which are provided by TPPs in TPP-Notification-URI shall comply with the domain secured by the eIDAS QWAC certificate of the TPP in the field CN or SubjectAltName of the certificate. Please note that in case of example-TPP.com as certificate entry TPP- Notification-URI like www.example-TPP.com/xs2a-client/v1/ASPSPidentifcation/mytransaction- id/notifications or notifications.example-TPP.com/xs2a-client/v1/ASPSPidentifcation/mytransaction- id/notifications would be compliant.  Wildcard definitions shall be taken into account for compliance checks by the ASPSP.  ASPSPs may respond with ASPSP-Notification-Support set to false, if the provided URIs do not comply.  | [optional] [default to null]
 **TPP-Notification-Content-Preferred** | **String**| The string has the form  status&#x3D;X1, ..., Xn  where Xi is one of the constants SCA, PROCESS, LAST and where constants are not repeated. The usage of the constants supports the of following semantics:    SCA: A notification on every change of the scaStatus attribute for all related authorisation processes is preferred by the TPP.    PROCESS: A notification on all changes of consentStatus or transactionStatus attributes is preferred by the TPP.   LAST: Only a notification on the last consentStatus or transactionStatus as available in the XS2A interface is preferred by the TPP.  This header field may be ignored, if the ASPSP does not support resource notification services for the related TPP.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding HTTP request IP Address field between PSU and TPP. It shall be contained if and only if this request was actively initiated by the PSU.  | [optional] [default to null]
 **PSU-IP-Port** | **String**| The forwarded IP Port header field consists of the corresponding HTTP request IP Port field between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Charset** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Encoding** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Language** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-User-Agent** | **String**| The forwarded Agent header field of the HTTP request between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Http-Method** | **String**| HTTP method used at the PSU ? TPP interface, if available. Valid values are: * GET * POST * PUT * PATCH * DELETE  | [optional] [default to null] [enum: GET, POST, PUT, PATCH, DELETE]
 **PSU-Device-ID** | **String**| UUID (Universally Unique Identifier) for a device, which is used by the PSU, if available. UUID identifies either a device or a device dependant application installation. In case of an installation identification this ID need to be unaltered until removal from device.  | [optional] [default to null]
 **PSU-Geo-Location** | **String**| The forwarded Geo Location of the corresponding http request between PSU and TPP if available.  | [optional] [default to null]
 **UNKNOWN\_BASE\_TYPE** | [**UNKNOWN_BASE_TYPE**](../Models/UNKNOWN_BASE_TYPE.md)|  | [optional]

### Return type

[**startScaprocessResponse**](../Models/startScaprocessResponse.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json, application/problem+json

<a name="updateConsentsPsuData"></a>
# **updateConsentsPsuData**
> oneOf&lt;updatePsuIdenticationResponse,updatePsuAuthenticationResponse,selectPsuAuthenticationMethodResponse,scaStatusResponse&gt; updateConsentsPsuData(consentId, authorisationId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-ID, PSU-ID-Type, PSU-Corporate-ID, PSU-Corporate-ID-Type, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location, UNKNOWN\_BASE\_TYPE)

Update PSU Data for consents

    This method update PSU data on the consents  resource if needed. It may authorise a consent within the Embedded SCA Approach where needed.  Independently from the SCA Approach it supports e.g. the selection of the authentication method and a non-SCA PSU authentication.  This methods updates PSU data on the cancellation authorisation resource if needed.  There are several possible Update PSU Data requests in the context of a consent request if needed, which depends on the SCA approach:  * Redirect SCA Approach:   A specific Update PSU Data Request is applicable for     * the selection of authentication methods, before choosing the actual SCA approach. * Decoupled SCA Approach:   A specific Update PSU Data Request is only applicable for   * adding the PSU Identification, if not provided yet in the Payment Initiation Request or the Account Information Consent Request, or if no OAuth2 access token is used, or   * the selection of authentication methods. * Embedded SCA Approach:   The Update PSU Data Request might be used   * to add credentials as a first factor authentication data of the PSU and   * to select the authentication method and   * transaction authorisation.  The SCA Approach might depend on the chosen SCA method. For that reason, the following possible Update PSU Data request can apply to all SCA approaches:  * Select an SCA method in case of several SCA methods are available for the customer.  There are the following request types on this access path:   * Update PSU Identification   * Update PSU Authentication   * Select PSU Autorization Method     WARNING: This method need a reduced header,     therefore many optional elements are not present.     Maybe in a later version the access path will change.   * Transaction Authorisation     WARNING: This method need a reduced header,     therefore many optional elements are not present.     Maybe in a later version the access path will change. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **consentId** | **String**| ID of the corresponding consent object as returned by an Account Information Consent Request.  | [default to null]
 **authorisationId** | **String**| Resource identification of the related SCA. | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-ID** | **String**| Client ID of the PSU in the ASPSP client interface.  Might be mandated in the ASPSP&#39;s documentation.  It might be contained even if an OAuth2 based authentication was performed in a pre-step or an OAuth2 based SCA was performed in an preceding AIS service in the same session. In this case the ASPSP might check whether PSU-ID and token match, according to ASPSP documentation.  | [optional] [default to null]
 **PSU-ID-Type** | **String**| Type of the PSU-ID, needed in scenarios where PSUs have several PSU-IDs as access possibility.  In this case, the mean and use are then defined in the ASPSP&#39;s documentation.  | [optional] [default to null]
 **PSU-Corporate-ID** | **String**| Might be mandated in the ASPSP&#39;s documentation. Only used in a corporate context.  | [optional] [default to null]
 **PSU-Corporate-ID-Type** | **String**| Might be mandated in the ASPSP&#39;s documentation. Only used in a corporate context.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding HTTP request IP Address field between PSU and TPP. It shall be contained if and only if this request was actively initiated by the PSU.  | [optional] [default to null]
 **PSU-IP-Port** | **String**| The forwarded IP Port header field consists of the corresponding HTTP request IP Port field between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Charset** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Encoding** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Language** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-User-Agent** | **String**| The forwarded Agent header field of the HTTP request between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Http-Method** | **String**| HTTP method used at the PSU ? TPP interface, if available. Valid values are: * GET * POST * PUT * PATCH * DELETE  | [optional] [default to null] [enum: GET, POST, PUT, PATCH, DELETE]
 **PSU-Device-ID** | **String**| UUID (Universally Unique Identifier) for a device, which is used by the PSU, if available. UUID identifies either a device or a device dependant application installation. In case of an installation identification this ID need to be unaltered until removal from device.  | [optional] [default to null]
 **PSU-Geo-Location** | **String**| The forwarded Geo Location of the corresponding http request between PSU and TPP if available.  | [optional] [default to null]
 **UNKNOWN\_BASE\_TYPE** | [**UNKNOWN_BASE_TYPE**](../Models/UNKNOWN_BASE_TYPE.md)|  | [optional]

### Return type

[**oneOf&lt;updatePsuIdenticationResponse,updatePsuAuthenticationResponse,selectPsuAuthenticationMethodResponse,scaStatusResponse&gt;**](../Models/oneOf&lt;updatePsuIdenticationResponse,updatePsuAuthenticationResponse,selectPsuAuthenticationMethodResponse,scaStatusResponse&gt;.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json, application/problem+json

