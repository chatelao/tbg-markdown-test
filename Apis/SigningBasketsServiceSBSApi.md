# SigningBasketsServiceSBSApi

All URIs are relative to *https://api.dev.openbankingproject.ch*

Method | HTTP request | Description
------------- | ------------- | -------------
[**createSigningBasket**](SigningBasketsServiceSBSApi.md#createSigningBasket) | **POST** /v1/signing-baskets | Create a signing basket resource
[**deleteSigningBasket**](SigningBasketsServiceSBSApi.md#deleteSigningBasket) | **DELETE** /v1/signing-baskets/{basketId} | Delete the signing basket
[**getSigningBasket**](SigningBasketsServiceSBSApi.md#getSigningBasket) | **GET** /v1/signing-baskets/{basketId} | Returns the content of an signing basket object.
[**getSigningBasketAuthorisation**](SigningBasketsServiceSBSApi.md#getSigningBasketAuthorisation) | **GET** /v1/signing-baskets/{basketId}/authorisations | Get Signing Basket Authorisation Sub-Resources Request
[**getSigningBasketScaStatus**](SigningBasketsServiceSBSApi.md#getSigningBasketScaStatus) | **GET** /v1/signing-baskets/{basketId}/authorisations/{authorisationId} | Read the SCA status of the signing basket authorisation
[**getSigningBasketStatus**](SigningBasketsServiceSBSApi.md#getSigningBasketStatus) | **GET** /v1/signing-baskets/{basketId}/status | Read the status of the signing basket
[**startSigningBasketAuthorisation**](SigningBasketsServiceSBSApi.md#startSigningBasketAuthorisation) | **POST** /v1/signing-baskets/{basketId}/authorisations | Start the authorisation process for a signing basket
[**updateSigningBasketPsuData**](SigningBasketsServiceSBSApi.md#updateSigningBasketPsuData) | **PUT** /v1/signing-baskets/{basketId}/authorisations/{authorisationId} | Update PSU Data for signing basket


<a name="createSigningBasket"></a>
# **createSigningBasket**
> signingBasketResponse-201 createSigningBasket(X-Request-ID, PSU-IP-Address, Digest, Signature, TPP-Signature-Certificate, PSU-ID, PSU-ID-Type, PSU-Corporate-ID, PSU-Corporate-ID-Type, Consent-ID, TPP-Redirect-Preferred, TPP-Redirect-URI, TPP-Nok-Redirect-URI, TPP-Explicit-Authorisation-Preferred, TPP-Notification-URI, TPP-Notification-Content-Preferred, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location, SigningBasket)

Create a signing basket resource

    Create a signing basket resource for authorising several transactions with one SCA method. The resource identifications of these transactions are contained in the  payload of this access method 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding http request IP Address field between PSU and TPP.  | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-ID** | **String**| Client ID of the PSU in the ASPSP client interface.  Might be mandated in the ASPSP&#39;s documentation.  It might be contained even if an OAuth2 based authentication was performed in a pre-step or an OAuth2 based SCA was performed in an preceding AIS service in the same session. In this case the ASPSP might check whether PSU-ID and token match, according to ASPSP documentation.  | [optional] [default to null]
 **PSU-ID-Type** | **String**| Type of the PSU-ID, needed in scenarios where PSUs have several PSU-IDs as access possibility.  In this case, the mean and use are then defined in the ASPSP&#39;s documentation.  | [optional] [default to null]
 **PSU-Corporate-ID** | **String**| Might be mandated in the ASPSP&#39;s documentation. Only used in a corporate context.  | [optional] [default to null]
 **PSU-Corporate-ID-Type** | **String**| Might be mandated in the ASPSP&#39;s documentation. Only used in a corporate context.  | [optional] [default to null]
 **Consent-ID** | **String**| This data element may be contained, if the payment initiation transaction is part of a session, i.e. combined AIS/PIS service. This then contains the consentId of the related AIS consent, which was performed prior to this payment initiation.  | [optional] [default to null]
 **TPP-Redirect-Preferred** | **String**| If it equals \&quot;true\&quot;, the TPP prefers a redirect over an embedded SCA approach. If it equals \&quot;false\&quot;, the TPP prefers not to be redirected for SCA. The ASPSP will then choose between the Embedded or the Decoupled SCA approach, depending on the choice of the SCA procedure by the TPP/PSU. If the parameter is not used, the ASPSP will choose the SCA approach to be applied depending on the SCA method chosen by the TPP/PSU.  | [optional] [default to null] [enum: true, false]
 **TPP-Redirect-URI** | **URI**| URI of the TPP, where the transaction flow shall be redirected to after a Redirect.  Mandated for the Redirect SCA Approach, specifically when TPP-Redirect-Preferred equals \&quot;true\&quot;. It is recommended to always use this header field.  **Remark for Future:** This field might be changed to mandatory in the next version of the specification.  | [optional] [default to null]
 **TPP-Nok-Redirect-URI** | **URI**| If this URI is contained, the TPP is asking to redirect the transaction flow to this address instead of the TPP-Redirect-URI in case of a negative result of the redirect SCA method. This might be ignored by the ASPSP.  | [optional] [default to null]
 **TPP-Explicit-Authorisation-Preferred** | **String**| If it equals \&quot;true\&quot;, the TPP prefers to start the authorisation process separately, e.g. because of the usage of a signing basket. This preference might be ignored by the ASPSP, if a signing basket is not supported as functionality.  If it equals \&quot;false\&quot; or if the parameter is not used, there is no preference of the TPP. This especially indicates that the TPP assumes a direct authorisation of the transaction in the next step, without using a signing basket.  | [optional] [default to null] [enum: true, false]
 **TPP-Notification-URI** | **String**| URI for the Endpoint of the TPP-API to which the status of the payment initiation should be sent. This header field may by ignored by the ASPSP.  For security reasons, it shall be ensured that the TPP-Notification-URI as introduced above is secured by the TPP eIDAS QWAC used for identification of the TPP. The following applies:  URIs which are provided by TPPs in TPP-Notification-URI shall comply with the domain secured by the eIDAS QWAC certificate of the TPP in the field CN or SubjectAltName of the certificate. Please note that in case of example-TPP.com as certificate entry TPP- Notification-URI like www.example-TPP.com/xs2a-client/v1/ASPSPidentifcation/mytransaction- id/notifications or notifications.example-TPP.com/xs2a-client/v1/ASPSPidentifcation/mytransaction- id/notifications would be compliant.  Wildcard definitions shall be taken into account for compliance checks by the ASPSP.  ASPSPs may respond with ASPSP-Notification-Support set to false, if the provided URIs do not comply.  | [optional] [default to null]
 **TPP-Notification-Content-Preferred** | **String**| The string has the form  status&#x3D;X1, ..., Xn  where Xi is one of the constants SCA, PROCESS, LAST and where constants are not repeated. The usage of the constants supports the of following semantics:    SCA: A notification on every change of the scaStatus attribute for all related authorisation processes is preferred by the TPP.    PROCESS: A notification on all changes of consentStatus or transactionStatus attributes is preferred by the TPP.   LAST: Only a notification on the last consentStatus or transactionStatus as available in the XS2A interface is preferred by the TPP.  This header field may be ignored, if the ASPSP does not support resource notification services for the related TPP.  | [optional] [default to null]
 **PSU-IP-Port** | **String**| The forwarded IP Port header field consists of the corresponding HTTP request IP Port field between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Charset** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Encoding** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Accept-Language** | **String**| The forwarded IP Accept header fields consist of the corresponding HTTP request Accept header fields between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-User-Agent** | **String**| The forwarded Agent header field of the HTTP request between PSU and TPP, if available.  | [optional] [default to null]
 **PSU-Http-Method** | **String**| HTTP method used at the PSU ? TPP interface, if available. Valid values are: * GET * POST * PUT * PATCH * DELETE  | [optional] [default to null] [enum: GET, POST, PUT, PATCH, DELETE]
 **PSU-Device-ID** | **String**| UUID (Universally Unique Identifier) for a device, which is used by the PSU, if available. UUID identifies either a device or a device dependant application installation. In case of an installation identification this ID need to be unaltered until removal from device.  | [optional] [default to null]
 **PSU-Geo-Location** | **String**| The forwarded Geo Location of the corresponding http request between PSU and TPP if available.  | [optional] [default to null]
 **SigningBasket** | [**SigningBasket**](../Models/SigningBasket.md)| Request body for a confirmation of an establishing signing basket request  | [optional]

### Return type

[**signingBasketResponse-201**](../Models/signingBasketResponse-201.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json, application/problem+json

<a name="deleteSigningBasket"></a>
# **deleteSigningBasket**
> deleteSigningBasket(basketId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Delete the signing basket

    Delete the signing basket structure as long as no (partial) authorisation has yet been applied. The undlerying transactions are not affected by this deletion.  Remark: The signing basket as such is not deletable after a first (partial) authorisation has been applied. Nevertheless, single transactions might be cancelled on an individual basis on the XS2A interface. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **basketId** | **String**| This identification of the corresponding signing basket object.  | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding http request IP Address field between PSU and TPP.  | [optional] [default to null]
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

<a name="getSigningBasket"></a>
# **getSigningBasket**
> signingBasketResponse-200 getSigningBasket(basketId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Returns the content of an signing basket object.

    Returns the content of an signing basket object.

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **basketId** | **String**| This identification of the corresponding signing basket object.  | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding http request IP Address field between PSU and TPP.  | [optional] [default to null]
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

[**signingBasketResponse-200**](../Models/signingBasketResponse-200.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/problem+json

<a name="getSigningBasketAuthorisation"></a>
# **getSigningBasketAuthorisation**
> authorisations getSigningBasketAuthorisation(basketId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Get Signing Basket Authorisation Sub-Resources Request

    Read a list of all authorisation subresources IDs which have been created.  This function returns an array of hyperlinks to all generated authorisation sub-resources. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **basketId** | **String**| This identification of the corresponding signing basket object.  | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding http request IP Address field between PSU and TPP.  | [optional] [default to null]
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

<a name="getSigningBasketScaStatus"></a>
# **getSigningBasketScaStatus**
> scaStatusResponse getSigningBasketScaStatus(basketId, authorisationId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Read the SCA status of the signing basket authorisation

    This method returns the SCA status of a signing basket&#39;s authorisation sub-resource. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **basketId** | **String**| This identification of the corresponding signing basket object.  | [default to null]
 **authorisationId** | **String**| Resource identification of the related SCA. | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding http request IP Address field between PSU and TPP.  | [optional] [default to null]
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

<a name="getSigningBasketStatus"></a>
# **getSigningBasketStatus**
> signingBasketStatusResponse-200 getSigningBasketStatus(basketId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-ID, PSU-ID-Type, PSU-Corporate-ID, PSU-Corporate-ID-Type, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Read the status of the signing basket

    Returns the status of a signing basket object. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **basketId** | **String**| This identification of the corresponding signing basket object.  | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-ID** | **String**| Client ID of the PSU in the ASPSP client interface.  Might be mandated in the ASPSP&#39;s documentation.  It might be contained even if an OAuth2 based authentication was performed in a pre-step or an OAuth2 based SCA was performed in an preceding AIS service in the same session. In this case the ASPSP might check whether PSU-ID and token match, according to ASPSP documentation.  | [optional] [default to null]
 **PSU-ID-Type** | **String**| Type of the PSU-ID, needed in scenarios where PSUs have several PSU-IDs as access possibility.  In this case, the mean and use are then defined in the ASPSP&#39;s documentation.  | [optional] [default to null]
 **PSU-Corporate-ID** | **String**| Might be mandated in the ASPSP&#39;s documentation. Only used in a corporate context.  | [optional] [default to null]
 **PSU-Corporate-ID-Type** | **String**| Might be mandated in the ASPSP&#39;s documentation. Only used in a corporate context.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding http request IP Address field between PSU and TPP.  | [optional] [default to null]
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

[**signingBasketStatusResponse-200**](../Models/signingBasketStatusResponse-200.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/problem+json

<a name="startSigningBasketAuthorisation"></a>
# **startSigningBasketAuthorisation**
> startScaprocessResponse startSigningBasketAuthorisation(basketId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-ID, PSU-ID-Type, PSU-Corporate-ID, PSU-Corporate-ID-Type, TPP-Redirect-Preferred, TPP-Redirect-URI, TPP-Nok-Redirect-URI, TPP-Notification-URI, TPP-Notification-Content-Preferred, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location, UNKNOWN\_BASE\_TYPE)

Start the authorisation process for a signing basket

    Create an authorisation sub-resource and start the authorisation process of a signing basket. The message might in addition transmit authentication and authorisation related data.  This method is iterated n times for a n times SCA authorisation in a corporate context, each creating an own authorisation sub-endpoint for the corresponding PSU authorising the signing-baskets.  The ASPSP might make the usage of this access method unnecessary in case of only one SCA process needed, since the related authorisation resource might be automatically created by the ASPSP after the submission of the payment data with the first POST signing basket call.  The start authorisation process is a process which is needed for creating a new authorisation or cancellation sub-resource.  This applies in the following scenarios:    * The ASPSP has indicated with an &#39;startAuthorisation&#39; hyperlink in the preceding Payment     Initiation Response that an explicit start of the authorisation process is needed by the TPP.     The &#39;startAuthorisation&#39; hyperlink can transport more information about data which needs to be     uploaded by using the extended forms.     * &#39;startAuthorisationWithPsuIdentfication&#39;,     * &#39;startAuthorisationWithPsuAuthentication&#39;     * &#39;startAuthorisationWithEncryptedPsuAuthentication&#39;     * &#39;startAuthorisationWithAuthentciationMethodSelection&#39;   * The related payment initiation cannot yet be executed since a multilevel SCA is mandated.   * The ASPSP has indicated with an &#39;startAuthorisation&#39; hyperlink in the preceding     Payment Cancellation Response that an explicit start of the authorisation process is needed by the TPP.     The &#39;startAuthorisation&#39; hyperlink can transport more information about data which needs to be uploaded     by using the extended forms as indicated above.   * The related payment cancellation request cannot be applied yet since a multilevel SCA is mandate for     executing the cancellation.   * The signing basket needs to be authorised yet. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **basketId** | **String**| This identification of the corresponding signing basket object.  | [default to null]
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
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding http request IP Address field between PSU and TPP.  | [optional] [default to null]
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

<a name="updateSigningBasketPsuData"></a>
# **updateSigningBasketPsuData**
> oneOf&lt;updatePsuIdenticationResponse,updatePsuAuthenticationResponse,selectPsuAuthenticationMethodResponse,scaStatusResponse&gt; updateSigningBasketPsuData(basketId, authorisationId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-ID, PSU-ID-Type, PSU-Corporate-ID, PSU-Corporate-ID-Type, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location, UNKNOWN\_BASE\_TYPE)

Update PSU Data for signing basket

    This method update PSU data on the signing basket resource if needed. It may authorise a igning basket within the Embedded SCA Approach where needed.  Independently from the SCA Approach it supports e.g. the selection of the authentication method and a non-SCA PSU authentication.  This methods updates PSU data on the cancellation authorisation resource if needed.  There are several possible Update PSU Data requests in the context of a consent request if needed, which depends on the SCA approach:  * Redirect SCA Approach:   A specific Update PSU Data Request is applicable for     * the selection of authentication methods, before choosing the actual SCA approach. * Decoupled SCA Approach:   A specific Update PSU Data Request is only applicable for   * adding the PSU Identification, if not provided yet in the Payment Initiation Request or the Account Information Consent Request, or if no OAuth2 access token is used, or   * the selection of authentication methods. * Embedded SCA Approach:   The Update PSU Data Request might be used   * to add credentials as a first factor authentication data of the PSU and   * to select the authentication method and   * transaction authorisation.  The SCA Approach might depend on the chosen SCA method. For that reason, the following possible Update PSU Data request can apply to all SCA approaches:  * Select an SCA method in case of several SCA methods are available for the customer.  There are the following request types on this access path:   * Update PSU Identification   * Update PSU Authentication   * Select PSU Autorization Method     WARNING: This method need a reduced header,     therefore many optional elements are not present.     Maybe in a later version the access path will change.   * Transaction Authorisation     WARNING: This method need a reduced header,     therefore many optional elements are not present.     Maybe in a later version the access path will change. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **basketId** | **String**| This identification of the corresponding signing basket object.  | [default to null]
 **authorisationId** | **String**| Resource identification of the related SCA. | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]
 **PSU-ID** | **String**| Client ID of the PSU in the ASPSP client interface.  Might be mandated in the ASPSP&#39;s documentation.  It might be contained even if an OAuth2 based authentication was performed in a pre-step or an OAuth2 based SCA was performed in an preceding AIS service in the same session. In this case the ASPSP might check whether PSU-ID and token match, according to ASPSP documentation.  | [optional] [default to null]
 **PSU-ID-Type** | **String**| Type of the PSU-ID, needed in scenarios where PSUs have several PSU-IDs as access possibility.  In this case, the mean and use are then defined in the ASPSP&#39;s documentation.  | [optional] [default to null]
 **PSU-Corporate-ID** | **String**| Might be mandated in the ASPSP&#39;s documentation. Only used in a corporate context.  | [optional] [default to null]
 **PSU-Corporate-ID-Type** | **String**| Might be mandated in the ASPSP&#39;s documentation. Only used in a corporate context.  | [optional] [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding http request IP Address field between PSU and TPP.  | [optional] [default to null]
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

