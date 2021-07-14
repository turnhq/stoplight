# Set Up & Integrations
Once you [sign up](#Sign-Up-For-a-Subscription) for Sourcing, we’ll work with your team to complete your Sourcing configuration.

We’ll determine the below:

1.  What [cities](#By-Location) you’re actively hiring in
2.  If you’d like us to automatically inject Turn Applicants into your preferred onboarding workflow using our [Webhook API](#Webhook-API) or [ATS Integration](#API-or-ATS-Integration) options. We have ATS integrations for [Fountain](https://get.fountain.com/) and [Greenhouse](https://www.greenhouse.io/integrations/turn-technologies).
3.  How Turn will receive [task completion and performance data](#Workforce--API) for active workers acquired via Sourcing

## Fountain Integration for Sourcing
Our Fountain integration allows us to inject Turn Applicants directly into your existing workflows. This helps to push potential workers through your onboarding stages as quickly as possible.

Setup typically takes about 1 business day or less.

To complete an integration with Fountain, we’ll gather the below information from you:

1.  The **Opening ID** of the workflow you’d like Turn Applicants added to. We can also drop candidates into multiple workflows based on location.
2.  For each workflow, we can drop Turn applicants into any desired stage.

Each Turn Applicant added to Fountain will include the following profile attributes:

* First name
* Last name
* Email address
* Zip code 
* Phone number
* Date of birth
* State 
* City

## Greenhouse Integration for Sourcing
Our Greenhouse integration allows us to inject Turn Applicants directly into your existing applicant workflow. This helps push potential workers through your onboarding stages quickly.

Setup typically takes about 1 business day or less.

To complete an integration with Greenhouse, we’ll gather the below information from you:

* The **Application ID** of the opportunity you want Turn Applicants to be added to

Each Turn Applicant added to Greenhouse will include the following profile attributes:

* First name
* Last name
* Email address
* Phone number

Each Turn Applicant is added to the **first step** of your application workflow.

## Webhook API
If you’re not using an ATS to track your applicants, you can take advantage of our [Webhook API](https://apidoc.turning.io/#2c2193a9-1319-48c9-88ed-4c009cdffc2a). This will inject workers into the system you use to track and onboard incoming applicants.

Implementation will require a developer resource on your team to set up the ability to receive the incoming webhook and initiate your onboarding flow using the Applicant Profile. 

Each Turn Applicant received will include the following profile attributes:

* First name
* Last name
* Email address
* Zip code 
* Phone number
* Date of birth
* State 
* City 
* Experience/interests
* Transportation method

## Onboarding API
Our Onboarding API is an easy way to receive Turn Applicants in your existing onboarding funnel. Setting up this API will enable us to inject workers, along with their profile properties, into your preferred tracking system and desired stage. This takes the manual follow-up out of starting to approve applicants for work—so you no longer have to export and import applicants into your hiring flow!

Additionally, this API enables Turn to understand where an applicant is in your hiring flow by detecting:

* If there is something stopping an applicant from being hired
* If and when an applicant completes a milestone
* If and when an applicant is rejected
* If and when an applicant is cleared/approved to start completing tasks

Turn will then use this data to help re-engage with applicants that have shown interest in working for you and drive them to complete your onboarding. Our ultimate goal is to send you applicants that turn into reliable workers, helping your business grow in the markets where you need it most.

### Initial Setup At-a-Glance
In order to set up our Onboarding API we’ll work with you to define the steps in your onboarding flow. Each step is defined with a name, order position, and indication of the responsible party. A complete onboarding flow is composed of 1 or more steps.

**Example:**

**![image (1).png](https://cdn.buttercms.com/9MfpZt3XQLuaXlkesuBk)![image.png](https://cdn.buttercms.com/jibYFLqaST2JccoZAYxU)**

### Creating an onboarding flow
To set up an onboarding flow first we would need to create one sending its name and steps. (For example, using Python* and [Requests](https://pypi.org/project/requests/) library):

![Create onboarding.png](https://cdn.buttercms.com/Rfz3yHplTxiZTcIsr993)

_*  For other languages, see_ [_https://apidoc.turning.io/#d72c56c6-fc37-4827-b2b4-58b2d0ac14da_](https://apidoc.turning.io/#d72c56c6-fc37-4827-b2b4-58b2d0ac14da)

_*  If you want to change the onboarding flow name or its steps you can contact the support team.  
_

### Moving candidates through the  onboarding flow
Once you have candidates you can move them through the onboarding process in different ways, you can move them to a specific step using the name. (For example, using Python* and [Requests](https://pypi.org/project/requests/) library):

![undefined](https://cdn.buttercms.com/1A40M6vfRG6cvLswjGXP)

**Or you can move it one step forward or backward relative to its current step. Example:**

**![undefined](https://cdn.buttercms.com/o3mFTjcvShatU3nfZ7Aq)**

**Also, you can move it to the start or end of the flow. Example:**

**![undefined](https://cdn.buttercms.com/UzXTRMdbQxm8b9LZwqOz)**

**And finally, you can change it to approved, rejected, and withdrawn. Example:**

**![undefined](https://cdn.buttercms.com/TopyzSucSg6BRkOWsbiD)**

_*  For other languages, see_ [_https://apidoc.turning.io/#d72c56c6-fc37-4827-b2b4-58b2d0ac14da_](https://apidoc.turning.io/#d72c56c6-fc37-4827-b2b4-58b2d0ac14da)

## Workforce  API
With our [Workforce API](https://apidoc.turning.io/?version=latest#05bc8a90-a566-4c13-9d64-bd9cc8e78893) you can send task completion and performance data for active workers acquired via Sourcing back to Turn. These insights enable us to:

* Provide you real, performance-based pricing options based on task completion
* Drive engagement and help active workers reach key milestones with your business 
* Programmatically refresh active workers’ background checks
* Qualify your active workers for ancillary services through Turn such as benefits, financial services, and incentive-based perks 

Turn’s flexible API lets you integrate in a customizable way. In this section, we will cover all the ways you can start an integration with Turn’s Workforce API.

#### Getting an API JWT Token

To interact with any of our REST API, you’ll need an API JWT Token. You can [contact us](https://docs.google.com/document/d/1zV5qTxJrj4vsjDj2eRP8o_ZrKij50JA_bPvsCfUj89k/edit?userstoinvite=jose@turning.io&ts=5f6a33b0#heading=h.5battufsr2ui) at [support@turning.io](mailto:support@turning.io) to get one.

Every request must contain the Authorization header with the JWT Token. You can refer to our [full API Documentation](https://apidoc.turning.io/) for more information on how Authentication works.

#### Data Points

You can push a variety of information about your active workers, at different points in time.

All data points you push can be “partial”, meaning you can easily update it as you’re made aware of new information. For example, you can push Task Completion data to our Tasks endpoint as soon as the Worker starts that Task even if it has not been completed yet (you don’t know when the Task has been completed). Later, by using the same ID you provided before, you can push the data again and we’ll update our records accordingly.

#### Submitting Data Points with a Turn ID

Our REST API is designed to receive data as soon as you learn about it, but you’re also able to submit data at any time.

For example (using Python and [Requests](https://pypi.org/project/requests/) library):

#### Submitting Data without a Turn ID

By using our [External Profile API](https://apidoc.turning.io/#561f36d6-ff7a-4849-966f-100a335cd3ea), you’ll be able to submit Data Points without using a Turn ID. To match your worker, we’ll use their personal details instead.

For example (using Python and [Requests](https://pypi.org/project/requests/) library):



























