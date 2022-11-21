# FUND3R [![NEAR](https://img.shields.io/badge/NEAR-%E2%8B%88-111111.svg)](https://near.org/) [![License](https://img.shields.io/github/license/NEARFoundation/fund3r)](LICENSE) [![Telegram](https://img.shields.io/badge/chat-Telegram-blue.svg)](https://t.me/FUND3RNEAR)

FUND3R is a platform that provides tooling for end-to-end management of a grant lifecycle, significantly improving the barrier of entry to run your grant program.

👉 [Read more](https://gov.near.org/t/demo-run-a-scalable-compliant-grant-program-on-top-of-your-dao/26640)

## Demo

- Watch the demo video: https://drive.google.com/file/d/1U3bBcozcY1WxMQeIfZHANTBica4_ossl/view
- Try the demo website: https://fund3r-ui-demo.funding.nearweek.com/

## Development

The project is made of three services (each with its own README):

- [ui](/ui)
- [api](/api)
- [backoffice](/backoffice)

### Set up

Each of these services has its own environment variables.
You need to run `cp .env.dist .env` in each of these 3 folders and fill in the values.

#### API Keys required

The project requires a few API keys & settings to work properly, you need to set them the `.env` file.

- Astro DAO Smart contract id
- Calendly API Key
- Calendly URL for the approval interview
- Calendly URL for the milestones interview
- Hello sign API Key
- Hello sign client ID

### Customization

There are a few easy to customize items, here are some hints to help you achieve that:

#### Contract agreement

The [api/templates/agreement.docx](api/templates/agreement.docx) file is the template used to generate the contract agreement, it uses variables that are replaced by the API

#### Text

The [ui/src/locales](ui/public/locales) folder and the [api/locales/en.json](api/locales/en.json) file are used to customize the text of the UI and of the error messages

Note that some of the strings are currently duplicated

#### AstroDAO proposal

The proposal creation is handled by this file [ui/services/sputnikContractService.ts](ui/services/sputnikContractService.ts)

#### Currency

Change the currency in the following files

- [api/config/currency.js](api/config/currency.js)
- [api/config/grant.js](api/config/grant.js)
- [ui/config/currency.ts](ui/config/currency.ts)

#### Logos

- The invoice's logo is located in [api/assets/logo.png](api/assets/logo.png)
- The website's logo is located in [ui/public/images/logo.svg](ui/public/images/logo.svg)

#### Forms

Customizing the form is a bit tedious because of lack of shared code between frontend and backend, and should be improved in the future.

Here are the files involved, in the frontend:

- Form Rendering component: [ui/components/grant-application-form/FormEditFieldsProject.tsx](ui/components/grant-application-form/FormEditFieldsProject.tsx)
- Form Zod Schema: [ui/form-schemas/grantApplicationFormSchema.ts](ui/form-schemas/grantApplicationFormSchema.ts)
- GrantApplication interface: [ui/types/GrantApplicationInterface.ts](ui/types/GrantApplicationInterface.ts)

And in the backend:

- GrantApplication Mongodb Model: [api/modules/GrantApplication/GrantApplicationModel.js](api/modules/GrantApplication/GrantApplicationModel.js)
- Form Zod Schema [api/modules/GrantApplication/GrantApplicationFormSchema.js](api/modules/GrantApplication/GrantApplicationFormSchema.js)

You will have to also change the related strings (as mentioned above).

### Run

You can either run each of these services separately or run them all together using docker compose:

```bash
docker-compose -f ./docker-compose.yml up --build
```

## Authors

- [Sandoche](https://github.com/sandoche)
- [Pierre Le Guen](https://github.com/PierreLeGuen)

## License

[GNU General Public License v3.0](/LICENSE)
