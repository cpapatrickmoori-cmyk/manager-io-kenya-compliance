# manager-io-kenya-compliance
Kenya eTIMS integration extension for Manager.io – Real-time KRA compliance with QR codes and invoice transmission and general compliance with accounting requirements in Kenya

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

HOW TO INSTALL

1) Set up invoice footer with this code;
   
<div style="margin-top: 50px; padding: 20px; border-top: 4px solid #922529; background-color: #f9f9f9; text-align: center; font-family: Arial, Helvetica, sans-serif; color: #000000;">
  <h2 style="color: #922529; font-size: 20px; margin-bottom: 15px; font-weight: bold;">
    Kenya Revenue Authority (KRA) eTIMS Verification
  </h2>
  
  {% assign qr_field = custom_fields | where: "label", "eTIMS QR Code" | first %}
  {% assign control_field = custom_fields | where: "label", "eTIMS Control Number" | first %}

  {% if qr_field and qr_field.text != blank %}
    <div style="margin: 25px 0;">
      <img src="{{ qr_field.text }}" alt="KRA eTIMS QR Code" 
           style="max-width: 240px; height: auto; border: 3px solid #008C51; background: white; padding: 10px;" />
    </div>
    
    <p style="margin: 15px 0; font-size: 15px; color: #000000;">
      <strong>Invoice Control Number:</strong> {{ control_field.text | default: "Pending" }}
    </p>
    <p style="margin: 10px 0; font-size: 15px; color: #008C51; font-weight: bold;">
      Verified: Scan QR code or visit verify.kra.go.ke
    </p>
  {% else %}
    <p style="color: #922529; font-size: 17px; font-weight: bold; margin: 25px 0;">
      eTIMS QR Code not generated yet
    </p>
    <p style="font-size: 14px; color: #000000;">
      Click "Transmit to KRA eTIMS" in the extension panel to generate
    </p>
  {% endif %}
  
  <hr style="margin: 30px 0; border-color: #008C51;" />
  <p style="font-size: 12px; color: #000000;">
    This invoice is electronically transmitted via the Electronic Tax Invoice Management System (eTIMS)
  </p>
</div>

2) Deploy to Netlify
In Netlify dashboard: Click "Add new site" > "Import an existing project".
Connect to GitHub > Select your repo manager-io-kenya-compliance.
Site settings:
Branch: main
Build command: Leave blank (no build needed for static).
Publish directory: extension (this tells Netlify to serve files from the extension/ folder).

Click Deploy site.

Get Your Live URL
Netlify gives a URL like https://your-site-name.netlify.app (you can customize later).
Test it: Open the URL – you should see the page with a QR code.


Option 2: Host on Vercel (Great if You Later Add Node.js Backend for OSCU Calls)
If you want server-side logic (e.g., secure KRA API calls without exposing keys):

Sign up at https://vercel.com (free with GitHub).
In your repo, create folder extension/ with the same index.html as above.
Dashboard: Add New Project > Import your GitHub repo.
Settings:
Framework Preset: "Other" (static).
Root Directory: ./extension
No build command needed.

Deploy – URL like https://your-project.vercel.app.

Step After Hosting: Test in Manager.io

Open Manager.io (latest version).
Go to Settings > Extensions.
Enable Playground (button at bottom) – this shows API examples.
Click New Extension:
Name: "Kenya eTIMS Compliance"
Endpoint: Your Netlify/Vercel URL (e.g., https://your-site.netlify.app)
Placement: /sales-invoices or /sales-invoices/edit (to show on invoice pages).

Save > Go to a Sales Invoice – your extension appears in an iframe at the bottom!

You'll see "Connected!" and a test QR when context loads.
