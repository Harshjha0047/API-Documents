# 2Factor SMS API Integration

This document outlines the usage of the 2Factor V1 API endpoint for sending DLT-compliant Transactional and OTP SMS messages. This endpoint automatically maps the Principal Entity ID (PEID) and Content Template ID (CTID) based on the registered Template Name.

## Base URL
`https://2factor.in`

---

## Send SMS (OTP & Transactional)

Triggers an SMS to a specified mobile number using a pre-approved DLT template.

**Endpoint:** `GET /API/V1/{api_key}/SMS/{phone_number}/{otp_value}/{template_name}?var1={var_value}`

### Path Parameters

| Parameter | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| `api_key` | `string` | Your unique 2Factor API key. **Keep this secure in your `.env` file.** | Yes |
| `phone_number` | `string` | The 10-digit destination mobile number (without country code). | Yes |
| `otp_value` | `string` | The OTP to inject into the first `{#var#}`. Use `AUTOGEN` if the message is a standard transactional alert (e.g., Order Confirmed) and not an OTP. | Yes |
| `template_name` | `string` | The exact DLT-approved Template Name (e.g., `OTP_GoRevive` or `Order%20Received`). Must be URL-encoded if it contains spaces. | Yes |

### Query Parameters

| Parameter | Type | Description | Required |
| :--- | :--- | :--- | :--- |
| `var1` | `string` | The value to inject into the second `{#var#}` placeholder in your template (e.g., App Name or Order ID). | Optional* |

*\*Note: Query parameters are required only if your specific DLT template contains more than one `{#var#}` placeholder.*

---
