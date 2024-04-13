# AIConvert API Documentation for Zapier Integration

This documentation provides detailed information on how to use the AIConvert API for integrating with Zapier. This guide will assist you in setting up and managing webhooks for seamless data transfer to your CRM or other systems through Zapier.

## Authentication

Our API uses API keys to authenticate requests. You can find your API key by navigating to the responses page of your form in AIConvert and clicking the "Zapier Integration" button.

## Base URL

All URLs referenced in the documentation have the following base:
`https://aiconvert.io/api`

## Endpoints

### Webhook Subscription

This endpoint allows you to subscribe or unsubscribe from webhook events, which send data to Zapier when a new form submission occurs.

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
