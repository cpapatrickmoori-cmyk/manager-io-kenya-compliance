# manager-io-kenya-compliance
Kenya eTIMS integration extension for Manager.io – Real-time KRA compliance with QR codes and invoice transmission and general compliance with accounting requirements in Kenya
# Manager.io Kenya Compliance Extension

# Manager.io Kenya eTIMS Compliance Extension

Open-source extension for real-time KRA eTIMS compliance in Kenya.

## Overview
This extension adds mandatory Kenya Revenue Authority (KRA) eTIMS features directly into Manager.io:
- Automatic invoice transmission via OSCU
- QR code generation with digital signatures and control numbers
- Item registration, stock updates, credit/debit notes
- Full support for VAT rates and buyer PINs

Built as a hosted iframe extension using Manager.io's official API and Playground tools.

Addresses high-demand Kenyan user requests (e.g., [forum thread](https://forum.manager.io/t/kenya-invoices-requirement/62879)).

## Status
- Early development
- MVP: OSCU initialization + invoice transmission + QR display
- Open for contributions!

## Requirements
- Manager.io (latest version with Extensions enabled)
- KRA eTIMS sandbox/production access
- Hosted web server (free: Vercel/Netlify)

## Setup (Coming Soon)
1. Deploy the extension code
2. Add endpoint in Manager.io Settings > Extensions
3. Target: Sales Invoices page

## Development
- Uses Manager.io Playground for contextual API examples
- Backend: Node.js (Express) for secure OSCU calls
- Frontend: HTML/JS in iframe

Contributions welcome—especially from Kenyan users/testing!

## License
MIT © [cpapatrickmoori-cmyk](https://github.com/cpapatrickmoori-cmyk)
