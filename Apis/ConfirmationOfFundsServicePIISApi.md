# ConfirmationOfFundsServicePIISApi

All URIs are relative to *https://api.dev.openbankingproject.ch*

Method | HTTP request | Description
------------- | ------------- | -------------
[**checkAvailabilityOfFunds**](ConfirmationOfFundsServicePIISApi.md#checkAvailabilityOfFunds) | **POST** /v1/funds-confirmations | Confirmation of Funds Request


<a name="checkAvailabilityOfFunds"></a>
# **checkAvailabilityOfFunds**
> inline_response_200 checkAvailabilityOfFunds(X-Request-ID, ConfirmationOfFunds, Authorization, Digest, Signature, TPP-Signature-Certificate)

Confirmation of Funds Request

    Creates a confirmation of funds request at the ASPSP. Checks whether a specific amount is available at point of time of the request on an account linked to a given tuple card issuer(TPP)/card number, or addressed by IBAN and TPP respectively.  If the related extended services are used a conditional Consent-ID is contained in the header. This field is contained but commented out in this specification. 

### Parameters

Name | Type | Description  | Notes
------------- | ------------- | ------------- | -------------
 **X-Request-ID** | **String**| ID of the request, unique to the call, as determined by the initiating party. | [default to null]
 **ConfirmationOfFunds** | [**ConfirmationOfFunds**](../Models/ConfirmationOfFunds.md)| Request body for a confirmation of funds request.  |
 **Authorization** | **String**| This field  might be used in case where a consent was agreed between ASPSP and PSU through an OAuth2 based protocol, facilitated by the TPP.  | [optional] [default to null]
 **Digest** | **String**| Is contained if and only if the \&quot;Signature\&quot; element is contained in the header of the request. | [optional] [default to null]
 **Signature** | **String**| A signature of the request by the TPP on application level. This might be mandated by ASPSP.  | [optional] [default to null]
 **TPP-Signature-Certificate** | **byte[]**| The certificate used for signing the request, in base64 encoding. Must be contained if a signature is contained.  | [optional] [default to null]

### Return type

[**inline_response_200**](../Models/inline_response_200.md)

### Authorization

No authorization required

### HTTP request headers

- **Content-Type**: application/json
- **Accept**: application/json, application/problem+json

