# Bitpay Invoice Generator

A tiny Node.js package that creates BitPay invoice pages through the BitPay API.

> **Status: dormant since 2014.** Written in December 2014 as part of Steven Zeiler's Bitcoin and Ripple payment plumbing. It was later used as a dependency by [bitpay-sync](https://github.com/stevenzeiler/bitpay-sync). It targets the BitPay API as it was in 2014 and has not been run against today's BitPay service as part of this documentation pass. See [docs/STATUS.md](docs/STATUS.md).

## Install

    npm install --save bitpay-invoice-generator

## Usage

    var InvoiceGenerator = require('bitpay-invoice-generator')
    var invoiceGenerator = new InvoiceGenerator({
      apiKey: 'bitpayApiKey',
      notificationURL: 'https://example.com/callbacks/bitpay'
    })

    invoiceGenerator.getNewInvoice({
      amount: 15,
      data: {
        arbitrary: 'embedded information'
      }
    })
    .then(function(invoice) {
      // invoice payment url and information returned
    })

## Config

- `apiKey` (required): your BitPay API key. The constructor throws `InvalidBitpayApiKey` without it.
- `notificationURL`: where BitPay should send payment notifications.
- `BITPAY_API_KEY`: environment variable read by the test in `test/invoice_generator.js`. Set it to your own key; never commit it.

## How it works

`getNewInvoice({ amount, data })` posts to `https://bitpay.com/api/invoice` with HTTP basic auth (the API key as the user name). The invoice price is `amount`, the currency is fixed to `BTC`, full notifications are on, and `data` is sent as JSON in the invoice `posData` field. The promise resolves with the response body, or rejects with an `Unauthorized` error on a 401.

## Status

Dormant but complete for what it set out to do. Details and open questions are in [docs/STATUS.md](docs/STATUS.md).

## License

ISC. See [LICENSE](LICENSE).
