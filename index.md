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

![[experthero-flow.png]]

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

landing page where the Project is explained and with two differentiated and ready to be filled forms: 

- Form to join the community as an expert
- Form to propose a challenge as a hero

Everything can be done without login / sign up BUT as later step we offer the possibility to create an user for later consultancy of challenges / applications / settings / account 

(pending to discuss design! )
## app.experthero.eus

App where we will allow both Experts and Hero to check their info like which challenges a Hero posted or which applications sent an Expert

All this will be discussed in a second iteration.

By now it will be just a logo and an email support@experthero.eus to contact for more info, change the password or so.

## shop.experthero.eus

A shop with useful items for Entrepreneurs and IT nerds

## grants.experthero.eus

A tool for searching grants (subventions) that could fit the Hero needs. (not part of this iteration)

## taxaid.experthero.eus

A tool for helping the Hero and the Expert to optimize taxes. (not part of this iteration)
# Module ExpertHero.eus

- Expert Flow: 
	- Expert Join Community Form / Sign Up
	- Expert Join a Challenge
- Hero Flow: Post Challenge and Sign Up Flow
## Expert  Flow

### Expert Join Community Form / Sign Up

With this form the expert will join the community and start to receive challenges.
#### Join Form & Optional Sign Up 

Copy:  

[**expert_join_community_form**](expert_join_community_form.md)

All fields are mandatory except Telephone, also the password if checkbox `Quiero formar parte de la comunidad`
##### **First iteration** 

Email / password sign up. Sign up experience have to be super smooth and very nice mobil friendly. **UX has to be great. It is the priority.**

**By email Also double opt-in should be applied.**

Check third party tooling. At best all logic / email opt in / receive MK / etc should be outsourced. (Think in Options!)
##### **Second iteration**

Sign Up Can support third party authentication platforms (google / apple / etc..) besides the name / email / password login 

Match between third party and internal email has to be taken. By email Also double opt-in should be applied.

#### Thank You Page

Once the expert has join the community, besides thank him by sending an email, he will be redirected a page / showing a message where we again tell him that we are happy to have in the community

[expert_thankyou_page](expert_thankyou_page.md)

### Expert Join a Challenge

#### first iteration

Expert will join a challenge by receiving an email and with a description of the challenge

[expert_join_challenge_email](copies_and_forms/expert_join_challenge_email.md)

This challenge email will be sent as part of a Marketing Campaign with a third party marketing tool.

The link will bring to a form where the Expert will be able to explain why he thinks he is a good candidate to help the Entrepreneur with this challenge.

##### Second iteration

As we will have already an Application (Module app.experthero.eus), ideally the expert would be able to join also the challenge through the app.

#### Join the Challenge Form

As discussed above, once the expert receives the email with the challenge details, he has the opportunity to join the challenge and help the entrepreneur. 

[expert_join_challenge_form](copies_and_forms/expert_join_challenge_form.md)
## Hero Flow: Post Challenge & Signup flow

### Post a Challenge Form

As discussed previously the entrepreneur can use a form to post a challenge

with the following fields

[hero_post_challenge_form](copies_and_forms/hero_post_challenge_form.md)

### First iteration 

Email / password sign up. Sign up experience have to be super smooth and very nice mobil friendly. **UX has to be great. It is the priority.**

**By email Also double opt-in should be applied.** (Validate Email)

Check third party tooling. At best all logic / email opt in / receive MK / etc should be outsourced.
### Second iteration

Sign Up Can support third party authentication platforms (google / apple / etc..) besides the name / email / password login 

Match between third party and internal email has to be taken. By email Also double opt-in should be applied.

## Thank You Page

similarly to the Expert, once the form has been filled up a new page / message / redirection will thank the entrepreneur for sending the challenge

[hero_thankyou_page](copies_and_forms/hero_thankyou_page)
# Module app.ExpertHero.eus

// next iteration

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

## Palette and colors

pending but it will be very related to the Euskadi flag colors: red, green and white

# Technology Stack

- React SSR & NextJS
- i18n? 
- Authentication? (https://nextjs.org/docs/pages/building-your-application/authentication) use a "free" auth library. Let's discuss it.
- Zoho Campaigns for sending bulk emails (Challenges to the expert)
- Zoho ZeptoEmail for transactional email
- Google Analytics for tracking. 

# Future (add AI support)

When Expert join the community add some info about himself and also a description and the Linked-in and so on, therefore when the challenge is set it is filtered based in AI decisions.

# Questions to Dev

- Do you need design for the experthero.eus ?
- I'd like that experthero.es and others redirect to experthero.eus transparently. Possible?
- Zoho Campaign Export pending to discussion
- Admin tools by now will be to have access to the DB 
- It would be great if texts can be tweaked without Dev help.
