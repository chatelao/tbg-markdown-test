# ChallengeData
## Properties

Name | Type | Description | Notes
------------ | ------------- | ------------- | -------------
**image** | [**byte[]**](ByteArray.md) | PNG data (max. 512 kilobyte) to be displayed to the PSU, Base64 encoding, cp. [RFC4648]. This attribute is used only, when PHOTO_OTP or CHIP_OTP is the selected SCA method.  | [optional] [default to null]
**data** | [**List**](string.md) | A collection of strings as challenge data | [optional] [default to null]
**imageLink** | [**String**](string.md) | A link where the ASPSP will provides the challenge image for the TPP. | [optional] [default to null]
**otpMaxLength** | [**Integer**](integer.md) | The maximal length for the OTP to be typed in by the PSU. | [optional] [default to null]
**otpFormat** | [**String**](string.md) | The format type of the OTP to be typed in. The admitted values are \&quot;characters\&quot; or \&quot;integer\&quot;. | [optional] [default to null]
**additionalInformation** | [**String**](string.md) | Additional explanation for the PSU to explain e.g. fallback mechanism for the chosen SCA method. The TPP is obliged to show this to the PSU.  | [optional] [default to null]

[[Back to Model list]](../README.md#documentation-for-models) [[Back to API list]](../README.md#documentation-for-api-endpoints) [[Back to README]](../README.md)

