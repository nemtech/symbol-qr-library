# nem2-qr-library

[![npm version](https://badge.fury.io/js/nem2-qr-library.svg)](https://badge.fury.io/js/nem2-qr-library)
[![Build Status](https://travis-ci.org/anthonylaw/nem2-qr-library.svg?branch=master)](https://travis-ci.org/anthonylaw/nem2-qr-library)
[![Slack](https://img.shields.io/badge/chat-on%20slack-green.svg)](https://nem2.slack.com/messages/CB0UU89GS//)

:warning: **This package is currently still in development, please do not use in production.** *The author of this package cannot be held responsible for any loss of money or any malintentioned usage forms of this package. Please use this package with caution.*

NEM2 QR Library generator to genereate QRcode by string (JSON format) for the Catapult (NEM2) platform.

This is a PoC to validate the proposed [NIP? QR Library - Definition](https://github.com/nemtech/NIP/issues/3). When stable, the repository will be moved to the [nemtech](https://github.com/nemtech) organization.

## Installation

`npm install nem2-qr-library`

## Usage

### Generate QRCode for a Transaction Request

```typescript
import { QRCodeGenerator } from 'nem2-qr-library';

// (Optional) create transfer transaction (or read from network)
const transfer = TransferTransaction.create(
  Deadline.create(), 
  Address.createFromPublicKey(
    'C5C55181284607954E56CD46DE85F4F3EF4CC713CC2B95000FA741998558D268',
    NetworkType.MIJIN_TEST
  ), 
  [new Mosaic(new NamespaceId('cat.currency'), UInt64.fromUint(10000000))],
  new PlainMessage('Welcome to NEM!'),
  NetworkType.MIJIN_TEST
);

// create QR Code base64
const base64 = QRCodeGenerator.fromTransaction(transfer).toBase64();
console.log(base64);
```

The produced Base64 encoded payload can be used to display the QR Code. An example of display can be done easily with HTML, as follows:

```html
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAAUAAAAFCAYAAACNbyblAAAAHElEQVQI12P4//8/w38GIAXDIBKE0DHxgljNBAAO9TXL0Y4OHwAAAABJRU5ErkJggg==" alt="Transfer Transaction QR code" />
```

## Changelog

Important versions listed below. Refer to the [Changelog](CHANGELOG.md) for a full history of the project.

- [0.2.0](CHANGELOG.md) - 2019-05-01
- [0.1.0](CHANGELOG.md) - 2019-04-20

## License

Licensed under the [Apache License](LICENSE.md), Version 2.
