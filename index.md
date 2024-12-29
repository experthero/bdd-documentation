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

### Expert Join Community Form

With this form the expert will join the community and start to receive challenges.
#### Form 

[**expert_join_community_form**](copies_and_forms/expert_join_community_form.md)

There is a captcha or similar to avoid bots. It will be enabled but a env variable. Default value "inactive", if not present it will be also inactive

Email / password sign up. Sign up experience have to be super smooth and very nice mobil friendly. **UX has to be great. It is the priority.**

**By email Also double opt-in should be applied.**

Emails have to be sent in Basque or Spanish depending the Language user filled the form.

If the Expert uses different emails each time he will be handle as different user. 

if the Expert uses the same email we tell him that he already exist in our database and se invite him to contact kaixo@experthero.eus 

We invite him to login in to retrieve his personal data and again if he does not remember the password he can send an email to kaixo@experthero.eus

#### Validate Email

```
Subject: Valida tu dirección de correo electrónico
Body: 

¡Bienvenido a Nuestra Comunidad de Expertos!

Hola {{Username}},

Gracias por unirte a nuestra comunidad de expertos. Estamos encantados de tenerte con nosotros. Para comenzar, por favor confirma tu correo electrónico haciendo clic en el botón de abajo.

[ CTA Button "Confirmar Correo"]

Si ya has validado este email, por favor ignora este mensaje o contacta con el soporte si tienes alguna pregunta.

<small> Recibiste este mensaje porque te uniste a nuestra comunidad mediante nuestro sitio web. Si no fuiste tú, por favor [contacta con el soporte (kaixo@experthero.eus)](mailto:kaixo@experthero.eus).  

© 2024 ExpertHero. Todos los derechos reservados.

```

(*) Please use as Guidelines the Template Design in Transcational Platform
#### Thank You Page

Once the expert has join the community he will be redirected a page / showing a message where we again tell him that we are happy to have in the community

The expert will receive an email for validating the email. Once he clicks he will be redirected to a page that thanks him do doing it.

```bash
¡Tu correo electrónico ha sido verificado con éxito! 🎉

Gracias por confirmar tu dirección de correo electrónico.
Tan pronto como haya un reto que se adapte a tus necesidades nos pondremos en contacto.

<button go home>
```

### Expert Join a Challenge

Expert will join a challenge by receiving an email and with a description of the challenge

[expert_join_challenge_email](copies_and_forms/expert_join_challenge_email.md)

This challenge email will be sent as part of a Marketing Campaign with a third party marketing tool.

In the email there is a link to a Form .

The link will bring to a form where the Expert will be able to explain why he thinks he is a good candidate to help the Entrepreneur with this challenge.

#### Join the Challenge Form

As discussed above, once the expert receives the email with the challenge details, he has the opportunity to join the challenge and help the entrepreneur. 

[expert_join_challenge_form](copies_and_forms/expert_join_challenge_form.md)

there is a captcha or similar to avoid bots. It will be enabled but a env variable. Default value "inactive", if not present it will be also inactive

IMPORTANT: Once the Expert Join a Challenge, 2 emails will be sent: 

- One email to the Hero sending him the info of the expert
- One email to the ADMIN, letting him know an expert is willing to help

#### Email Validate

```
Subject: Valida tu dirección de correo electrónico
Body: 

¡Muchas gracias por publicar un Reto en nuestra comunidad de expertos!

Hola {{Username}},

muchas gracias por publicar un Reto en nuestra comunidad de expertos. Estamos encantados de tenerte con nosotros. Para comenzar, por favor confirma tu correo electrónico haciendo clic en el botón de abajo.

[ CTA Button "Confirmar Correo"]

Si ya has validado este email, por favor ignora el mensaje o contacta con el soporte si tienes alguna pregunta.

<small> Recibiste este mensaje porque has publicado un reto en nuestro sitio web. Si no fuiste tú, por favor [contacta con el soporte (kaixo@experthero.eus)](mailto:kaixo@experthero.eus).  

© 2024 ExpertHero. Todos los derechos reservados.
```

#### Thank you Page

Once Form is completed a `thankyou` page will be shown with the following text: 

```
Hola <name of expert>

Gracias por aceptar esta challenge. El Hero será inmediaamente notificado por email y se pondrá en contacto contigo si cree que puedes ser de ayuda.

Un saludo del equipo de Expert Hero

Para cualquier cosa no dudes en ponerte en contacto con nosotros en kaixo@experthero.eus
```

#### Email to Experts (Manual)

As discussed when a new challenge is posted an Email is triggered to the Experts. This process is manual.

[hero_expert_accepted_challenge_email](copies_and_forms/hero_expert_accepted_challenge_email.md)

Through a query the Admin will retrieve all the experts that  have that will be sent the challenge. 

See [Challenge Export](Challenge%20Export)

#### Email to Admin

As stated above the admin will also receive an email to let him know there is a match

```
Subject: ExpertHero: There is a match!

Body: 

Hero

[Hero Name]
[Hero Surname]
[Hero Company]
[Hero Linkedin]
[Hero email]
[Hero Telephone]

[ Descripción del tu empresa ]ea
[ Titulo del reto ] 
[ Descripción del reto ]
[ Descripción del candidato ideal ]

Expert

Expert Nombre: 
Expert LastName 
Expert Linkedin:
Expert Email: 
Expert Tephone 

[Message Expert wrote to the Hero]

[Message Expert wrote about how he can help]
```

## Hero Flow: Post Challenge & Signup flow

### Post a Challenge Form

As discussed previously the entrepreneur can use a form to post a challenge

with the following fields

[hero_post_challenge_form](copies_and_forms/hero_post_challenge_form.md)

> take in account that the Hero can post more than one Challenge and we should somehow don't duplicate the "sign ups" we do (Email is the primary) key.


When a Challenge is posted the "ADMIN" (me) should get an email informing a new challenge have been posted. 

Email to send to kaixo@experthero.eus 

email to receive as an admin [admin_hero_posted_a_challenge_email](copies_and_forms/admin_hero_posted_a_challenge_email.md)

UX has to be great. It is the priority.

**By email Also double opt-in should be applied.** (Validate Email)

If the Hero uses different emails each time he will be handle as different user. 

if the Hero uses the same email we will tell him we allow to do so, overwritten the user data. 
### Thank You Page

Similarly to the Expert, once the form has been filled up a new page / message / redirection will thank the entrepreneur for sending the challenge

[hero_thankyou_page](copies_and_forms/hero_thankyou_page)

### Verify Email Hero

The expert will receive an email for validating the email. Once he clicks he will be redirected to a page that thanks him do doing it

```bash
¡Tu correo electrónico ha sido verificado con éxito! 🎉

Gracias por confirmar tu dirección de correo electrónico. 

Estamos revisando el reto para evitar un mal uso de la herramienta. En breve, el reto será compartido con los expertos que mejor se adapten a tus necesidades.

<button go experthero.eus>
```

## App

The app having access to challenges / experts / applications etc.. will be discussed in the next iteration.

## Challenge Export

Each time a challenge is posted an email to all experts have to be sent. 

By now it will be done **manually** by exporting the data from the DataBase (via SQL)

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

Other considerations: 

- This CSV will be loaded in a MK Email tool with a template and sent as MK campaign.
- There will be 2 CSV one for each language the email campaign have to be sent.
- The query has to allow to filter for those experts that are active or not. 
- Also it would be good to know if there is any email sent to this expert in regards the given Challenge.

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

# Others

## Non functional requirements. 

### Email Logging

Email sending should be properly logged in Database so given a challenge we can now which emails where send to a Hero and which Experts were included in this challenge: 

Of course a global email sent log would be good if possible
## UX / UI

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

## Tech & More requirements

## Tech stack

NextJS, ORM (??), Typescript, AWS Cloud, Kubernetes, Postgress

## Cookies

We need cookies support: 

https://www.npmjs.com/package/vanilla-cookieconsent
https://www.termsfeed.com/

# Future 

Add AI Support

When Expert join the community add some info about himself and also a description and the Linked-in and so on, therefore when the challenge is set it is filtered based in AI decisions.






