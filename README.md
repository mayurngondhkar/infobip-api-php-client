# Infobip API PHP Client (WhatsApp Only)

[![Packagist](https://badgen.net/packagist/v/infobip/infobip-api-php-client)](https://packagist.org/packages/infobip/infobip-api-php-client)
[![MIT License](https://badgen.net/github/license/infobip/infobip-api-php-client)](https://opensource.org/licenses/MIT)

This repository is scoped to the Infobip WhatsApp API only.

## General Info

- PHP requirement: `>= 8.0`
- Package: `infobip/infobip-api-php-client`
- License: MIT

## Installation

```json
"require": {
  "infobip/infobip-api-php-client": "6.2.1"
}
```

Then run:

```bash
composer install
```

## Quickstart

### Configure the client

```php
use Infobip\Configuration;
use Infobip\Api\WhatsAppApi;

$configuration = new Configuration(
    host: 'your-base-url',
    apiKey: 'your-api-key'
);

$whatsAppApi = new WhatsAppApi(config: $configuration);
```

### Send a WhatsApp template message

```php
use Infobip\Model\WhatsAppBulkMessage;
use Infobip\Model\WhatsAppMessage;
use Infobip\Model\WhatsAppTemplateContent;
use Infobip\Model\WhatsAppTemplateDataContent;
use Infobip\Model\WhatsAppTemplateBodyContent;

$bulkMessage = new WhatsAppBulkMessage(
    messages: [
        new WhatsAppMessage(
            from: '447860099299',
            to: '<PUT YOUR NUMBER>',
            content: new WhatsAppTemplateContent(
                templateName: 'welcome_multiple_languages',
                templateData: new WhatsAppTemplateDataContent(
                    body: new WhatsAppTemplateBodyContent(
                        placeholders: ['<PUT YOUR NAME>']
                    )
                ),
                language: 'en'
            )
        )
    ]
);

$response = $whatsAppApi->sendWhatsAppTemplateMessage($bulkMessage);
```

## More WhatsApp examples

See [whatsapp.md](whatsapp.md).

## Support

For help, open an issue or contact [support@infobip.com](mailto:support@infobip.com).
