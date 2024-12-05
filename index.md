# Introduction

This document describes the functional requirements for the "heroexpert" application.

The Application consists of two parts:

- The part aimed at the entrepreneur (Hero)
- The part aimed at the expert.

The idea of the app is to put in contact Entrepreneurs (Heroes) with the need of a IT consultancy with experts willing to help by free. The gain is to build networking and future opportunities. 

# Flow

the simplest way to understand the flow is like so: 

- Expert join the community
- Hero post a Challenge
- Expert receives an Email and apply to the Challenge
- Hero receives an Email with application + Expert contact data, and eventually contacts him (out of the scope of this application)

[experthero-flow-figure](imgs/experthero-flow2.png)

### Entrepreneur (Hero) part

First and more important, it consists of a form with different fields where the entrepreneur proposes the challenge, project, or consultancy they need.

Once Challenge is proposed, an Email campaign is send to all related Experts. (Manually)

The entrepreneur will also have access to an administration tool where they can view all submitted requests and the experts who have offered to help. (iteration 2)

### Expert part

This section consists of a form where experts can sign up to an email list.

Whenever an entrepreneur needs help and meets the selection criteria, the expert will receive an email offering the opportunity to assist. (through the campaign email discuss in the section above)

The email will contain a link to a form where the expert can explain why they believe they are the right person for the job, as well as provide their contact details. This link will allow to "connect" the application to the related challenge internally

Optionally, through the application, the expert can access a tool where all the different help requests are listed. (iteration 2)

### Use Case Example

An entrepreneur needs help with an AI-related IT project. They access the tool and fill out the "I Need Help" form.

Later on an email will be sent to all the experts who may be a good match. (manually by now)

The email contains a detailed description of the project for which assistance is requested.

The experts can then click the "I Want to Help" button and are redirected to another form where they can explain why they believe they are a good match.

This generates an email that is sent directly to the entrepreneur for their review.

This email contains all the explanations from the expert about why they think they can help, as well as their contact information.

Additionally, both entrepreneurs and experts will have a tool (app) to view both project requests and offers of help (optional).

# Projects

Expert Hero can be split in 3 projects
## experthero.eus 

landing page where the Project is explained.

(pending to discuss design! )
## app.experthero.eus

 By now it has two differentiated and ready to be filled forms: 

- Form to join the community as an expert
- Form to propose a challenge as a hero

Everything can be done without login / sign up BUT as later step we offer the possibility to create an user for later consultancy of challenges / applications / settings / account 

In a second stage, the "app.experthero.eus" will allow both Experts and Hero to check their info like which challenges a Hero posted or which applications sent an Expert.

All this will be discussed in a second iteration.

By now it will be just a logo and an email kaixo@experthero.eus to contact for more info, change the password or so.

## shop.experthero.eus

A shop with useful items for Entrepreneurs and IT nerds

## grants.experthero.eus

A tool for searching grants (subventions) that could fit the Hero needs. (not part of this iteration)

## taxaid.experthero.eus

A tool for helping the Hero and the Expert to optimize taxes. (not part of this iteration)
# Module ExpertHero.eus

// landing page 

# Module App.expertHero.eus

- Expert Flow: 
	- Expert Join Community Form / Sign Up
	- Expert Join a Challenge
- Hero Flow: Post Challenge and Sign Up Flow
## Expert  Flow

### Expert Join Community Form / Sign Up

With this form the expert will join the community and start to receive challenges.
#### Join Form & Optional Sign Up 

Copy:  

[**expert_join_community_form**](copies_and_forms/copies_and_forms/expert_join_community_form.md)

All fields are mandatory except Telephone, also the password if checkbox `Quiero formar parte de la comunidad`

there is a captcha or similar to avoid bots.

Type of expert: (dropdown)

Technology, revenue, marketing

Email / password sign up. Sign up experience have to be super smooth and very nice mobil friendly. **UX has to be great. It is the priority.**

**By email Also double opt-in should be applied.**

Emails have to be sent in Basque or Spanish depending the Language user filled the form.

Check third party tooling. At best all logic / email opt in / receive MK / etc should be outsourced. (Think in Options!)

If the Expert uses different emails each time he will be handle as different user. 

if the Expert uses the same email we tell him that he already exist in our database and se invite him to contact kaixo@experthero.eus 

We invite him to login in to retrieve his personal data and again if he does not remember the password he can send an email to kaixo@experthero.eus

#### Thank You Page

Once the expert has join the community, besides thank him by sending an email, he will be redirected a page / showing a message where we again tell him that we are happy to have in the community

[expert_thankyou_page](copies_and_forms/copies_and_forms/expert_thankyou_page.md)

### Expert Join a Challenge

#### first iteration

Expert will join a challenge by receiving an email and with a description of the challenge

[expert_join_challenge_email](copies_and_forms/expert_join_challenge_email.md)

there is a captcha or similar to avoid bots

This challenge email will be sent as part of a Marketing Campaign with a third party marketing tool.

The link will bring to a form where the Expert will be able to explain why he thinks he is a good candidate to help the Entrepreneur with this challenge.

##### Second iteration

As we will have already an Application (Module app.experthero.eus), ideally the expert would be able to join also the challenge through the app.

#### Join the Challenge Form

As discussed above, once the expert receives the email with the challenge details, he has the opportunity to join the challenge and help the entrepreneur. 

[expert_join_challenge_form](copies_and_forms/expert_join_challenge_form.md)

there is a captcha or similar to avoid bots
## Hero Flow: Post Challenge & Signup flow

### Post a Challenge Form

As discussed previously the entrepreneur can use a form to post a challenge

with the following fields

[hero_post_challenge_form](copies_and_forms/hero_post_challenge_form.md)

> take in account that the Hero can post more than one Challenge and we should somehow don't duplicate the "sign ups" we do (Email is the primary) key.


Type of challenge: (dropdown)

Technology, revenue, marketing


When a Challenge is posted the "ADMIN" (me) should get an email informing a new challenge have been posted. 

Email to send to kaixo@experthero.eus 

email to receive as an admin [admin_hero_posted_a_challenge_email](copies_and_forms/admin_hero_posted_a_challenge_email.md)

Email / password sign up. Sign up experience have to be super smooth and very nice mobil friendly. **UX has to be great. It is the priority.**

**By email Also double opt-in should be applied.** (Validate Email)

Check third party tooling. At best all logic / email opt in / receive MK / etc should be outsourced.

If the Hero uses different emails each time he will be handle as different user 

if the Hero uses the same email we will tell him we allow to do so, overwritten the data. 

We allow the Hero to log in, (if he did it) with his password to retrieve and autocomplete some of the fields

If he does not remember the password we say in the form to contact kaixo@experthero.eus

## Thank You Page

similarly to the Expert, once the form has been filled up a new page / message / redirection will thank the entrepreneur for sending the challenge

[hero_thankyou_page](copies_and_forms/hero_thankyou_page)

## App

The app having access to challenges / experts / applications etc.. will be discussed in the next iteration.

## Challenge Export

Each time a challenge is posted an email to all experts have to be sent. 

By now it will be done manually by exporting the data from the DataBase (via SQL or API call)

Given a challenge for each expert willing to join the challenge I'g get a row with the following columns (we can talk about the naming):

```
expert_name
expert_email
challenge_title
challenge_hero_name
challenge_hero_linkedin
challenge_company_description
challenge_expert_description
challenge_cta
```

This CSV will be loaded in a MK Email tool with a template and sent as MK campaign.

There will be 2 CSV one for each language the email campaign have to be sent

## Expert Joins the Challenge

Once the email bulk with the challenge have been done, the experts will receive the challenge and in that moment they will have a link to accept the challenge. As we have discussed above with [expert_join_challenge_form](copies_and_forms/expert_join_challenge_form.md)

And in this moment the Hero will receive an email on his side telling him he has an Expert interested to help 

The email body will be [hero_expert_accepted_challenge_email](copies_and_forms/expert_join_challenge_form.md)

Of course a Hero can receive more than one Email / Expert interested. The Hero will decide on his own who to choose.

Emails he receive are in the language the Hero post the challenge. It can be changed by sending an email to kaixo@experthero.eus
# Module shop.ExpertHero.eus

- Payment Gateway
- Shop technology
- Better 
- Where to host it
# UX / UI

Everything must be available in Euskadi two official languages: Basque and Spanish.

We build a Web App but UX is the priority, it has to be great both in Mobil and Computer. The tool has to be responsive and forms have to be very easy and smooth to fill in both in Computer and Mobile. 

This is the top priority.

This tool is intended to support the Basque ecosystem and minority communities, giving priority to entrepreneurs/experts who are Basque or from marginalized groups, such as women or LGBTQ+ individuals.

[copies_and_sections](imgs/copies.png)
## Palette and colors

pending but it will be very related to the Euskadi flag colors: red, green and white

pending to select a Template 

# Technology Stack

- NextJS
- i18n? 
- Authentication? (https://nextjs.org/docs/pages/building-your-application/authentication) use a "free" auth library. Let's discuss it.
- Zoho Campaigns for sending bulk emails (Challenges to the expert)
- Zoho ZeptoEmail for transactional email
- Google Analytics for tracking. 

# Tech & More requirements

## Tech stack

NextJS, ORM (??), Typescript, AWS Cloud, Kubernetes, Postgress

## Cookies

We need cookies support: 

https://www.npmjs.com/package/vanilla-cookieconsent
https://www.termsfeed.com/

# Future (add AI support)

When Expert join the community add some info about himself and also a description and the Linked-in and so on, therefore when the challenge is set it is filtered based in AI decisions.

# Questions open to Dev

- I'd like that experthero.es and others redirect to experthero.eus transparently. Possible?

## Tasks

- Hero - Post a Challenge Form (as part of the App)
- Expert - Join Community Form (as part of the App)
- Expert - Join Challenge Form (as part of the App)
- Landing Page (if it is included in the App) - Vicens
- Zoho Campaigns exports (Challenge & related Experts) 
- Zoho Campaign config - Vicens
- Transactional Email API connections & Templates (Vicens & Andreu)
- eCommerce Shop  - Wordpress x Woocommerce
- Design (Euskera!) 
- Two languages (Spanish / Euskera)


