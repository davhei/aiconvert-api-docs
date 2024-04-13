# AIConvert API Documentation for Zapier Integration

This documentation provides detailed information on how to use the AIConvert API for integrating with Zapier. This guide will assist you in setting up and managing webhooks for seamless data transfer to your CRM or other systems through Zapier.

## Authentication

Our API uses API keys to authenticate requests. You can find your API key by navigating to the responses page of your form in AIConvert and clicking the "Zapier Integration" button.

## Base URL

All URLs referenced in the documentation have the following base:
`https://aiconvert.io/api`

## Endpoints

### Webhook Subscription

This endpoint allows you to subscribe or unsubscribe from webhook events, which send data to Zapier when a new conversation is recorded for your form.

- **URL**: `/forms/webhook_subscription`
- **Method**: `POST` | `DELETE`
- **Headers**:
  - **Key**: `X-API-KEY`
  - **Value**: `Your API key`
- **Data Params for POST**:
  ```json
  {
    "target_url": "https://hooks.zapier.com/hooks/catch/123456/"
  }
- **Success Response**:
  - **POST**:
    - **Code**: 200
    - **Content**: 
      ```json
      { "status": "subscribed" }
      ```
  - **DELETE**:
    - **Code**: 200
    - **Content**: 
      ```json
      { "status": "unsubscribed" }
      ```

- **Error Response**:
  - **Code**: 401 UNAUTHORIZED
    - **Content**: 
      ```json
      { "error": "API key required" }
      ```
  - **Code**: 401 UNAUTHORIZED
    - **Content**: 
      ```json
      { "error": "Invalid API key" }
      ```
  - **Code**: 404 NOT FOUND
    - **Content**: 
      ```json
      { "error": "Subscription not found" }
      ```

## Sample Webhook Payload

Subscribers receive a webhook payload structured as follows when a new form submission is made:

```json
{
  "name": "Mike",
  "email": "mike@vistalens.com",
  "phone": "(212) 555-6789",
  "summary": "Mike, the CEO of VistaLens Studios, is seeking a software solution to efficiently manage, edit, and deliver high-resolution images for their commercial photography projects. The current workflow challenges are impacting their turnaround times and business profitability. The ideal software would be a simple integrated solution with advanced image editing, efficient digital asset management, and seamless client gallery integration. The budget allocated for the project is $75,000 to $150,000, and the decision-makers are Mike and the studio manager.",
  "submitted_at": "2024-04-15 14:35:00"
}

## Errors

The API uses the following error codes:

| Code | Description                                      |
|------|--------------------------------------------------|
| 200  | Success                                          |
| 401  | Unauthorized (invalid or missing API key)        |
| 404  | Not Found (resource does not exist)              |
| 500  | Internal Server Error                            |

## Best Practices

- **Security**: Ensure that your API key is kept confidential.

## Updating Webhook URLs

If you need to change the URL targeted by the webhook, make a DELETE request followed by a POST request with the new URL as the target_url parameter.

## Support

For further assistance, please contact us at hello@aiconvert.io.
