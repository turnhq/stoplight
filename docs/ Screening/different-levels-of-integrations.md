# Different Levels of Integrations

## Standalone (No Integration)
You can use the Turn Dashboard to initiate background checks without needing to integrate with an ATS (3rd party or your own in-house). There are two main ways to start a new background check:

### Unique Package URL
You can send a candidate a unique URL that’s linked to a specific package; you’ll have a unique URL for each package you configure. You can see a list of all your configured packages and the unique URLs in your Turn Dashboard under Settings > Packages.

![alt text](https://documentation.turning.io/static/status/package-url.png)

Once the candidate opens the URL, the consent form is displayed, and they’ll provide all the required information. You can also prefill every part of the form, see [prefilling the candidate consent form section](#Pre-filling-the-Unique-URL---Consent-Form).

### Personal Invitation
You can also kick off a background check by sending personalized invitation to a candidate with the “Add Candidate” feature in your Turn Dashboard.

![alt text](https://documentation.turning.io/static/status/personal-invitation.png)

You need to specify the candidate’s name, email and the desired package (you can also specify a mobile phone number).

![alt text](https://documentation.turning.io/static/status/personal-invitation-2.png)

We’ll send a personalized email invitation to start the background check with a direct link to the consent form. If a phone number is provided, we’ll also send a sms/text invitation.

The candidate will appear in your Turn Dashboard as emailed:

![alt text](https://documentation.turning.io/static/status/personal-invitation-3.png)

We’ll let you know if, and how many times, the candidate opened the invitation, clicked on the consent form as well as allow you to manually resend the invitation.

![alt text](https://documentation.turning.io/static/status/personal-invitation-4.png)

Turn has a communication protocol in place for candidates that have yet to fill out the consent form.

| Invite delivery | First communication | First reminder | Second reminder |
| --- | --- | --- | --- |
| Email | 0 hours | 12 hours | 48 hours |
| SMS | 1 hours | 24 hours | 72 hours |

### Pre-filling the Unique URL - Consent Form
Most Turn partners have some or all of a candidate’s details on hand at the time they are ready to invite the candidate to complete a background check. Rather than forcing a candidate to re-enter all their information and possibly using different values (for example, a different email address), it is possible for you to customize your candidate consent link to pre-populate the form. This reduces the data entry on the candidate’s part and enforces data integrity for you.

To pre-populate the candidate consent form, you can append URL parameters to your candidate URL. For example, your candidate URL may be:

[https://partners.turning.io/apply/ACME/P123456789](https://partners.turning.io/apply/ACME/P123456789)

To add the additional parameters, append a ’?’ character, then the name of the attribute ’=’ and the value you wish to be populated in the field. Any additional parameters are separated by a ’&’ character. For example, to pre-populate the most common fields on the form you would format your URL as follows:

[https://partners.turning.io/apply/ACME/P123456789?first\_name=David&last\_name=Lee&email=david.lee@acme.edu&phone_number=3125551212](https://partners.turning.io/apply/ACME/P123456789?first_name=David&last_name=Lee&email=david.lee@acme.edu&phone_number=3125551212)

A list of all the possible parameters is listed here.

| Parameter Name | Description |
| --- | --- |
| first_name | First name of the candidate |
| middle_name | Middle name of the candidate |
| no\_middle\_name | To enable the ‘No Middle Name’ checkbox pass true along with this parameter. The default is false. If set to true it will ignore any value passed in with the middle_name parameter |
| last_name | Last name of the candidate |
| email | Email address of the candidate. Must be formatted as a valid email and must be deliverable. |
| date\_of\_birth | Date of birth of the candidate (Must be passed as DD/MM/YYYY) |
| gender | Must be either ‘Male’ or ‘Female’ |
| ssn | If available it can be passed along. Must be 9 digits |
| phone_number | Phone number as a 10 or 11 digit number |
| zipcode | Five digit zip code of the candidate |
| drivers\_license\_number | Driver’s license (if using MVR). Must follow state specific formatting guidelines |
| drivers\_license\_state | Two character state code |

Note: All fields will be prefilled when the consent form is loaded, but the candidate will still be able to edit everything that was prefilled. The only exception is **email**.

If the **email** parameter is set via the prefill parameter, it will be frozen, meaning that the candidate won’t have a chance to edit it.

### Extra functionality Unique URL - Consent Form
In addition to all the parameters than can be pre-populated in the consent form, there are two extra parameters than can be added, they are invisible to your candidate and can be very helpful in certain situations:

| Parameter Name | Description |
| --- | --- |
| redirect_url | Redirect to a given URL after the candidate finishes filling the consent form |
| reference_id | An arbitrary reference you’d like to assign to this candidate |

**redirect_url**

If you want your candidate to be redirected as soon as they complete the consent form, to any custom landing page or URL, specify this parameter. It’s content should be a valid URL reference such as:

www.acme.com/hiring

A valid Unique URL would read like:

[https://partners.turning.io/apply/ACME/P123456789?first\_name=David&last\_name=Lee&redirect_url=www.acme.com/hiring](https://partners.turning.io/apply/ACME/P123456789?first_name=David&last_name=Lee&redirect_url=www.acme.com/hiring)

If you need to add a custom URL that has a set parameters of its own like this:

[www.acme.com/hiring?my_applicant=123](http://www.acme.com/hiring?my_applicant=123)

You’ll need to first encode a URL version of it beforehand:

[www.acme.com%2Fhiring%3Fmy_applicant%3D123](http://www.acme.com%2Fhiring%3Fmy_applicant%3D123/)

The valid Unique URL would read like:

[https://partners.turning.io/apply/ACME/P123456789?first\_name=David&last\_name=Lee&redirect\_url=www.acme.com%2Fhiring%3Fmy\_applicant%3D123](https://partners.turning.io/apply/ACME/P123456789?first_name=David&last_name=Lee&redirect_url=www.acme.com%2Fhiring%3Fmy_applicant%3D123)

**reference_id**

If you want to link a specific candidate with some arbitrary internal reference of yours, you can use this parameter, it’ll be visible in your Turn Dashboard in your candidate report like this:

![alt text](https://documentation.turning.io/static/status/reference-id.png)

And it will also be sent in all API events sent back to you.

The valid Unique URL would read like:

[https://partners.turning.io/apply/ACME/P123456789?first\_name=David&last\_name=Lee&reference_id=abc-123-def](https://partners.turning.io/apply/ACME/P123456789?first_name=David&last_name=Lee&reference_id=abc-123-def)

## Fountain Integration
Turn offers a seamless integration with Fountain. You can integrate Turn and Fountain in just a few minutes, with no technical support. Let’s get started.

### Configure Fountain Secondary API Token in your Turn Dashboard
**We have a 7 step process to incorporate Turn into your Fountain Dashboard.** To do this, you need to have your fountain dashboard and your Turn dashboard open and signed into.

**Step 1 is to Generate the API token in Fountain and get that into your Turn Dashboard.**

Starting in your fountain dashboard. In the upper right corner, hovering over your name and it will give you the option for Company Settings. Please click on that.

![alt text](https://documentation.turning.io/static/fountain/company-settings.png)

On the left side of the screen you will see the developer settings tab. Under that you will see API. Please click on that.

![alt text](https://documentation.turning.io/static/fountain/developer-settings.png)

Click on the show API Keys button.

![alt text](https://documentation.turning.io/static/fountain/show-api-keys.png)

Click on the create secondary tokens. Please copy that private API key under Secondary Token.

Lets now go over into your Turn dashboard. Click on the settings menu in the top right.

![alt text](https://documentation.turning.io/static/partner-dashboard/settings-button.png)

Scroll down in your setting tab until you see the Fountain Integration header. Input the private API key into the API key field.

Go back to Fountain and copy the public API key from the secondary tokens.

And let’s go back into Turn settings and input the Public API Key into the Public API Key in the Turn Dashboard. Click save.

![alt text](https://documentation.turning.io/static/partner-dashboard/fountain-integration-section.png)

**Great, we are done with Step 1.**

**Next let’s go back into the Fountain Dashboard and we will set up Turn’s two custom Attributes.**

Staying in the Company Settings tab in Fountain. Under the app Settings tab on the left you will see Custom Attributes. Please click that.

![alt text](https://documentation.turning.io/static/fountain/app-settings-option.png)

In the top right corner you will see a blue button that says Add Custom Attribute. Please click on that.

![alt text](https://documentation.turning.io/static/fountain/add-custom-attribute-button.png)

We are going to add two custom attributes in the next form starting with Attribute Name: turn_status. Please make sure that is all lowercase. Attribute Title: Turn Status. Please click Save Attribute.

![alt text](https://documentation.turning.io/static/fountain/add-custom-attribute-form-turn-status.png)

**The Turn status will show the status of Turn’s background checks in Fountain.**

**![alt text](https://documentation.turning.io/static/fountain/custom-attributes-table.png)**

We are going to click on Add Custom Attribute again.

![alt text](https://documentation.turning.io/static/fountain/add-custom-attribute-button.png)

This time the Attribute Name is: turn_url. All lowercase. Attribute Title: Turn URL. Please click “Save Attribute”.

![alt text](https://documentation.turning.io/static/fountain/add-custom-attribute-form-turn-url.png)

**The Turn URL provides you with the links to take you to the complete background check in the Turn Dashboard.**

**Step 2 is now done.**

**To test Turn, you can set up a new workflow or add Turn’s Background Check into an already existing workflow. If you want to create a new workflow, please go to Step 3. If you want to add Turn into an already built workflow, please skip Step 3 and go to Step 4.**

**Step 3 we are going to create a new opening / workflow so you can test Turn in Fountain.**

Please click on the blue fountain logo in the top left corner which will take you back to the fountain home page.

![alt text](https://documentation.turning.io/static/fountain/fountain-header.png)

In the top right corner, please click on Add Opening.

![alt text](https://documentation.turning.io/static/fountain/add-opening.png)

You will see a Position & Location form.![alt text](https://documentation.turning.io/static/fountain/position-and-location-form.png)

For location you can decide where you want to test. You can click on the Add Location button and label it as you see fit.

![alt text](https://documentation.turning.io/static/fountain/position-and-location-form-add-location.png)

For position, you need to have a position not currently associated with that selected location. So you can click on the Add Position button and label it something like New Courier.

![alt text](https://documentation.turning.io/static/fountain/position-and-location-form-add-position.png)

Feel free to adjust the name opening or keep it as is.

For opening details you need to add an Owner, but other than that you can either fill it out now or skip it.

For the application form we can skip this for now. Select continue.

![alt text](https://documentation.turning.io/static/fountain/opening-details-form.png)

Now you have the opportunity to either clone a workflow you already have or create a new workflow. If you have a workflow you want to use, you can pick that one from the drop down and click Save.

![alt text](https://documentation.turning.io/static/fountain/hiring-workflow-options.png)

**Great. Now we are done with Step 3.**

**Onto step 4 where we are going to create and configure the stages and rules for this workflow.**

Please click on the actions button next to the workflow we want to test. Click on Edit Workflow.

![alt text](https://documentation.turning.io/static/fountain/edit-workflow.png)

We are going to start by deleting any stages and rules that are not relevant here. Please click on the background stage and then hit the red x button to delete. If there are rules in the workflow, you will need to delete that first. Except the predefined rules Approved, Rejected and On Hold, they can’t be deleted.

![alt text](https://documentation.turning.io/static/fountain/default-stages.png)

We are going to add two new stages. So first click on the button in the top left that says add stage. Click on Create New Stage.

![alt text](https://documentation.turning.io/static/fountain/create-new-stage-button.png)

You can title it - Turn Background Check. Stage type is Custom. You can pick where you want to insert it in the flow.

![alt text](https://documentation.turning.io/static/fountain/create-new-stage-turn-bgc.png)

We are going to add another stage now. Please click on Create New Stage again.

![alt text](https://documentation.turning.io/static/fountain/create-new-stage-button.png)

We can title this Turn Background Check Processing. Stage type is Custom here as well.

![alt text](https://documentation.turning.io/static/fountain/create-new-stage-turn-bgc-processing.png)

This is where workers will go once they submit their background check.

Please put this after the Turn Background check in the workflow.

![alt text](https://documentation.turning.io/static/fountain/stages-highlighted.png)

We are now done with the stages and moving on to creating the two rules. Please click on the Add Rule button in the top left.

![alt text](https://documentation.turning.io/static/fountain/add-rule-button.png)

Lets title that Turn Rules. Set that below the Turn Background Check Processing stage and click Add Rule stage.

![alt text](https://documentation.turning.io/static/fountain/create-new-rule-stage-turn-rules.png)

From here we are going to add two rules. Please click on the green Add Rule button.

![alt text](https://documentation.turning.io/static/fountain/add-rule-alt.png)

Applicant field is turn_status from the custom tab. Set value as Equals. Below Equals input clear. Move applicant to stage Approved. Click Save Changes.

![alt text](https://documentation.turning.io/static/fountain/rules-turn-status.png)

Click on the green Add Rule button again.

![alt text](https://documentation.turning.io/static/fountain/add-rule-alt2.png)

In the And Then section we are going to add another rule. Select turn_status from the custom tab again. Set value as equals. Then consider.

Next move the applicant to rejected (or whatever stage to review candidates). Provide a reason in the because field.

![alt text](https://documentation.turning.io/static/fountain/rules-turn-status2.png)

Click Save Changes.

![alt text](https://documentation.turning.io/static/fountain/rules-save-changes-button.png)

Below is an example of the order:

![alt text](https://documentation.turning.io/static/fountain/turn-rules-stage.png)

**We are now done with Step 4.**

**Moving on to step 5 which is Implementing the custom attributes we created into the Fountain Table.**

Click on the Applicant tab in the top left corner.

![alt text](https://documentation.turning.io/static/fountain/applicants-tab.png)

Click on the bottom plus menu item in the table.

![alt text](https://documentation.turning.io/static/fountain/plus-icon-on-table.png)

Search Turn and select turn\_status and turn\_url attributes.

![alt text](https://documentation.turning.io/static/fountain/turn-status-and-url.png)

Those will now display in your table.

![alt text](https://documentation.turning.io/static/fountain/turn-table-headers.png)

**That is it for Step 5.**

**For Step 6. We are going to set up the Fountain webhook. If you have not already, please reach out to your Turn representative to get your Fountain Webhook.**

We are going to go back into the Company Settings tab.

Under Developer Settings on the left you will see Webhooks. Please click that.

![alt text](https://documentation.turning.io/static/fountain/company-settings.png)

![alt text](https://documentation.turning.io/static/fountain/developer-settings.png)

Click on the blue button that says Add Webhook.

![alt text](https://documentation.turning.io/static/fountain/add-webhook-button.png)

Give it the webhook name: Turn Webhook. Input your Fountain Webhook. Trigger should be Stage Transition. And then for stage the All Stages option. Click save.

![alt text](https://documentation.turning.io/static/fountain/add-turn-webhook-form.png)

**That is it for step 6.**

**The final step is setting up your email notifications. If you have not already, please reach out to your Turn representative to get your candidate URL.**

Click on the blue fountain logo in the top left.

![alt text](https://documentation.turning.io/static/fountain/fountain-header.png)

Click on the action button in the workflow we just created. Click on the Edit Workflow.

![alt text](https://documentation.turning.io/static/fountain/edit-workflow.png)

Click on the Turn Background check stage.

![alt text](https://documentation.turning.io/static/fountain/turn-bgc-stage.png)

Click on Add Message under Automated Message.

![alt text](https://documentation.turning.io/static/fountain/add-message-button.png)

Message Name is: Background Check Email. Message type is Automated. Send from the Opening Owner is fine.

![alt text](https://documentation.turning.io/static/fountain/add-automated-message.png)

Click on the “What do you want to say” add email button.

![alt text](https://documentation.turning.io/static/fountain/add-email-field.png)

Email subject is: {your company name} - Background Needed to Continue. For the email body, please include the candidate URL.

![alt text](https://documentation.turning.io/static/fountain/email-message-form.png)

You are now all set up with Turn in Fountain!

### Fountain - Adverse Action Flow
We have the ability to run Adverse Action simultaneously in your Fountain flow.

You can select the number of stages you want for Adverse Action / Rejected Stage in Fountain.

| Number of Stages | Meaning |
| --- | --- |
| 1   | You can only pass in our Partner Dashboard through First Notice. |
| 2   | You can pass in our Partner Dashboard through First Notice and Second Notice. At the end your candidates will stay as 2nd Notice. |
| 3   | You can pass in our Partner Dashboard through First Notice, Second Notice and Rejected. |

* * *

Below is the walkthrough if you select the 3 stage option.

When you access the Partner Dashboard and want to apply Pre-Adverse Action to one candidate:

![alt text](https://documentation.turning.io/static/partner-dashboard/pre-aa-button.png)

Respectively provide your decision.

![alt text](https://documentation.turning.io/static/partner-dashboard/reason-aa.png)

You will see the candidate passed to Adverse Action / Rejected Stage inside the Fountain process page as well as the Turn Status will pass to First notice. Do not worry about a Status empty column.

![alt text](https://documentation.turning.io/static/fountain/aa-first-notice.png)

Then if you want to pass the candidate to Second Notice, click again on:

![alt text](https://documentation.turning.io/static/partner-dashboard/pre-aa-button.png)

Provide the reason as shown previously.

You will see the candidate stay at Adverse Action / Rejected Stage inside the Fountain process but Turn Status will pass to Second notice. Do not worry about a Status empty column.

![alt text](https://documentation.turning.io/static/fountain/aa-second-notice.png)

In case you have 2 steps configured, the candidate will stop here.

You have one step left. Click again in Pre-Adverse Action:

![alt text](https://documentation.turning.io/static/partner-dashboard/pre-aa-button.png)

Introduce the message and return to the Fountain process page and you’ll see the candidate has passed to Rejected.

![alt text](https://documentation.turning.io/static/fountain/rejected.png)

Any questions please reach out to your Turn representative.

### Fountain - Store Data Configuration
You have the option to allow a candidate to fill out the consent form, but instead of starting the background check right away, it “stores the candidate data” in order to start checks in the future (or never).

In order to turn on this feature, you have to configure this in your Fountain Dashboard following the next 3 steps:

**Custom stage**

Add a new custom stage just after the already existing Processing Stage. (If no processing stage is present, it’s mandatory to enable the processing stage). The stage needs to be EXACTLY NAMED:

**Initiated BGC**

No more, no less, match spaces and upper/lower case.

![alt text](https://documentation.turning.io/static/fountain/initiated-bgc-stage.png)

**Email with do_checks parameter**

Edit email/SMS with instructions on how to start the BGC, to append the do_checks parameter:

_&do_checks=false_

_![alt text](https://documentation.turning.io/static/fountain/message-with-do_checks-parameter.png)_

**Add a new Webhook with /run parameter**

The URL will be the same as the existing Turn Webhook but will end in /run

Existing “Turn Webhook”:

[https://api.turning.io/v1/fountain/partner/45941fa4-829f-4901-a7df-273f7db7e78c](https://api.turning.io/v1/fountain/partner/45941fa4-829f-4901-a7df-273f7db7e78c)

New “Turn Webhook Run”

[https://api.turning.io/v1/fountain/partner/45941fa4-829f-4901-a7df-273f7db7e78c/run](https://api.turning.io/v1/fountain/partner/45941fa4-829f-4901-a7df-273f7db7e78c/run)

So please add the previous URL to Payload URL text field:

![alt text](https://documentation.turning.io/static/fountain/add-webhook-form.png)

It’s Done! How does the new flow work?

When a candidate completes the BGC it will be moved to the Fountain Processing Stage. On Turn’s side, the checks won’t be started.

When you want to initiate the checks. You need to move the candidate from Processing to Initiated BGC. That action will trigger the new webhook, and we’ll start processing all checks.

Everything afterwards follows the same flow with your background check.

## Greenhouse Integration
We have a working integration with Greenhouse. If you have your hiring process with that platform, you can choose Turn as your vendor to process your background checks.

Please reach out to your Turn representative to make it possible.

![alt text](https://documentation.turning.io/static/greenhouse/turn-greenhouse.png)

## API Integration
Turn’s flexible API lets you integrate in a customizable way depending on your needs and desired level of integration. In this section, we will cover all the ways you can start an integration with Turn’s API, the webhooks you can expect, and other useful API calls.

There are three levels of integration:

### a) Automating the background check request - Turn’s Protocol
The first level of integration automates the initial request of a background check for a specific candidate. Turn will be responsible for delivering the invitation to the candidate, utilizing our communication protocol to guide the candidate through the check, and a webhook to deliver the completed results.

This level of integration is recommended when:

* You reach the point in your onboarding flow when you have the candidate name/email and you wish to start the background check, but do not want to manually input the candidate’s information in your Turn Dashboard.
* You want to know programmatically when a check is completed and its status.

Take a look on how to implement it:[API /person/search_async](https://turnhq.stoplight.io/docs/turn-api/TurnAPIStoplight.yml/paths/~1person~1search_async/post)(email_candidate flag on)

### b) Automating the background check request - Your Protocol

The second level of integration still automates the initial request of a background check, but instead of having Turn control the communication with the candidate, you control the communication. You’ll still have a unique URL for each candidate’s consent form, and you will decide when and how to display it to your candidates. When the background check is completed, a webhook with the check results will be posted back at you.

This level of integration is recommended when:

* You want to take control over when exactly the candidate receives the invitation.
* You want to include the link of the consent form in other types of communication.
* You want to embed the consent form as part of your already existing web or mobile application.

Take a look on how to implement it:[API /person/search_async](https://turnhq.stoplight.io/docs/turn-api/TurnAPIStoplight.yml/paths/~1person~1search_async/post)(email_candidate flag off)

### c) End to End Integration
The third level of integration is when you want control over the UI and UX of your background check request process for candidates. We’ll let you know the inputs you need to gather from candidates, and the legal text to display. When the background check is completed, a webhook with the results will be posted back at you.

This level of integration is recommended when:

* You want complete control over the background check experience for the candidates.

Take a look on how to implement it:[API /fcra_check/form](https://turnhq.stoplight.io/docs/turn-api/TurnAPIStoplight.yml/paths/~1fcra_check~1form/post)

### Test Identities
While testing with the API, a set of identities can be used to simulate reports with multiple background hits, specifying the following names (no matter what other information is required) a complete simulated report will be posted back to the specified webhook URL.

| First Name | Last Name |
| --- | --- |
| Darth | Vader |
| Samwise | Gamgee |
| Walter | White |

### Automating the background check request - Turn’s Protocol
This integration involves the use of the [API /person/search_async](https://turnhq.stoplight.io/docs/turn-api/TurnAPIStoplight.yml/paths/~1person~1search_async/post) endpoint. You provide basic candidate details (name, email,) specify your required package, and make sure to pass the email\_candidate flag with a true value. Once the check is complete the results will be posted back via a webhook to the specified location provided in the callback\_url parameter. See [Webhooks - Background Check Results](https://turnhq.stoplight.io/docs/turn-api/TurnAPIStoplight.yml/paths/~1fcra_check~1form/post) for details on the response.

### Automating the background check request - Your Protocol
This integration also involves the[API /person/search_async](https://turnhq.stoplight.io/docs/turn-api/TurnAPIStoplight.yml/paths/~1person~1search_async/post)endpoint. You provide basic candidate details (name, email) specify your required package, and make sure to pass the email_candidate flag with a false value.

In the response, look for the candidate\_consent\_url value, this will be the URL you need to present to the candidate to start their background check.

Once the check is complete, the results will be posted back via a webhook to the specified location provided in the callback_url parameter. See[Webhooks - Background Check Results](https://turnhq.stoplight.io/docs/turn-api/TurnAPIStoplight.yml/paths/~1fcra_check~1form/post)for details on the response.

### End to End Integration
This integration involves the use of the[API /fcra_check/form](https://turnhq.stoplight.io/docs/turn-api/TurnAPIStoplight.yml/paths/~1fcra_check~1form/post)endpoint, with a two step process. First, you need to call the[Create Check Form](https://turnhq.stoplight.io/docs/turn-api/TurnAPIStoplight.yml/paths/~1fcra_check~1form/post)endpoint, specifying the package you want to run, and the zip code where the candidate resides. This won’t create a new check, but will give you directions on 1) What information to gather from the candidate and 2) All legal disclosures the candidate must agree to before running the background check.

The first response is divided into two main sections: data and disclosures. data - Has all the inputs you should gather from the candidate disclosures - This is a list of “sections” or disclosures you should display to the candidate. Each section has 4 attributes: title - Main title for the section order - Numeric order in how to display the sections. checkboxes - A list of checkboxes to display to the user copy_html - An HTML containing the text to be displayed.

Once you have gathered all user information, it’s time to call the[Submit Check Form](https://turnhq.stoplight.io/docs/turn-api/TurnAPIStoplight.yml/paths/~1fcra_check~1form/post)endpoint, you’ll provide all user information as required in the first endpoint plus a Base64 encoded image with the signature of the candidate.

Once the check is complete the results will be posted back via a webhook to the specified location provided in the callback_url parameter. See[Webhooks - Background Check Results](https://turnhq.stoplight.io/docs/turn-api/TurnAPIStoplight.yml/paths/~1fcra_check~1form/post)for details on the response.

### Query Endpoints
There might be a case where you need to poll the specific status/contents of a background check. We have two endpoints which will be useful depending on your use case: Candidate Status and Candidate Details.

Both endpoints receive a worker_id which can either be:

The full UUID of the worker eg: d54eb469-d74d-450a-b7f9-b0d98f55ac9e The shortened version, also called turn id: C1704355400

### Candidate Status
This endpoint will give you basic information about the candidate, primarily the current status.

[API /person/&lt;worker_id&gt;/status](https://apidoc.turning.io/?version=latest#6f10e036-f9be-48b5-9a7f-5986bcee4f8b)

Here is a sample response:

    {
    	"dashboard_url": "https://partners.turning.io/workers/d54eb469-d74d-450a-b7f9-b0d98f55ac9e",
    	"state": "emailed",
    	"turn_id": "C1704355400",
    	"worker_email": "someone@gmail.com",
    	"worker_id": "d54eb469-d74d-450a-b7f9-b0d98f55ac9e"
    }

### Candidate Details
This endpoint is focused on delivering the status of the worker and as much information as possible about the candidate background check results.

[API /person/&lt;worker_id&gt;/details](https://apidoc.turning.io/?version=latest#c25b098f-2f3a-40fb-bc94-bcb913ae8e64)

Here is a sample response:

    {
       "checks": {
    	   "addresses": [
    		   {
    			   "address1": "123 Main St",
    			   "city": "CHICAGO",
    			   "county": "COOK",
    			   "state": "IL",
    			   "zip": "12345",
    			   "zip4": null
    		   },
    		   [...]
    	   ],
    	   "aliases": null,
    	   "candidate_provided_date_of_birth": "1987-09-15",
    	   "candidate_provided_name": "Hari Seldon",
    	   "candidate_provided_ssn": null,
    	   "criminal": "clear",
    	   "dob_status": "matched",
    	   "location": null,
    	   "mvr": null,
    	   "name_status": "matched",
    	   "partner_provided_name": "Hari Seldon",
    	   "partner_provided_ssn": null,
    	   "public_name_status": "matched",
    	   "public_provided_name": "HARI SELDON",
    	   "public_record_date_of_birth": "1987-09-15",
    	   "sex_offender": "clear",
    	   "ssn": {
    		   "deceased_date": null,
    		   "dob_status": "",
    		   "is_deceased": false,
    		   "is_random": false,
    		   "issue_date": "IN THE YEAR 1994-1996",
    		   "issue_state": "OH",
    		   "name_status": "",
    		   "number": "*****1234",
    		   "status": "valid"
    	   },
    	   "ssn_status": "none",
    	   "watchlist": "clear"
       },
       "complete": true,
       "current_address": {
    	   "address1": "123 Main St",
    	   "address2": null,
    	   "city": "CHICAGO",
    	   "first_seen": "2016-11-01",
    	   "last_seen": "2019-08-01",
    	   "state": "IL",
    	   "zip": "12345"
       },
       "dashboard_url": "https://partners.turning.io/workers/6c72b249-d1c1-4a1e-9697-650948171738",
       "date_of_birth": "1987-09-15",
       "email": "someone@gmail.com",
       "license_number": "",
       "license_state": "",
       "name": "Hari Seldon",
       "partner_worker_status": "approved",
       "reference_id": "",
       "turn_id": "C1108624821",
       "worker_uuid": "6c72b249-d1c1-4a1e-9697-650948171739"
    }
     

The checks section will include all background-check related information.

If the check hasn’t been initiated (the candidate hasn’t filled out the consent form) this endpoint will return a 422 status along with a message stating that the report is not available yet.

If the check is being processed but hasn’t been completed, this endpoint will display the preliminary data of the report, a warning key will be appended to the response stating that no action should be taken against the candidate until the report is complete.

You can always check if the report is already completed with the complete key of the response.