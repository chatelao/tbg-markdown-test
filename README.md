# Documentation for Swiss NextGen Banking API-Framework

<a name="documentation-for-api-endpoints"></a>
## Documentation for API Endpoints

All URIs are relative to *https://api.dev.openbankingproject.ch*

Class | Method | HTTP request | Description
------------ | ------------- | ------------- | -------------
*AccountInformationServiceAISApi* | [**createConsent**](Apis/AccountInformationServiceAISApi.md#createconsent) | **POST** /v1/consents | Create consent
*AccountInformationServiceAISApi* | [**deleteConsent**](Apis/AccountInformationServiceAISApi.md#deleteconsent) | **DELETE** /v1/consents/{consentId} | Delete Consent
*AccountInformationServiceAISApi* | [**getAccountList**](Apis/AccountInformationServiceAISApi.md#getaccountlist) | **GET** /v1/accounts | Read Account List
*AccountInformationServiceAISApi* | [**getBalances**](Apis/AccountInformationServiceAISApi.md#getbalances) | **GET** /v1/accounts/{account-id}/balances | Read Balance
*AccountInformationServiceAISApi* | [**getConsentAuthorisation**](Apis/AccountInformationServiceAISApi.md#getconsentauthorisation) | **GET** /v1/consents/{consentId}/authorisations | Get Consent Authorisation Sub-Resources Request
*AccountInformationServiceAISApi* | [**getConsentInformation**](Apis/AccountInformationServiceAISApi.md#getconsentinformation) | **GET** /v1/consents/{consentId} | Get Consent Request
*AccountInformationServiceAISApi* | [**getConsentScaStatus**](Apis/AccountInformationServiceAISApi.md#getconsentscastatus) | **GET** /v1/consents/{consentId}/authorisations/{authorisationId} | Read the SCA status of the consent authorisation.
*AccountInformationServiceAISApi* | [**getConsentStatus**](Apis/AccountInformationServiceAISApi.md#getconsentstatus) | **GET** /v1/consents/{consentId}/status | Consent status request
*AccountInformationServiceAISApi* | [**getTransactionDetails**](Apis/AccountInformationServiceAISApi.md#gettransactiondetails) | **GET** /v1/accounts/{account-id}/transactions/{transactionId} | Read Transaction Details
*AccountInformationServiceAISApi* | [**getTransactionList**](Apis/AccountInformationServiceAISApi.md#gettransactionlist) | **GET** /v1/accounts/{account-id}/transactions | Read transaction list of an account
*AccountInformationServiceAISApi* | [**readAccountDetails**](Apis/AccountInformationServiceAISApi.md#readaccountdetails) | **GET** /v1/accounts/{account-id} | Read Account Details
*AccountInformationServiceAISApi* | [**startConsentAuthorisation**](Apis/AccountInformationServiceAISApi.md#startconsentauthorisation) | **POST** /v1/consents/{consentId}/authorisations | Start the authorisation process for a consent
*AccountInformationServiceAISApi* | [**updateConsentsPsuData**](Apis/AccountInformationServiceAISApi.md#updateconsentspsudata) | **PUT** /v1/consents/{consentId}/authorisations/{authorisationId} | Update PSU Data for consents
*CommonServicesApi* | [**deleteSigningBasket**](Apis/CommonServicesApi.md#deletesigningbasket) | **DELETE** /v1/signing-baskets/{basketId} | Delete the signing basket
*CommonServicesApi* | [**getConsentScaStatus**](Apis/CommonServicesApi.md#getconsentscastatus) | **GET** /v1/consents/{consentId}/authorisations/{authorisationId} | Read the SCA status of the consent authorisation.
*CommonServicesApi* | [**getPaymentCancellationScaStatus**](Apis/CommonServicesApi.md#getpaymentcancellationscastatus) | **GET** /v1/{payment-service}/{payment-product}/{paymentId}/cancellation-authorisations/{cancellationId} | Read the SCA status of the payment cancellation's authorisation.
*CommonServicesApi* | [**getPaymentInitiationAuthorisation**](Apis/CommonServicesApi.md#getpaymentinitiationauthorisation) | **GET** /v1/{payment-service}/{payment-product}/{paymentId}/authorisations | Get Payment Initiation Authorisation Sub-Resources Request
*CommonServicesApi* | [**getPaymentInitiationScaStatus**](Apis/CommonServicesApi.md#getpaymentinitiationscastatus) | **GET** /v1/{payment-service}/{payment-product}/{paymentId}/authorisations/{authorisationId} | Read the SCA Status of the payment authorisation
*CommonServicesApi* | [**getSigningBasketAuthorisation**](Apis/CommonServicesApi.md#getsigningbasketauthorisation) | **GET** /v1/signing-baskets/{basketId}/authorisations | Get Signing Basket Authorisation Sub-Resources Request
*CommonServicesApi* | [**getSigningBasketScaStatus**](Apis/CommonServicesApi.md#getsigningbasketscastatus) | **GET** /v1/signing-baskets/{basketId}/authorisations/{authorisationId} | Read the SCA status of the signing basket authorisation
*CommonServicesApi* | [**getSigningBasketStatus**](Apis/CommonServicesApi.md#getsigningbasketstatus) | **GET** /v1/signing-baskets/{basketId}/status | Read the status of the signing basket
*CommonServicesApi* | [**startConsentAuthorisation**](Apis/CommonServicesApi.md#startconsentauthorisation) | **POST** /v1/consents/{consentId}/authorisations | Start the authorisation process for a consent
*CommonServicesApi* | [**startPaymentAuthorisation**](Apis/CommonServicesApi.md#startpaymentauthorisation) | **POST** /v1/{payment-service}/{payment-product}/{paymentId}/authorisations | Start the authorisation process for a payment initiation
*CommonServicesApi* | [**startPaymentInitiationCancellationAuthorisation**](Apis/CommonServicesApi.md#startpaymentinitiationcancellationauthorisation) | **POST** /v1/{payment-service}/{payment-product}/{paymentId}/cancellation-authorisations | Start the authorisation process for the cancellation of the addressed payment
*CommonServicesApi* | [**startSigningBasketAuthorisation**](Apis/CommonServicesApi.md#startsigningbasketauthorisation) | **POST** /v1/signing-baskets/{basketId}/authorisations | Start the authorisation process for a signing basket
*CommonServicesApi* | [**updateConsentsPsuData**](Apis/CommonServicesApi.md#updateconsentspsudata) | **PUT** /v1/consents/{consentId}/authorisations/{authorisationId} | Update PSU Data for consents
*CommonServicesApi* | [**updatePaymentCancellationPsuData**](Apis/CommonServicesApi.md#updatepaymentcancellationpsudata) | **PUT** /v1/{payment-service}/{payment-product}/{paymentId}/cancellation-authorisations/{cancellationId} | Update PSU Data for payment initiation cancellation
*CommonServicesApi* | [**updatePaymentPsuData**](Apis/CommonServicesApi.md#updatepaymentpsudata) | **PUT** /v1/{payment-service}/{payment-product}/{paymentId}/authorisations/{authorisationId} | Update PSU data for payment initiation
*CommonServicesApi* | [**updateSigningBasketPsuData**](Apis/CommonServicesApi.md#updatesigningbasketpsudata) | **PUT** /v1/signing-baskets/{basketId}/authorisations/{authorisationId} | Update PSU Data for signing basket
*ConfirmationOfFundsServicePIISApi* | [**checkAvailabilityOfFunds**](Apis/ConfirmationOfFundsServicePIISApi.md#checkavailabilityoffunds) | **POST** /v1/funds-confirmations | Confirmation of Funds Request
*PaymentInitiationServicePISApi* | [**cancelPayment**](Apis/PaymentInitiationServicePISApi.md#cancelpayment) | **DELETE** /v1/{payment-service}/{payment-product}/{paymentId} | Payment Cancellation Request
*PaymentInitiationServicePISApi* | [**getPaymentCancellationScaStatus**](Apis/PaymentInitiationServicePISApi.md#getpaymentcancellationscastatus) | **GET** /v1/{payment-service}/{payment-product}/{paymentId}/cancellation-authorisations/{cancellationId} | Read the SCA status of the payment cancellation's authorisation.
*PaymentInitiationServicePISApi* | [**getPaymentInformation**](Apis/PaymentInitiationServicePISApi.md#getpaymentinformation) | **GET** /v1/{payment-service}/{payment-product}/{paymentId} | Get Payment Information
*PaymentInitiationServicePISApi* | [**getPaymentInitiationAuthorisation**](Apis/PaymentInitiationServicePISApi.md#getpaymentinitiationauthorisation) | **GET** /v1/{payment-service}/{payment-product}/{paymentId}/authorisations | Get Payment Initiation Authorisation Sub-Resources Request
*PaymentInitiationServicePISApi* | [**getPaymentInitiationCancellationAuthorisationInformation**](Apis/PaymentInitiationServicePISApi.md#getpaymentinitiationcancellationauthorisationinformation) | **GET** /v1/{payment-service}/{payment-product}/{paymentId}/cancellation-authorisations | Will deliver an array of resource identifications to all generated cancellation authorisation sub-resources.
*PaymentInitiationServicePISApi* | [**getPaymentInitiationScaStatus**](Apis/PaymentInitiationServicePISApi.md#getpaymentinitiationscastatus) | **GET** /v1/{payment-service}/{payment-product}/{paymentId}/authorisations/{authorisationId} | Read the SCA Status of the payment authorisation
*PaymentInitiationServicePISApi* | [**getPaymentInitiationStatus**](Apis/PaymentInitiationServicePISApi.md#getpaymentinitiationstatus) | **GET** /v1/{payment-service}/{payment-product}/{paymentId}/status | Payment initiation status request
*PaymentInitiationServicePISApi* | [**initiatePayment**](Apis/PaymentInitiationServicePISApi.md#initiatepayment) | **POST** /v1/{payment-service}/{payment-product} | Payment initiation request
*PaymentInitiationServicePISApi* | [**startPaymentAuthorisation**](Apis/PaymentInitiationServicePISApi.md#startpaymentauthorisation) | **POST** /v1/{payment-service}/{payment-product}/{paymentId}/authorisations | Start the authorisation process for a payment initiation
*PaymentInitiationServicePISApi* | [**startPaymentInitiationCancellationAuthorisation**](Apis/PaymentInitiationServicePISApi.md#startpaymentinitiationcancellationauthorisation) | **POST** /v1/{payment-service}/{payment-product}/{paymentId}/cancellation-authorisations | Start the authorisation process for the cancellation of the addressed payment
*PaymentInitiationServicePISApi* | [**updatePaymentCancellationPsuData**](Apis/PaymentInitiationServicePISApi.md#updatepaymentcancellationpsudata) | **PUT** /v1/{payment-service}/{payment-product}/{paymentId}/cancellation-authorisations/{cancellationId} | Update PSU Data for payment initiation cancellation
*PaymentInitiationServicePISApi* | [**updatePaymentPsuData**](Apis/PaymentInitiationServicePISApi.md#updatepaymentpsudata) | **PUT** /v1/{payment-service}/{payment-product}/{paymentId}/authorisations/{authorisationId} | Update PSU data for payment initiation
*SigningBasketsServiceSBSApi* | [**createSigningBasket**](Apis/SigningBasketsServiceSBSApi.md#createsigningbasket) | **POST** /v1/signing-baskets | Create a signing basket resource
*SigningBasketsServiceSBSApi* | [**deleteSigningBasket**](Apis/SigningBasketsServiceSBSApi.md#deletesigningbasket) | **DELETE** /v1/signing-baskets/{basketId} | Delete the signing basket
*SigningBasketsServiceSBSApi* | [**getSigningBasket**](Apis/SigningBasketsServiceSBSApi.md#getsigningbasket) | **GET** /v1/signing-baskets/{basketId} | Returns the content of an signing basket object.
*SigningBasketsServiceSBSApi* | [**getSigningBasketAuthorisation**](Apis/SigningBasketsServiceSBSApi.md#getsigningbasketauthorisation) | **GET** /v1/signing-baskets/{basketId}/authorisations | Get Signing Basket Authorisation Sub-Resources Request
*SigningBasketsServiceSBSApi* | [**getSigningBasketScaStatus**](Apis/SigningBasketsServiceSBSApi.md#getsigningbasketscastatus) | **GET** /v1/signing-baskets/{basketId}/authorisations/{authorisationId} | Read the SCA status of the signing basket authorisation
*SigningBasketsServiceSBSApi* | [**getSigningBasketStatus**](Apis/SigningBasketsServiceSBSApi.md#getsigningbasketstatus) | **GET** /v1/signing-baskets/{basketId}/status | Read the status of the signing basket
*SigningBasketsServiceSBSApi* | [**startSigningBasketAuthorisation**](Apis/SigningBasketsServiceSBSApi.md#startsigningbasketauthorisation) | **POST** /v1/signing-baskets/{basketId}/authorisations | Start the authorisation process for a signing basket
*SigningBasketsServiceSBSApi* | [**updateSigningBasketPsuData**](Apis/SigningBasketsServiceSBSApi.md#updatesigningbasketpsudata) | **PUT** /v1/signing-baskets/{basketId}/authorisations/{authorisationId} | Update PSU Data for signing basket


<a name="documentation-for-models"></a>
## Documentation for Models

 - [AccountAccess](./Models/AccountAccess.md)
 - [AccountDetails](./Models/AccountDetails.md)
 - [AccountList](./Models/AccountList.md)
 - [AccountReference16CH](./Models/AccountReference16CH.md)
 - [AccountReport](./Models/AccountReport.md)
 - [AccountStatus](./Models/AccountStatus.md)
 - [Address](./Models/Address.md)
 - [Amount](./Models/Amount.md)
 - [AuthenticationObject](./Models/AuthenticationObject.md)
 - [AuthenticationType](./Models/AuthenticationType.md)
 - [Authorisations](./Models/Authorisations.md)
 - [Balance](./Models/Balance.md)
 - [BalanceType](./Models/BalanceType.md)
 - [BulkPaymentInitiationJson](./Models/BulkPaymentInitiationJson.md)
 - [BulkPaymentInitiationWithStatusResponse](./Models/BulkPaymentInitiationWithStatusResponse.md)
 - [CardAccountDetails](./Models/CardAccountDetails.md)
 - [CardAccountList](./Models/CardAccountList.md)
 - [CardAccountReport](./Models/CardAccountReport.md)
 - [CardAccountsTransactionsResponse200](./Models/CardAccountsTransactionsResponse200.md)
 - [CardTransaction](./Models/CardTransaction.md)
 - [ChallengeData](./Models/ChallengeData.md)
 - [ChargeBearer](./Models/ChargeBearer.md)
 - [ConfirmationOfFunds](./Models/ConfirmationOfFunds.md)
 - [ConsentInformationResponse200Json](./Models/ConsentInformationResponse200Json.md)
 - [ConsentStatus](./Models/ConsentStatus.md)
 - [ConsentStatusResponse200](./Models/ConsentStatusResponse200.md)
 - [Consents](./Models/Consents.md)
 - [ConsentsResponse201](./Models/ConsentsResponse201.md)
 - [CreditorAgent7CH](./Models/CreditorAgent7CH.md)
 - [DayOfExecution](./Models/DayOfExecution.md)
 - [DeptorAgent7CH](./Models/DeptorAgent7CH.md)
 - [Error400AIS](./Models/Error400AIS.md)
 - [Error400AISAdditionalErrors](./Models/Error400AISAdditionalErrors.md)
 - [Error400NGAIS](./Models/Error400NGAIS.md)
 - [Error400NGPIIS](./Models/Error400NGPIIS.md)
 - [Error400NGPIS](./Models/Error400NGPIS.md)
 - [Error400NGSBS](./Models/Error400NGSBS.md)
 - [Error400PIIS](./Models/Error400PIIS.md)
 - [Error400PIISAdditionalErrors](./Models/Error400PIISAdditionalErrors.md)
 - [Error400PIS](./Models/Error400PIS.md)
 - [Error400PISAdditionalErrors](./Models/Error400PISAdditionalErrors.md)
 - [Error400SBS](./Models/Error400SBS.md)
 - [Error400SBSAdditionalErrors](./Models/Error400SBSAdditionalErrors.md)
 - [Error401AIS](./Models/Error401AIS.md)
 - [Error401AISAdditionalErrors](./Models/Error401AISAdditionalErrors.md)
 - [Error401NGAIS](./Models/Error401NGAIS.md)
 - [Error401NGPIIS](./Models/Error401NGPIIS.md)
 - [Error401NGPIS](./Models/Error401NGPIS.md)
 - [Error401NGSBS](./Models/Error401NGSBS.md)
 - [Error401PIIS](./Models/Error401PIIS.md)
 - [Error401PIISAdditionalErrors](./Models/Error401PIISAdditionalErrors.md)
 - [Error401PIS](./Models/Error401PIS.md)
 - [Error401PISAdditionalErrors](./Models/Error401PISAdditionalErrors.md)
 - [Error401SBS](./Models/Error401SBS.md)
 - [Error401SBSAdditionalErrors](./Models/Error401SBSAdditionalErrors.md)
 - [Error403AIS](./Models/Error403AIS.md)
 - [Error403AISAdditionalErrors](./Models/Error403AISAdditionalErrors.md)
 - [Error403NGAIS](./Models/Error403NGAIS.md)
 - [Error403NGPIIS](./Models/Error403NGPIIS.md)
 - [Error403NGPIS](./Models/Error403NGPIS.md)
 - [Error403NGSBS](./Models/Error403NGSBS.md)
 - [Error403PIIS](./Models/Error403PIIS.md)
 - [Error403PIISAdditionalErrors](./Models/Error403PIISAdditionalErrors.md)
 - [Error403PIS](./Models/Error403PIS.md)
 - [Error403PISAdditionalErrors](./Models/Error403PISAdditionalErrors.md)
 - [Error403SBS](./Models/Error403SBS.md)
 - [Error403SBSAdditionalErrors](./Models/Error403SBSAdditionalErrors.md)
 - [Error404AIS](./Models/Error404AIS.md)
 - [Error404AISAdditionalErrors](./Models/Error404AISAdditionalErrors.md)
 - [Error404NGAIS](./Models/Error404NGAIS.md)
 - [Error404NGPIIS](./Models/Error404NGPIIS.md)
 - [Error404NGPIS](./Models/Error404NGPIS.md)
 - [Error404NGSBS](./Models/Error404NGSBS.md)
 - [Error404PIIS](./Models/Error404PIIS.md)
 - [Error404PIISAdditionalErrors](./Models/Error404PIISAdditionalErrors.md)
 - [Error404PIS](./Models/Error404PIS.md)
 - [Error404PISAdditionalErrors](./Models/Error404PISAdditionalErrors.md)
 - [Error404SBS](./Models/Error404SBS.md)
 - [Error404SBSAdditionalErrors](./Models/Error404SBSAdditionalErrors.md)
 - [Error405AIS](./Models/Error405AIS.md)
 - [Error405AISAdditionalErrors](./Models/Error405AISAdditionalErrors.md)
 - [Error405NGAIS](./Models/Error405NGAIS.md)
 - [Error405NGPIIS](./Models/Error405NGPIIS.md)
 - [Error405NGPIS](./Models/Error405NGPIS.md)
 - [Error405NGPISCANC](./Models/Error405NGPISCANC.md)
 - [Error405NGSBS](./Models/Error405NGSBS.md)
 - [Error405PIIS](./Models/Error405PIIS.md)
 - [Error405PIISAdditionalErrors](./Models/Error405PIISAdditionalErrors.md)
 - [Error405PIS](./Models/Error405PIS.md)
 - [Error405PISAdditionalErrors](./Models/Error405PISAdditionalErrors.md)
 - [Error405PISCANC](./Models/Error405PISCANC.md)
 - [Error405PISCANCAdditionalErrors](./Models/Error405PISCANCAdditionalErrors.md)
 - [Error405SBS](./Models/Error405SBS.md)
 - [Error405SBSAdditionalErrors](./Models/Error405SBSAdditionalErrors.md)
 - [Error406AIS](./Models/Error406AIS.md)
 - [Error406AISAdditionalErrors](./Models/Error406AISAdditionalErrors.md)
 - [Error406NGAIS](./Models/Error406NGAIS.md)
 - [Error409AIS](./Models/Error409AIS.md)
 - [Error409AISAdditionalErrors](./Models/Error409AISAdditionalErrors.md)
 - [Error409NGAIS](./Models/Error409NGAIS.md)
 - [Error409NGPIIS](./Models/Error409NGPIIS.md)
 - [Error409NGPIS](./Models/Error409NGPIS.md)
 - [Error409NGSBS](./Models/Error409NGSBS.md)
 - [Error409PIIS](./Models/Error409PIIS.md)
 - [Error409PIISAdditionalErrors](./Models/Error409PIISAdditionalErrors.md)
 - [Error409PIS](./Models/Error409PIS.md)
 - [Error409PISAdditionalErrors](./Models/Error409PISAdditionalErrors.md)
 - [Error409SBS](./Models/Error409SBS.md)
 - [Error409SBSAdditionalErrors](./Models/Error409SBSAdditionalErrors.md)
 - [Error429AIS](./Models/Error429AIS.md)
 - [Error429AISAdditionalErrors](./Models/Error429AISAdditionalErrors.md)
 - [Error429NGAIS](./Models/Error429NGAIS.md)
 - [ExchangeRateInformation1](./Models/ExchangeRateInformation1.md)
 - [ExecutionRule](./Models/ExecutionRule.md)
 - [ExternalServiceLevel1Code](./Models/ExternalServiceLevel1Code.md)
 - [FrequencyCode](./Models/FrequencyCode.md)
 - [HrefType](./Models/HrefType.md)
 - [InlineResponse200](./Models/InlineResponse200.md)
 - [InstitutionalIdentification2](./Models/InstitutionalIdentification2.md)
 - [LinksAccountDetails](./Models/LinksAccountDetails.md)
 - [LinksAccountReport](./Models/LinksAccountReport.md)
 - [LinksAll](./Models/LinksAll.md)
 - [LinksCardAccountReport](./Models/LinksCardAccountReport.md)
 - [LinksConsents](./Models/LinksConsents.md)
 - [LinksDownload](./Models/LinksDownload.md)
 - [LinksGetConsent](./Models/LinksGetConsent.md)
 - [LinksPaymentInitiation](./Models/LinksPaymentInitiation.md)
 - [LinksPaymentInitiationCancel](./Models/LinksPaymentInitiationCancel.md)
 - [LinksSelectPsuAuthenticationMethod](./Models/LinksSelectPsuAuthenticationMethod.md)
 - [LinksSigningBasket](./Models/LinksSigningBasket.md)
 - [LinksStartScaProcess](./Models/LinksStartScaProcess.md)
 - [LinksTransactionDetails](./Models/LinksTransactionDetails.md)
 - [LinksUpdatePsuAuthentication](./Models/LinksUpdatePsuAuthentication.md)
 - [LinksUpdatePsuIdentification](./Models/LinksUpdatePsuIdentification.md)
 - [MessageCode2XX](./Models/MessageCode2XX.md)
 - [MessageCode400AIS](./Models/MessageCode400AIS.md)
 - [MessageCode400PIIS](./Models/MessageCode400PIIS.md)
 - [MessageCode400PIS](./Models/MessageCode400PIS.md)
 - [MessageCode400SBS](./Models/MessageCode400SBS.md)
 - [MessageCode401AIS](./Models/MessageCode401AIS.md)
 - [MessageCode401PIIS](./Models/MessageCode401PIIS.md)
 - [MessageCode401PIS](./Models/MessageCode401PIS.md)
 - [MessageCode401SBS](./Models/MessageCode401SBS.md)
 - [MessageCode403AIS](./Models/MessageCode403AIS.md)
 - [MessageCode403PIIS](./Models/MessageCode403PIIS.md)
 - [MessageCode403PIS](./Models/MessageCode403PIS.md)
 - [MessageCode403SBS](./Models/MessageCode403SBS.md)
 - [MessageCode404AIS](./Models/MessageCode404AIS.md)
 - [MessageCode404PIIS](./Models/MessageCode404PIIS.md)
 - [MessageCode404PIS](./Models/MessageCode404PIS.md)
 - [MessageCode404SBS](./Models/MessageCode404SBS.md)
 - [MessageCode405AIS](./Models/MessageCode405AIS.md)
 - [MessageCode405PIIS](./Models/MessageCode405PIIS.md)
 - [MessageCode405PIS](./Models/MessageCode405PIS.md)
 - [MessageCode405PISCANC](./Models/MessageCode405PISCANC.md)
 - [MessageCode405SBS](./Models/MessageCode405SBS.md)
 - [MessageCode406AIS](./Models/MessageCode406AIS.md)
 - [MessageCode409AIS](./Models/MessageCode409AIS.md)
 - [MessageCode409PIIS](./Models/MessageCode409PIIS.md)
 - [MessageCode409PIS](./Models/MessageCode409PIS.md)
 - [MessageCode409SBS](./Models/MessageCode409SBS.md)
 - [MessageCode429AIS](./Models/MessageCode429AIS.md)
 - [PaymentInitationRequestResponse201](./Models/PaymentInitationRequestResponse201.md)
 - [PaymentInitiationBulkElementJson](./Models/PaymentInitiationBulkElementJson.md)
 - [PaymentInitiationCancelResponse202](./Models/PaymentInitiationCancelResponse202.md)
 - [PaymentInitiationJson](./Models/PaymentInitiationJson.md)
 - [PaymentInitiationStatusResponse200Json](./Models/PaymentInitiationStatusResponse200Json.md)
 - [PaymentInitiationWithStatusResponse](./Models/PaymentInitiationWithStatusResponse.md)
 - [PeriodicPaymentInitiationJson](./Models/PeriodicPaymentInitiationJson.md)
 - [PeriodicPaymentInitiationMultipartBody](./Models/PeriodicPaymentInitiationMultipartBody.md)
 - [PeriodicPaymentInitiationWithStatusResponse](./Models/PeriodicPaymentInitiationWithStatusResponse.md)
 - [PeriodicPaymentInitiationXmlPart2StandingorderTypeJson](./Models/PeriodicPaymentInitiationXmlPart2StandingorderTypeJson.md)
 - [PostalAddress6CH](./Models/PostalAddress6CH.md)
 - [PsuData](./Models/PsuData.md)
 - [PurposeCode](./Models/PurposeCode.md)
 - [ReadAccountBalanceResponse200](./Models/ReadAccountBalanceResponse200.md)
 - [ReadCardAccountBalanceResponse200](./Models/ReadCardAccountBalanceResponse200.md)
 - [RemittanceInformationStructured](./Models/RemittanceInformationStructured.md)
 - [ReportExchangeRate](./Models/ReportExchangeRate.md)
 - [ScaStatus](./Models/ScaStatus.md)
 - [ScaStatusResponse](./Models/ScaStatusResponse.md)
 - [SelectPsuAuthenticationMethod](./Models/SelectPsuAuthenticationMethod.md)
 - [SelectPsuAuthenticationMethodResponse](./Models/SelectPsuAuthenticationMethodResponse.md)
 - [SigningBasket](./Models/SigningBasket.md)
 - [SigningBasketResponse200](./Models/SigningBasketResponse200.md)
 - [SigningBasketResponse201](./Models/SigningBasketResponse201.md)
 - [SigningBasketStatusResponse200](./Models/SigningBasketStatusResponse200.md)
 - [StartScaprocessResponse](./Models/StartScaprocessResponse.md)
 - [TppMessage2XX](./Models/TppMessage2XX.md)
 - [TppMessage400AIS](./Models/TppMessage400AIS.md)
 - [TppMessage400PIIS](./Models/TppMessage400PIIS.md)
 - [TppMessage400PIS](./Models/TppMessage400PIS.md)
 - [TppMessage400SBS](./Models/TppMessage400SBS.md)
 - [TppMessage401AIS](./Models/TppMessage401AIS.md)
 - [TppMessage401PIIS](./Models/TppMessage401PIIS.md)
 - [TppMessage401PIS](./Models/TppMessage401PIS.md)
 - [TppMessage401SBS](./Models/TppMessage401SBS.md)
 - [TppMessage403AIS](./Models/TppMessage403AIS.md)
 - [TppMessage403PIIS](./Models/TppMessage403PIIS.md)
 - [TppMessage403PIS](./Models/TppMessage403PIS.md)
 - [TppMessage403SBS](./Models/TppMessage403SBS.md)
 - [TppMessage404AIS](./Models/TppMessage404AIS.md)
 - [TppMessage404PIIS](./Models/TppMessage404PIIS.md)
 - [TppMessage404PIS](./Models/TppMessage404PIS.md)
 - [TppMessage404SBS](./Models/TppMessage404SBS.md)
 - [TppMessage405AIS](./Models/TppMessage405AIS.md)
 - [TppMessage405PIIS](./Models/TppMessage405PIIS.md)
 - [TppMessage405PIS](./Models/TppMessage405PIS.md)
 - [TppMessage405PISCANC](./Models/TppMessage405PISCANC.md)
 - [TppMessage405SBS](./Models/TppMessage405SBS.md)
 - [TppMessage406AIS](./Models/TppMessage406AIS.md)
 - [TppMessage409AIS](./Models/TppMessage409AIS.md)
 - [TppMessage409PIIS](./Models/TppMessage409PIIS.md)
 - [TppMessage409PIS](./Models/TppMessage409PIS.md)
 - [TppMessage409SBS](./Models/TppMessage409SBS.md)
 - [TppMessage429AIS](./Models/TppMessage429AIS.md)
 - [TppMessageCategory](./Models/TppMessageCategory.md)
 - [TransactionAuthorisation](./Models/TransactionAuthorisation.md)
 - [TransactionDetails](./Models/TransactionDetails.md)
 - [TransactionStatus](./Models/TransactionStatus.md)
 - [TransactionStatusSBS](./Models/TransactionStatusSBS.md)
 - [TransactionsResponse200Json](./Models/TransactionsResponse200Json.md)
 - [UpdatePsuAuthentication](./Models/UpdatePsuAuthentication.md)
 - [UpdatePsuAuthenticationResponse](./Models/UpdatePsuAuthenticationResponse.md)
 - [UpdatePsuIdenticationResponse](./Models/UpdatePsuIdenticationResponse.md)


<a name="documentation-for-authorization"></a>
## Documentation for Authorization

<a name="BearerAuthOAuth"></a>
### BearerAuthOAuth

- **Type**: HTTP basic authentication

