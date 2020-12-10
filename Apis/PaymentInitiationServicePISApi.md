# PaymentInitiationServicePISApi

All URIs are relative to *https://api.dev.openbankingproject.ch*

Method | HTTP request | Description
------------- | ------------- | -------------
[**cancelPayment**](PaymentInitiationServicePISApi.md#cancelPayment) | **DELETE** /v1/{payment-service}/{payment-product}/{paymentId} | Payment Cancellation Request
[**getPaymentCancellationScaStatus**](PaymentInitiationServicePISApi.md#getPaymentCancellationScaStatus) | **GET** /v1/{payment-service}/{payment-product}/{paymentId}/cancellation-authorisations/{cancellationId} | Read the SCA status of the payment cancellation&#39;s authorisation.
[**getPaymentInformation**](PaymentInitiationServicePISApi.md#getPaymentInformation) | **GET** /v1/{payment-service}/{payment-product}/{paymentId} | Get Payment Information
[**getPaymentInitiationAuthorisation**](PaymentInitiationServicePISApi.md#getPaymentInitiationAuthorisation) | **GET** /v1/{payment-service}/{payment-product}/{paymentId}/authorisations | Get Payment Initiation Authorisation Sub-Resources Request
[**getPaymentInitiationCancellationAuthorisationInformation**](PaymentInitiationServicePISApi.md#getPaymentInitiationCancellationAuthorisationInformation) | **GET** /v1/{payment-service}/{payment-product}/{paymentId}/cancellation-authorisations | Will deliver an array of resource identifications to all generated cancellation authorisation sub-resources.
[**getPaymentInitiationScaStatus**](PaymentInitiationServicePISApi.md#getPaymentInitiationScaStatus) | **GET** /v1/{payment-service}/{payment-product}/{paymentId}/authorisations/{authorisationId} | Read the SCA Status of the payment authorisation
[**getPaymentInitiationStatus**](PaymentInitiationServicePISApi.md#getPaymentInitiationStatus) | **GET** /v1/{payment-service}/{payment-product}/{paymentId}/status | Payment initiation status request
[**initiatePayment**](PaymentInitiationServicePISApi.md#initiatePayment) | **POST** /v1/{payment-service}/{payment-product} | Payment initiation request
[**startPaymentAuthorisation**](PaymentInitiationServicePISApi.md#startPaymentAuthorisation) | **POST** /v1/{payment-service}/{payment-product}/{paymentId}/authorisations | Start the authorisation process for a payment initiation
[**startPaymentInitiationCancellationAuthorisation**](PaymentInitiationServicePISApi.md#startPaymentInitiationCancellationAuthorisation) | **POST** /v1/{payment-service}/{payment-product}/{paymentId}/cancellation-authorisations | Start the authorisation process for the cancellation of the addressed payment
[**updatePaymentCancellationPsuData**](PaymentInitiationServicePISApi.md#updatePaymentCancellationPsuData) | **PUT** /v1/{payment-service}/{payment-product}/{paymentId}/cancellation-authorisations/{cancellationId} | Update PSU Data for payment initiation cancellation
[**updatePaymentPsuData**](PaymentInitiationServicePISApi.md#updatePaymentPsuData) | **PUT** /v1/{payment-service}/{payment-product}/{paymentId}/authorisations/{authorisationId} | Update PSU data for payment initiation


<a name="cancelPayment"></a>
# **cancelPayment**
> paymentInitiationCancelResponse-202 cancelPayment(payment-service, payment-product, paymentId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Payment Cancellation Request

    This method initiates the cancellation of a payment. Depending on the payment-service, the payment-product and the ASPSP&#39;s implementation, this TPP call might be sufficient to cancel a payment. If an authorisation of the payment cancellation is mandated by the ASPSP, a corresponding hyperlink will be contained in the response message.  Cancels the addressed payment with resource identification paymentId if applicable to the payment-service, payment-product and received in product related timelines (e.g. before end of business day for scheduled payments of the last business day before the scheduled execution day).  The response to this DELETE command will tell the TPP whether the   * access method was rejected   * access method was successful, or   * access method is generally applicable, but further authorisation processes are needed. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **payment-service** | **String**| Payment service:  Possible values are: * payments * bulk-payments * periodic-payments  | [default to null] [enum: payments, bulk-payments, periodic-payments]
 **payment-product** | **String**| The addressed payment product endpoint, e.g. for SEPA Credit Transfers (SCT). The ASPSP will publish which of the payment products/endpoints will be supported.  The following payment products are supported:   - sepa-credit-transfers   - cross-border-credit-transfers   - domestic-swiss-credit-transfers   - domestic-swiss-credit-transfers-isr   - domestic-swiss-foreign-credit-transfers   - pain.001-sepa-credit-transfers   - pain.001-cross-border-credit-transfers   - pain.001-swiss-six-credit-transfers  **Remark:** For all SEPA Credit Transfer based endpoints which accept XML encoding, the XML pain.001 schemes provided by EPC are supported by the ASPSP as a minimum for the body content. Further XML schemes might be supported by some communities.  **Remark:** For cross-border and TARGET-2 payments only community wide pain.001 schemes do exist. There are plenty of country specificic scheme variants.  | [default to null] [enum: sepa-credit-transfers, cross-border-credit-transfers, domestic-swiss-credit-transfers, domestic-swiss-credit-transfers-isr, domestic-swiss-foreign-credit-transfers, pain.001-sepa-credit-transfers, pain.001-cross-border-credit-transfers, pain.001-swiss-six-credit-transfers]
 **paymentId** | **String**| Resource identification of the generated payment initiation resource. | [default to null]
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

[**paymentInitiationCancelResponse-202**](../Models/paymentInitiationCancelResponse-202.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/problem+json

<a name="getPaymentCancellationScaStatus"></a>
# **getPaymentCancellationScaStatus**
> scaStatusResponse getPaymentCancellationScaStatus(payment-service, payment-product, paymentId, cancellationId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Read the SCA status of the payment cancellation&#39;s authorisation.

    This method returns the SCA status of a payment initiation&#39;s authorisation sub-resource. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **payment-service** | **String**| Payment service:  Possible values are: * payments * bulk-payments * periodic-payments  | [default to null] [enum: payments, bulk-payments, periodic-payments]
 **payment-product** | **String**| The addressed payment product endpoint, e.g. for SEPA Credit Transfers (SCT). The ASPSP will publish which of the payment products/endpoints will be supported.  The following payment products are supported:   - sepa-credit-transfers   - cross-border-credit-transfers   - domestic-swiss-credit-transfers   - domestic-swiss-credit-transfers-isr   - domestic-swiss-foreign-credit-transfers   - pain.001-sepa-credit-transfers   - pain.001-cross-border-credit-transfers   - pain.001-swiss-six-credit-transfers  **Remark:** For all SEPA Credit Transfer based endpoints which accept XML encoding, the XML pain.001 schemes provided by EPC are supported by the ASPSP as a minimum for the body content. Further XML schemes might be supported by some communities.  **Remark:** For cross-border and TARGET-2 payments only community wide pain.001 schemes do exist. There are plenty of country specificic scheme variants.  | [default to null] [enum: sepa-credit-transfers, cross-border-credit-transfers, domestic-swiss-credit-transfers, domestic-swiss-credit-transfers-isr, domestic-swiss-foreign-credit-transfers, pain.001-sepa-credit-transfers, pain.001-cross-border-credit-transfers, pain.001-swiss-six-credit-transfers]
 **paymentId** | **String**| Resource identification of the generated payment initiation resource. | [default to null]
 **cancellationId** | **String**| Identification for cancellation resource. | [default to null]
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

<a name="getPaymentInformation"></a>
# **getPaymentInformation**
> oneOf&lt;paymentInitiationWithStatusResponse,periodicPaymentInitiationWithStatusResponse,bulkPaymentInitiationWithStatusResponse&gt; getPaymentInformation(payment-service, payment-product, paymentId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Get Payment Information

    Returns the content of a payment object

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **payment-service** | **String**| Payment service:  Possible values are: * payments * bulk-payments * periodic-payments  | [default to null] [enum: payments, bulk-payments, periodic-payments]
 **payment-product** | **String**| The addressed payment product endpoint, e.g. for SEPA Credit Transfers (SCT). The ASPSP will publish which of the payment products/endpoints will be supported.  The following payment products are supported:   - sepa-credit-transfers   - cross-border-credit-transfers   - domestic-swiss-credit-transfers   - domestic-swiss-credit-transfers-isr   - domestic-swiss-foreign-credit-transfers   - pain.001-sepa-credit-transfers   - pain.001-cross-border-credit-transfers   - pain.001-swiss-six-credit-transfers  **Remark:** For all SEPA Credit Transfer based endpoints which accept XML encoding, the XML pain.001 schemes provided by EPC are supported by the ASPSP as a minimum for the body content. Further XML schemes might be supported by some communities.  **Remark:** For cross-border and TARGET-2 payments only community wide pain.001 schemes do exist. There are plenty of country specificic scheme variants.  | [default to null] [enum: sepa-credit-transfers, cross-border-credit-transfers, domestic-swiss-credit-transfers, domestic-swiss-credit-transfers-isr, domestic-swiss-foreign-credit-transfers, pain.001-sepa-credit-transfers, pain.001-cross-border-credit-transfers, pain.001-swiss-six-credit-transfers]
 **paymentId** | **String**| Resource identification of the generated payment initiation resource. | [default to null]
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

[**oneOf&lt;paymentInitiationWithStatusResponse,periodicPaymentInitiationWithStatusResponse,bulkPaymentInitiationWithStatusResponse&gt;**](../Models/oneOf&lt;paymentInitiationWithStatusResponse,periodicPaymentInitiationWithStatusResponse,bulkPaymentInitiationWithStatusResponse&gt;.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/xml, multipart/form-data, application/problem+json

<a name="getPaymentInitiationAuthorisation"></a>
# **getPaymentInitiationAuthorisation**
> authorisations getPaymentInitiationAuthorisation(payment-service, payment-product, paymentId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Get Payment Initiation Authorisation Sub-Resources Request

    Read a list of all authorisation subresources IDs which have been created.  This function returns an array of hyperlinks to all generated authorisation sub-resources. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **payment-service** | **String**| Payment service:  Possible values are: * payments * bulk-payments * periodic-payments  | [default to null] [enum: payments, bulk-payments, periodic-payments]
 **payment-product** | **String**| The addressed payment product endpoint, e.g. for SEPA Credit Transfers (SCT). The ASPSP will publish which of the payment products/endpoints will be supported.  The following payment products are supported:   - sepa-credit-transfers   - cross-border-credit-transfers   - domestic-swiss-credit-transfers   - domestic-swiss-credit-transfers-isr   - domestic-swiss-foreign-credit-transfers   - pain.001-sepa-credit-transfers   - pain.001-cross-border-credit-transfers   - pain.001-swiss-six-credit-transfers  **Remark:** For all SEPA Credit Transfer based endpoints which accept XML encoding, the XML pain.001 schemes provided by EPC are supported by the ASPSP as a minimum for the body content. Further XML schemes might be supported by some communities.  **Remark:** For cross-border and TARGET-2 payments only community wide pain.001 schemes do exist. There are plenty of country specificic scheme variants.  | [default to null] [enum: sepa-credit-transfers, cross-border-credit-transfers, domestic-swiss-credit-transfers, domestic-swiss-credit-transfers-isr, domestic-swiss-foreign-credit-transfers, pain.001-sepa-credit-transfers, pain.001-cross-border-credit-transfers, pain.001-swiss-six-credit-transfers]
 **paymentId** | **String**| Resource identification of the generated payment initiation resource. | [default to null]
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

<a name="getPaymentInitiationCancellationAuthorisationInformation"></a>
# **getPaymentInitiationCancellationAuthorisationInformation**
> List getPaymentInitiationCancellationAuthorisationInformation(payment-service, payment-product, paymentId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Will deliver an array of resource identifications to all generated cancellation authorisation sub-resources.

    Retrieve a list of all created cancellation authorisation sub-resources. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **payment-service** | **String**| Payment service:  Possible values are: * payments * bulk-payments * periodic-payments  | [default to null] [enum: payments, bulk-payments, periodic-payments]
 **payment-product** | **String**| The addressed payment product endpoint, e.g. for SEPA Credit Transfers (SCT). The ASPSP will publish which of the payment products/endpoints will be supported.  The following payment products are supported:   - sepa-credit-transfers   - cross-border-credit-transfers   - domestic-swiss-credit-transfers   - domestic-swiss-credit-transfers-isr   - domestic-swiss-foreign-credit-transfers   - pain.001-sepa-credit-transfers   - pain.001-cross-border-credit-transfers   - pain.001-swiss-six-credit-transfers  **Remark:** For all SEPA Credit Transfer based endpoints which accept XML encoding, the XML pain.001 schemes provided by EPC are supported by the ASPSP as a minimum for the body content. Further XML schemes might be supported by some communities.  **Remark:** For cross-border and TARGET-2 payments only community wide pain.001 schemes do exist. There are plenty of country specificic scheme variants.  | [default to null] [enum: sepa-credit-transfers, cross-border-credit-transfers, domestic-swiss-credit-transfers, domestic-swiss-credit-transfers-isr, domestic-swiss-foreign-credit-transfers, pain.001-sepa-credit-transfers, pain.001-cross-border-credit-transfers, pain.001-swiss-six-credit-transfers]
 **paymentId** | **String**| Resource identification of the generated payment initiation resource. | [default to null]
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

[**List**](../Models/string.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/problem+json

<a name="getPaymentInitiationScaStatus"></a>
# **getPaymentInitiationScaStatus**
> scaStatusResponse getPaymentInitiationScaStatus(payment-service, payment-product, paymentId, authorisationId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Read the SCA Status of the payment authorisation

    This method returns the SCA status of a payment initiation&#39;s authorisation sub-resource. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **payment-service** | **String**| Payment service:  Possible values are: * payments * bulk-payments * periodic-payments  | [default to null] [enum: payments, bulk-payments, periodic-payments]
 **payment-product** | **String**| The addressed payment product endpoint, e.g. for SEPA Credit Transfers (SCT). The ASPSP will publish which of the payment products/endpoints will be supported.  The following payment products are supported:   - sepa-credit-transfers   - cross-border-credit-transfers   - domestic-swiss-credit-transfers   - domestic-swiss-credit-transfers-isr   - domestic-swiss-foreign-credit-transfers   - pain.001-sepa-credit-transfers   - pain.001-cross-border-credit-transfers   - pain.001-swiss-six-credit-transfers  **Remark:** For all SEPA Credit Transfer based endpoints which accept XML encoding, the XML pain.001 schemes provided by EPC are supported by the ASPSP as a minimum for the body content. Further XML schemes might be supported by some communities.  **Remark:** For cross-border and TARGET-2 payments only community wide pain.001 schemes do exist. There are plenty of country specificic scheme variants.  | [default to null] [enum: sepa-credit-transfers, cross-border-credit-transfers, domestic-swiss-credit-transfers, domestic-swiss-credit-transfers-isr, domestic-swiss-foreign-credit-transfers, pain.001-sepa-credit-transfers, pain.001-cross-border-credit-transfers, pain.001-swiss-six-credit-transfers]
 **paymentId** | **String**| Resource identification of the generated payment initiation resource. | [default to null]
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

<a name="getPaymentInitiationStatus"></a>
# **getPaymentInitiationStatus**
> paymentInitiationStatusResponse-200_json getPaymentInitiationStatus(payment-service, payment-product, paymentId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Payment initiation status request

    Check the transaction status of a payment initiation.

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **payment-service** | **String**| Payment service:  Possible values are: * payments * bulk-payments * periodic-payments  | [default to null] [enum: payments, bulk-payments, periodic-payments]
 **payment-product** | **String**| The addressed payment product endpoint, e.g. for SEPA Credit Transfers (SCT). The ASPSP will publish which of the payment products/endpoints will be supported.  The following payment products are supported:   - sepa-credit-transfers   - cross-border-credit-transfers   - domestic-swiss-credit-transfers   - domestic-swiss-credit-transfers-isr   - domestic-swiss-foreign-credit-transfers   - pain.001-sepa-credit-transfers   - pain.001-cross-border-credit-transfers   - pain.001-swiss-six-credit-transfers  **Remark:** For all SEPA Credit Transfer based endpoints which accept XML encoding, the XML pain.001 schemes provided by EPC are supported by the ASPSP as a minimum for the body content. Further XML schemes might be supported by some communities.  **Remark:** For cross-border and TARGET-2 payments only community wide pain.001 schemes do exist. There are plenty of country specificic scheme variants.  | [default to null] [enum: sepa-credit-transfers, cross-border-credit-transfers, domestic-swiss-credit-transfers, domestic-swiss-credit-transfers-isr, domestic-swiss-foreign-credit-transfers, pain.001-sepa-credit-transfers, pain.001-cross-border-credit-transfers, pain.001-swiss-six-credit-transfers]
 **paymentId** | **String**| Resource identification of the generated payment initiation resource. | [default to null]
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

[**paymentInitiationStatusResponse-200_json**](../Models/paymentInitiationStatusResponse-200_json.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/xml, application/problem+json

<a name="initiatePayment"></a>
# **initiatePayment**
> paymentInitationRequestResponse-201 initiatePayment(payment-service, payment-product, X-Request-ID, PSU-IP-Address, UNKNOWN\_BASE\_TYPE, Digest, Signature, TPP-Signature-Certificate, PSU-ID, PSU-ID-Type, PSU-Corporate-ID, PSU-Corporate-ID-Type, Consent-ID, TPP-Redirect-Preferred, TPP-Redirect-URI, TPP-Nok-Redirect-URI, TPP-Explicit-Authorisation-Preferred, TPP-Rejection-NoFunds-Preferred, TPP-Notification-URI, TPP-Notification-Content-Preferred, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Payment initiation request

    This method is used to initiate a payment at the ASPSP.  ## Variants of Payment Initiation Requests  This method to initiate a payment initiation at the ASPSP can be sent with either a JSON body or an pain.001 body depending on the payment product in the path.  There are the following **payment products**:    - Payment products with payment information in *JSON* format:     - ***domestic-swiss-credit-transfers-isr***     - ***domestic-swiss-credit-transfers***     - ***domestic-swiss-foreign-credit-transfers***     - ***sepa-credit-transfers***     - ***cross-border-credit-transfers***   - Payment products with payment information in *SIX pain.001* XML format:     - ***pain.001-sepa-credit-transfers***     - ***pain.001-cross-border-credit-transfers***     - ***pain.001-swiss-six-credit-transfers***  Furthermore the request body depends on the **payment-service**   * ***payments***: A single payment initiation request.   * ***bulk-payments***: A collection of several payment iniatiation requests.      In case of a *pain.001* message there are more than one payments contained in the *pain.001 message.      In case of a *JSON* there are several JSON payment blocks contained in a joining list.   * ***periodic-payments***:     Create a standing order initiation resource for recurrent i.e. periodic payments addressable under {paymentId}      with all data relevant for the corresponding payment product and the execution of the standing order contained in a JSON body.  This is the first step in the API to initiate the related recurring/periodic payment.  ## Single and mulitilevel SCA Processes  The Payment Initiation Requests are independent from the need of one ore multilevel SCA processing, i.e. independent from the number of authorisations needed for the execution of payments.  But the response messages are specific to either one SCA processing or multilevel SCA processing.  For payment initiation with multilevel SCA, this specification requires an explicit start of the authorisation, i.e. links directly associated with SCA processing like &#39;scaRedirect&#39; or &#39;scaOAuth&#39; cannot be contained in the response message of a Payment Initation Request for a payment, where multiple authorisations are needed. Also if any data is needed for the next action, like selecting an SCA method is not supported in the response, since all starts of the multiple authorisations are fully equal. In these cases, first an authorisation sub-resource has to be generated following the &#39;startAuthorisation&#39; link. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **payment-service** | **String**| Payment service:  Possible values are: * payments * bulk-payments * periodic-payments  | [default to null] [enum: payments, bulk-payments, periodic-payments]
 **payment-product** | **String**| The addressed payment product endpoint, e.g. for SEPA Credit Transfers (SCT). The ASPSP will publish which of the payment products/endpoints will be supported.  The following payment products are supported:   - sepa-credit-transfers   - cross-border-credit-transfers   - domestic-swiss-credit-transfers   - domestic-swiss-credit-transfers-isr   - domestic-swiss-foreign-credit-transfers   - pain.001-sepa-credit-transfers   - pain.001-cross-border-credit-transfers   - pain.001-swiss-six-credit-transfers  **Remark:** For all SEPA Credit Transfer based endpoints which accept XML encoding, the XML pain.001 schemes provided by EPC are supported by the ASPSP as a minimum for the body content. Further XML schemes might be supported by some communities.  **Remark:** For cross-border and TARGET-2 payments only community wide pain.001 schemes do exist. There are plenty of country specificic scheme variants.  | [default to null] [enum: sepa-credit-transfers, cross-border-credit-transfers, domestic-swiss-credit-transfers, domestic-swiss-credit-transfers-isr, domestic-swiss-foreign-credit-transfers, pain.001-sepa-credit-transfers, pain.001-cross-border-credit-transfers, pain.001-swiss-six-credit-transfers]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **PSU-IP-Address** | **String**| The forwarded IP Address header field consists of the corresponding http request IP Address field between PSU and TPP.  | [default to null]
 **UNKNOWN\_BASE\_TYPE** | [**UNKNOWN_BASE_TYPE**](../Models/UNKNOWN_BASE_TYPE.md)| JSON request body for a payment inition request message  There are the following payment-products supported:   * \&quot;sepa-credit-transfers\&quot; with JSON-Body   * \&quot;cross-border-credit-transfers\&quot; with JSON-Body   * \&quot;domestic-swiss-credit-transfers\&quot;   * \&quot;domestic-swiss-credit-transfers-isr\&quot;   * \&quot;pain.001-sepa-credit-transfers\&quot; with XML pain.001.001.03 body for SCT scheme     Only country specific schemes are currently available   * \&quot;pain.001-cross-border-credit-transfers\&quot; with pain.001 body.     Only country specific schemes are currently available   * \&quot;pain.001-swiss-six-credit-transfers\&quot;  There are the following payment-services supported:   * \&quot;payments\&quot;   * \&quot;periodic-payments\&quot;   * \&quot;bulk-paments\&quot;  All optional, conditional and predefined but not yet used fields are defined.  |
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
 **TPP-Rejection-NoFunds-Preferred** | **String**| If it equals \&quot;true\&quot; then the TPP prefers a rejection of the payment initiation in case the ASPSP is providing an integrated confirmation of funds request an the result of this is that not sufficient funds are available.  If it equals \&quot;false\&quot; then the TPP prefers that the ASPSP is dealing with the payment initiation like in the ASPSPs online channel, potentially waiting for a certain time period for funds to arrive to initiate the payment.  This parameter might be ignored by the ASPSP.  | [optional] [default to null] [enum: true, false]
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

### Return type

[**paymentInitationRequestResponse-201**](../Models/paymentInitationRequestResponse-201.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: application/json, application/xml, multipart/form-data
- **Accept**: application/json, application/problem+json

<a name="startPaymentAuthorisation"></a>
# **startPaymentAuthorisation**
> startScaprocessResponse startPaymentAuthorisation(payment-service, payment-product, paymentId, X-Request-ID, PSU-ID, PSU-ID-Type, PSU-Corporate-ID, PSU-Corporate-ID-Type, TPP-Redirect-Preferred, TPP-Redirect-URI, TPP-Nok-Redirect-URI, TPP-Notification-URI, TPP-Notification-Content-Preferred, Digest, Signature, TPP-Signature-Certificate, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location, UNKNOWN\_BASE\_TYPE)

Start the authorisation process for a payment initiation

    Create an authorisation sub-resource and start the authorisation process. The message might in addition transmit authentication and authorisation related data.  This method is iterated n times for a n times SCA authorisation in a corporate context, each creating an own authorisation sub-endpoint for the corresponding PSU authorising the transaction.  The ASPSP might make the usage of this access method unnecessary in case of only one SCA process needed, since the related authorisation resource might be automatically created by the ASPSP after the submission of the payment data with the first POST payments/{payment-product} call.  The start authorisation process is a process which is needed for creating a new authorisation or cancellation sub-resource.  This applies in the following scenarios:    * The ASPSP has indicated with an &#39;startAuthorisation&#39; hyperlink in the preceding Payment     Initiation Response that an explicit start of the authorisation process is needed by the TPP.     The &#39;startAuthorisation&#39; hyperlink can transport more information about data which needs to be     uploaded by using the extended forms.     * &#39;startAuthorisationWithPsuIdentfication&#39;,     * &#39;startAuthorisationWithPsuAuthentication&#39;     * &#39;startAuthorisationWithEncryptedPsuAuthentication&#39;     * &#39;startAuthorisationWithAuthentciationMethodSelection&#39;   * The related payment initiation cannot yet be executed since a multilevel SCA is mandated.   * The ASPSP has indicated with an &#39;startAuthorisation&#39; hyperlink in the preceding     Payment Cancellation Response that an explicit start of the authorisation process is needed by the TPP.     The &#39;startAuthorisation&#39; hyperlink can transport more information about data which needs to be uploaded     by using the extended forms as indicated above.   * The related payment cancellation request cannot be applied yet since a multilevel SCA is mandate for     executing the cancellation.   * The signing basket needs to be authorised yet. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **payment-service** | **String**| Payment service:  Possible values are: * payments * bulk-payments * periodic-payments  | [default to null] [enum: payments, bulk-payments, periodic-payments]
 **payment-product** | **String**| The addressed payment product endpoint, e.g. for SEPA Credit Transfers (SCT). The ASPSP will publish which of the payment products/endpoints will be supported.  The following payment products are supported:   - sepa-credit-transfers   - cross-border-credit-transfers   - domestic-swiss-credit-transfers   - domestic-swiss-credit-transfers-isr   - domestic-swiss-foreign-credit-transfers   - pain.001-sepa-credit-transfers   - pain.001-cross-border-credit-transfers   - pain.001-swiss-six-credit-transfers  **Remark:** For all SEPA Credit Transfer based endpoints which accept XML encoding, the XML pain.001 schemes provided by EPC are supported by the ASPSP as a minimum for the body content. Further XML schemes might be supported by some communities.  **Remark:** For cross-border and TARGET-2 payments only community wide pain.001 schemes do exist. There are plenty of country specificic scheme variants.  | [default to null] [enum: sepa-credit-transfers, cross-border-credit-transfers, domestic-swiss-credit-transfers, domestic-swiss-credit-transfers-isr, domestic-swiss-foreign-credit-transfers, pain.001-sepa-credit-transfers, pain.001-cross-border-credit-transfers, pain.001-swiss-six-credit-transfers]
 **paymentId** | **String**| Resource identification of the generated payment initiation resource. | [default to null]
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **PSU-ID** | **String**| Client ID of the PSU in the ASPSP client interface.  Might be mandated in the ASPSP&#39;s documentation.  It might be contained even if an OAuth2 based authentication was performed in a pre-step or an OAuth2 based SCA was performed in an preceding AIS service in the same session. In this case the ASPSP might check whether PSU-ID and token match, according to ASPSP documentation.  | [optional] [default to null]
 **PSU-ID-Type** | **String**| Type of the PSU-ID, needed in scenarios where PSUs have several PSU-IDs as access possibility.  In this case, the mean and use are then defined in the ASPSP&#39;s documentation.  | [optional] [default to null]
 **PSU-Corporate-ID** | **String**| Might be mandated in the ASPSP&#39;s documentation. Only used in a corporate context.  | [optional] [default to null]
 **PSU-Corporate-ID-Type** | **String**| Might be mandated in the ASPSP&#39;s documentation. Only used in a corporate context.  | [optional] [default to null]
 **TPP-Redirect-Preferred** | **String**| If it equals \&quot;true\&quot;, the TPP prefers a redirect over an embedded SCA approach. If it equals \&quot;false\&quot;, the TPP prefers not to be redirected for SCA. The ASPSP will then choose between the Embedded or the Decoupled SCA approach, depending on the choice of the SCA procedure by the TPP/PSU. If the parameter is not used, the ASPSP will choose the SCA approach to be applied depending on the SCA method chosen by the TPP/PSU.  | [optional] [default to null] [enum: true, false]
 **TPP-Redirect-URI** | **URI**| URI of the TPP, where the transaction flow shall be redirected to after a Redirect.  Mandated for the Redirect SCA Approach, specifically when TPP-Redirect-Preferred equals \&quot;true\&quot;. It is recommended to always use this header field.  **Remark for Future:** This field might be changed to mandatory in the next version of the specification.  | [optional] [default to null]
 **TPP-Nok-Redirect-URI** | **URI**| If this URI is contained, the TPP is asking to redirect the transaction flow to this address instead of the TPP-Redirect-URI in case of a negative result of the redirect SCA method. This might be ignored by the ASPSP.  | [optional] [default to null]
 **TPP-Notification-URI** | **String**| URI for the Endpoint of the TPP-API to which the status of the payment initiation should be sent. This header field may by ignored by the ASPSP.  For security reasons, it shall be ensured that the TPP-Notification-URI as introduced above is secured by the TPP eIDAS QWAC used for identification of the TPP. The following applies:  URIs which are provided by TPPs in TPP-Notification-URI shall comply with the domain secured by the eIDAS QWAC certificate of the TPP in the field CN or SubjectAltName of the certificate. Please note that in case of example-TPP.com as certificate entry TPP- Notification-URI like www.example-TPP.com/xs2a-client/v1/ASPSPidentifcation/mytransaction- id/notifications or notifications.example-TPP.com/xs2a-client/v1/ASPSPidentifcation/mytransaction- id/notifications would be compliant.  Wildcard definitions shall be taken into account for compliance checks by the ASPSP.  ASPSPs may respond with ASPSP-Notification-Support set to false, if the provided URIs do not comply.  | [optional] [default to null]
 **TPP-Notification-Content-Preferred** | **String**| The string has the form  status&#x3D;X1, ..., Xn  where Xi is one of the constants SCA, PROCESS, LAST and where constants are not repeated. The usage of the constants supports the of following semantics:    SCA: A notification on every change of the scaStatus attribute for all related authorisation processes is preferred by the TPP.    PROCESS: A notification on all changes of consentStatus or transactionStatus attributes is preferred by the TPP.   LAST: Only a notification on the last consentStatus or transactionStatus as available in the XS2A interface is preferred by the TPP.  This header field may be ignored, if the ASPSP does not support resource notification services for the related TPP.  | [optional] [default to null]
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
 **UNKNOWN\_BASE\_TYPE** | [**UNKNOWN_BASE_TYPE**](../Models/UNKNOWN_BASE_TYPE.md)|  | [optional]

### Return type

[**startScaprocessResponse**](../Models/startScaprocessResponse.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json, application/problem+json

<a name="startPaymentInitiationCancellationAuthorisation"></a>
# **startPaymentInitiationCancellationAuthorisation**
> startScaprocessResponse startPaymentInitiationCancellationAuthorisation(payment-service, payment-product, paymentId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-ID, PSU-ID-Type, PSU-Corporate-ID, PSU-Corporate-ID-Type, TPP-Redirect-Preferred, TPP-Redirect-URI, TPP-Nok-Redirect-URI, TPP-Notification-URI, TPP-Notification-Content-Preferred, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location)

Start the authorisation process for the cancellation of the addressed payment

    Creates an authorisation sub-resource and start the authorisation process of the cancellation of the addressed payment. The message might in addition transmit authentication and authorisation related data.  This method is iterated n times for a n times SCA authorisation in a corporate context, each creating an own authorisation sub-endpoint for the corresponding PSU authorising the cancellation-authorisation.  The ASPSP might make the usage of this access method unnecessary in case of only one SCA process needed, since the related authorisation resource might be automatically created by the ASPSP after the submission of the payment data with the first POST payments/{payment-product} call.  The start authorisation process is a process which is needed for creating a new authorisation or cancellation sub-resource.  This applies in the following scenarios:    * The ASPSP has indicated with an &#39;startAuthorisation&#39; hyperlink in the preceding Payment     Initiation Response that an explicit start of the authorisation process is needed by the TPP.     The &#39;startAuthorisation&#39; hyperlink can transport more information about data which needs to be     uploaded by using the extended forms.     * &#39;startAuthorisationWithPsuIdentfication&#39;,     * &#39;startAuthorisationWithPsuAuthentication&#39;     * &#39;startAuthorisationWithAuthentciationMethodSelection&#39;   * The related payment initiation cannot yet be executed since a multilevel SCA is mandated.   * The ASPSP has indicated with an &#39;startAuthorisation&#39; hyperlink in the preceding     Payment Cancellation Response that an explicit start of the authorisation process is needed by the TPP.     The &#39;startAuthorisation&#39; hyperlink can transport more information about data which needs to be uploaded     by using the extended forms as indicated above.   * The related payment cancellation request cannot be applied yet since a multilevel SCA is mandate for     executing the cancellation.   * The signing basket needs to be authorised yet. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **payment-service** | **String**| Payment service:  Possible values are: * payments * bulk-payments * periodic-payments  | [default to null] [enum: payments, bulk-payments, periodic-payments]
 **payment-product** | **String**| The addressed payment product endpoint, e.g. for SEPA Credit Transfers (SCT). The ASPSP will publish which of the payment products/endpoints will be supported.  The following payment products are supported:   - sepa-credit-transfers   - cross-border-credit-transfers   - domestic-swiss-credit-transfers   - domestic-swiss-credit-transfers-isr   - domestic-swiss-foreign-credit-transfers   - pain.001-sepa-credit-transfers   - pain.001-cross-border-credit-transfers   - pain.001-swiss-six-credit-transfers  **Remark:** For all SEPA Credit Transfer based endpoints which accept XML encoding, the XML pain.001 schemes provided by EPC are supported by the ASPSP as a minimum for the body content. Further XML schemes might be supported by some communities.  **Remark:** For cross-border and TARGET-2 payments only community wide pain.001 schemes do exist. There are plenty of country specificic scheme variants.  | [default to null] [enum: sepa-credit-transfers, cross-border-credit-transfers, domestic-swiss-credit-transfers, domestic-swiss-credit-transfers-isr, domestic-swiss-foreign-credit-transfers, pain.001-sepa-credit-transfers, pain.001-cross-border-credit-transfers, pain.001-swiss-six-credit-transfers]
 **paymentId** | **String**| Resource identification of the generated payment initiation resource. | [default to null]
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

### Return type

[**startScaprocessResponse**](../Models/startScaprocessResponse.md)

### Authorization

[BearerAuthOAuth](../README.md#BearerAuthOAuth)

### HTTP request headers

- **Content-Type**: Not defined
- **Accept**: application/json, application/problem+json

<a name="updatePaymentCancellationPsuData"></a>
# **updatePaymentCancellationPsuData**
> oneOf&lt;updatePsuIdenticationResponse,updatePsuAuthenticationResponse,selectPsuAuthenticationMethodResponse,scaStatusResponse&gt; updatePaymentCancellationPsuData(payment-service, payment-product, paymentId, cancellationId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-ID, PSU-ID-Type, PSU-Corporate-ID, PSU-Corporate-ID-Type, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location, UNKNOWN\_BASE\_TYPE)

Update PSU Data for payment initiation cancellation

    This method updates PSU data on the cancellation authorisation resource if needed. It may authorise a cancellation of the payment within the Embedded SCA Approach where needed.  Independently from the SCA Approach it supports e.g. the selection of the authentication method and a non-SCA PSU authentication.  This methods updates PSU data on the cancellation authorisation resource if needed.  There are several possible Update PSU Data requests in the context of a cancellation authorisation within the payment initiation services needed, which depends on the SCA approach:  * Redirect SCA Approach:   A specific Update PSU Data Request is applicable for     * the selection of authentication methods, before choosing the actual SCA approach. * Decoupled SCA Approach:   A specific Update PSU Data Request is only applicable for   * adding the PSU Identification, if not provided yet in the Payment Initiation Request or the Account Information Consent Request, or if no OAuth2 access token is used, or   * the selection of authentication methods. * Embedded SCA Approach:   The Update PSU Data Request might be used   * to add credentials as a first factor authentication data of the PSU and   * to select the authentication method and   * transaction authorisation.  The SCA Approach might depend on the chosen SCA method. For that reason, the following possible Update PSU Data request can apply to all SCA approaches:  * Select an SCA method in case of several SCA methods are available for the customer.  There are the following request types on this access path:   * Update PSU Identification   * Update PSU Authentication   * Select PSU Autorization Method     WARNING: This method need a reduced header,     therefore many optional elements are not present.     Maybe in a later version the access path will change.   * Transaction Authorisation     WARNING: This method need a reduced header,     therefore many optional elements are not present.     Maybe in a later version the access path will change. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **payment-service** | **String**| Payment service:  Possible values are: * payments * bulk-payments * periodic-payments  | [default to null] [enum: payments, bulk-payments, periodic-payments]
 **payment-product** | **String**| The addressed payment product endpoint, e.g. for SEPA Credit Transfers (SCT). The ASPSP will publish which of the payment products/endpoints will be supported.  The following payment products are supported:   - sepa-credit-transfers   - cross-border-credit-transfers   - domestic-swiss-credit-transfers   - domestic-swiss-credit-transfers-isr   - domestic-swiss-foreign-credit-transfers   - pain.001-sepa-credit-transfers   - pain.001-cross-border-credit-transfers   - pain.001-swiss-six-credit-transfers  **Remark:** For all SEPA Credit Transfer based endpoints which accept XML encoding, the XML pain.001 schemes provided by EPC are supported by the ASPSP as a minimum for the body content. Further XML schemes might be supported by some communities.  **Remark:** For cross-border and TARGET-2 payments only community wide pain.001 schemes do exist. There are plenty of country specificic scheme variants.  | [default to null] [enum: sepa-credit-transfers, cross-border-credit-transfers, domestic-swiss-credit-transfers, domestic-swiss-credit-transfers-isr, domestic-swiss-foreign-credit-transfers, pain.001-sepa-credit-transfers, pain.001-cross-border-credit-transfers, pain.001-swiss-six-credit-transfers]
 **paymentId** | **String**| Resource identification of the generated payment initiation resource. | [default to null]
 **cancellationId** | **String**| Identification for cancellation resource. | [default to null]
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

<a name="updatePaymentPsuData"></a>
# **updatePaymentPsuData**
> oneOf&lt;updatePsuIdenticationResponse,updatePsuAuthenticationResponse,selectPsuAuthenticationMethodResponse,scaStatusResponse&gt; updatePaymentPsuData(payment-service, payment-product, paymentId, authorisationId, X-Request-ID, Digest, Signature, TPP-Signature-Certificate, PSU-ID, PSU-ID-Type, PSU-Corporate-ID, PSU-Corporate-ID-Type, PSU-IP-Address, PSU-IP-Port, PSU-Accept, PSU-Accept-Charset, PSU-Accept-Encoding, PSU-Accept-Language, PSU-User-Agent, PSU-Http-Method, PSU-Device-ID, PSU-Geo-Location, UNKNOWN\_BASE\_TYPE)

Update PSU data for payment initiation

    This methods updates PSU data on the authorisation resource if needed. It may authorise a payment within the Embedded SCA Approach where needed.  Independently from the SCA Approach it supports e.g. the selection of the authentication method and a non-SCA PSU authentication.  There are several possible Update PSU Data requests in the context of payment initiation services needed, which depends on the SCA approach:  * Redirect SCA Approach:   A specific Update PSU Data Request is applicable for     * the selection of authentication methods, before choosing the actual SCA approach. * Decoupled SCA Approach:   A specific Update PSU Data Request is only applicable for   * adding the PSU Identification, if not provided yet in the Payment Initiation Request or the Account Information Consent Request, or if no OAuth2 access token is used, or   * the selection of authentication methods. * Embedded SCA Approach:   The Update PSU Data Request might be used   * to add credentials as a first factor authentication data of the PSU and   * to select the authentication method and   * transaction authorisation.  The SCA Approach might depend on the chosen SCA method. For that reason, the following possible Update PSU Data request can apply to all SCA approaches:  * Select an SCA method in case of several SCA methods are available for the customer.  There are the following request types on this access path:   * Update PSU Identification   * Update PSU Authentication   * Select PSU Autorization Method     WARNING: This method need a reduced header,     therefore many optional elements are not present.     Maybe in a later version the access path will change.   * Transaction Authorisation     WARNING: This method need a reduced header,     therefore many optional elements are not present.     Maybe in a later version the access path will change. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **payment-service** | **String**| Payment service:  Possible values are: * payments * bulk-payments * periodic-payments  | [default to null] [enum: payments, bulk-payments, periodic-payments]
 **payment-product** | **String**| The addressed payment product endpoint, e.g. for SEPA Credit Transfers (SCT). The ASPSP will publish which of the payment products/endpoints will be supported.  The following payment products are supported:   - sepa-credit-transfers   - cross-border-credit-transfers   - domestic-swiss-credit-transfers   - domestic-swiss-credit-transfers-isr   - domestic-swiss-foreign-credit-transfers   - pain.001-sepa-credit-transfers   - pain.001-cross-border-credit-transfers   - pain.001-swiss-six-credit-transfers  **Remark:** For all SEPA Credit Transfer based endpoints which accept XML encoding, the XML pain.001 schemes provided by EPC are supported by the ASPSP as a minimum for the body content. Further XML schemes might be supported by some communities.  **Remark:** For cross-border and TARGET-2 payments only community wide pain.001 schemes do exist. There are plenty of country specificic scheme variants.  | [default to null] [enum: sepa-credit-transfers, cross-border-credit-transfers, domestic-swiss-credit-transfers, domestic-swiss-credit-transfers-isr, domestic-swiss-foreign-credit-transfers, pain.001-sepa-credit-transfers, pain.001-cross-border-credit-transfers, pain.001-swiss-six-credit-transfers]
 **paymentId** | **String**| Resource identification of the generated payment initiation resource. | [default to null]
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

