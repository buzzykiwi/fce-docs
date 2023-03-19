## Getting Started
> FCE is third-party, open source software. As it is not provided or endorsed by Fluxx, the Zapier integration is a Private rather than Public integration. i.e. you will not find FCE in Zapier's standard list of integrations. To use it, follow [this link](https://zapier.com/developer/public-invite/171896/79f0f6177294d5882a4e1eb79aa80fef/) to add it to your Zapier account.


### Public vs Private Zapier Integrations

Zapier has two levels of integrations/apps. Public integrations are "first-class citizens": the integrations go through a rigorous assessment by Zapier staff and are then listed and available for all Zapier users. In order for an integration to go public, it has to be developed by the owner of the API (Fluxx) or an authorised contractor. Third-party developers cannot make their integrations Public in this way, but they may make their Private integration available via invite or [by link](https://zapier.com/developer/public-invite/171896/79f0f6177294d5882a4e1eb79aa80fef/).


### Use of This Software

FCE is provided free of charge. You may use it in three ways:

- The most up-to-date version of the software is available within Zapier once you have used [this link](https://zapier.com/developer/public-invite/171896/79f0f6177294d5882a4e1eb79aa80fef/).
- Developers may wish to download the source from Github, make modifications, and use it as a private integration. See the Zapier CLI documentation for how to set up a developer environment for a custom integration.
- You may use the software in any other way consistent with the MIT licence.

### Setup and Authentication

1. If you have not already done so, follow [the link](https://zapier.com/developer/public-invite/171896/79f0f6177294d5882a4e1eb79aa80fef/) to add FCE to your Zapier account. You only need to do this once.

  <p align="center"><img alt="Invite" src="../../img/14.png" width="500px"></p>

2. Set up an API application id and secret on your Fluxx Preprod and/or Production servers. The link is **https://[[server url]]/oauth/applications**
   1. Name the application e.g. "Zapier integration"
   2. Redirect URI: *copy and paste the following text:* https://zapier.com/dashboard/auth/oauth/return/App171896CLIAPI/
   3. Scopes: *leave blank*
   4. Click Submit
   5. The browser now shows the Application Name, Id, and Secret. Keep this window open as you will need the Id and Secret later.
3. In a new browser tab, create a new Zap in Zapier
4. In the search bar under *1. Trigger*, search for *Fluxx* 
5. Choose "Fluxx Community Edition (X.Y.Z)" under "Choose app & event"
6. Choose an Event that will occur in Fluxx and trigger this Zap to start processing. e.g. "Trigger on New Records", then "Continue"
7. The first time you do this, you need to click on "Sign In" next to "Connect Fluxx Community Edition *(nn.nn.nn)*" to connect to your Fluxx instance.
   1. A popup window appears, so ensure that popup windows are enabled for Zapier.com in your browser.
   2. In Fluxx Client Domain, enter the full domain name of the Fluxx Preprod or Production site, e.g. **mydomain.preprod.fluxxlabs.com**. Do not include the leading *https://*
   3. In Fluxx Application Id, copy and paste the Application Id you created in step 2
   4. In Fluxx Secret, copy and paste the "Secret" you created in step 2
   5. Click "Yes, Continue"
   6. The browser redirects to your chosen Fluxx instance, https://[[server url]]/oauth/authorize?client_id=...
   7. If the browser takes you to the Fluxx login page, complete the login then close the popup window and repeat from step 7i again.
8. Finish setting up the trigger. The "Trigger on New Records" trigger could use a trigger such as: `SELECT id, full_name FROM User ORDER BY updated_at desc LIMIT 100` to take the latest 100 records, and trigger on any new ones found.
9. Perform the Test Trigger step to ensure that Zapier is able to retrieve records from Fluxx. Zapier will pull in the latest three individual records and name them SQL Records Search Results [A-C].

If the authentication succeeds, congratulations! You are now ready to start automating Fluxx actions.
