# PumpX Bundler.

## Getting Started

PumpX Bundler allows you to hide the bundled trades on pump.fun only and showing only the dev buy.

There will be no connection between the dev wallet and the other wallets.
three wallets will be needed for the setup. The dev wallet that will create the token and show the first buy,
The Ghost bundler wallet that will fund most operations and the other configured wallets to buy.
And finally the jito auth keypair, recently jito has removed whitelisting so normally you can use any keypair you want. 
in the bundling process, the dev wallet will not be connected onchain to any of the others wallets that buy (not on sell)
provided that the ghost bundler wallet was funded from a seperate source.

Join pumpX [discord](https://discord.gg/j3szDJ6CH9) for more info.


### Prerequisites

- Node.js and npm installed on your machine (latest versions).
- solana wallet(s)/Base58 private key.
- RPC Endpoint url (with high rate limit).
- JITO access.


### Installation

1. Download or clone the repository to your local machine.
2. Navigate to the project directory.
3. Install dependencies:
```npm install```

### Configuration and Setup
1. Rename `config.example.json` to `config.json` in the root directory.
- Populate the `config.json` file with the required information
- Do not change, add or remove fields but only change their values.
2. Rename `bundle-wallets.example.json` to `bundle-wallets.json` in the root directory.
- Populate the `bundle-wallets.json` with desired number of wallet entries (up to 21)
- Wallet entry:
```json
        {
            "privateKey": "ENTER WALLET BASE58 PRIVATE KEY HERE",
            "sol": 0.01
        },
```
- Do not add a trailing comma at the last entry.
3. Rename `metadata.example.json` to `metadata.json` in the `assets` directory.
- Populate the `metadata.json` file with the required and optional values.
- Do not change, add or remove fields but only change their values.

4. Add an image file in the `assets` directory and name it `image.png|jpeg|jpg|gif (choose only one of the supported extension).`

6. ####  Pointers

- In case of issues arising after editing the json files, you can always download a new .example file and follow the same respective steps above according to the type.
- you can resume of tracking your position on the bundle if selling or transfering fails/timeouts/gets stuck by choosing the resume tracking option.
- always check the balances of you configured wallets before generating new wallets to avoid loss of funds.
- in case of latency or issues with uploading metadata, use the provided link in the second metadata creation option then upload your image using storage tools, add an image field to the metadata template file and then upload the adjusted metadata file.  metadata template (add image field and set its value as the uri of your uploaded image):
 ``` json
    {
        "name":"",
        "symbol":"",
        "description":"",
        "twitter":"",
        "telegram":"",
        "website":""
    }
```
- In case of errors regarding program failing to complete, try re-distributing the buy amounts or using more wallets and spread more.
- you can always close the address lookup table you created to reclaim its rent after you are finished with the bundle.
- you can always resume


### Usage

1. Run the script:
```npm run start```