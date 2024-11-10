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

[[ExpertHero - Expert - Join Community & Login Flow]]

#### Join Form & Optional Sign Up 

Copy:  

```
Unete a la comunidad de portfolio CTO para comenzar a recibir retos con los que ayudar a emprendedores a crear sus proyectos. Crea una red de contactos y enfrentate a retos que ponen a prueba y complementan tus habilidades. 

Es muy fácil!

(not definitive copy)
```

Form
```
[   Nombre   ] Input
[   Apellidos   ] Input 
[ perfil de LinkedIn ] Input 
[   Teléfono.  ] Input (i) Si añades tu teléfono el emprendedor te podra contactar directamente, además en el futuro te podremos enviar challenges mediante sms o whatsapp. (No te preocupes te pediremos permiso nuevamente antes)

[x] Quiero formar parte de la comunidad (i) legal note
[ Contraseña ] Input Password 

[ ] Quiero recibir informacion de otro tipo, eventos e informaciones de interes

(i) al formar parte de la comunidad reconoces que blah blah .. (legal things)

| Enviar |
```

```
Al enviar esta formulario das por hecho que aceptas el envio exclusivamente de challenges a tu bandeja de email email. 
```

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

Copy: 

```
Hola <name of expert>

Gracias por apoyar esta comunidad! A partir de ahora cada vez que haya un Challenge seras notificado por email y podras ayudar si asi lo deseas.

<dynamic part App WIP, see below >

Un saludo del equipo de Expert Hero

Para cualquier cosa no dudes en ponerte en contacto con nosotros en support@experthero.eus
```

##### dynamic App WIP

If he has Sign Up the community we will let him know that we are working in an administration panel where he will be able to manage the open challenges and more.

Copy 
```
En breve pondremos a tu disposición una aplicación donde podrás hacer seguimiento de todas las challenges lanzadados y tus aplicaciones. 

Por ahora, estate atento ya los challenges te llegaran por email!
```

### Expert Join a Challenge

#### first iteration

Expert will join a challenge by receiving an email and with a description of the challenge

###### Join the Challenge Email

Subject: 

```
Nuevo Reto Disponible
```

Body: 
```
Hola <name of the expert>

Tenemos otra solicitud para un mentor/asesor. Por favor, lee los detalles a continuación y, si estás dispuesto a ayudar, completa el formulario.

|| Acepta el Reto ||

Empresa / Emprendedor

// blah blah (is comming from Challenge info)

Descripcion del reto

// blah blah (is comming from Challenge info)

A quien estan buscando idealmente

// blah blah (is comming from Challenge info)

Acepta el Reto y ayuda a <name of the enterprenour> ! [ Link ]
```

This challenge email will be sent as part of a Marketing Campaign with a third party marketing tool.

The link will bring to a form where the Expert will be able to explain why he thinks he is a good candidate to help the Entrepreneur with this challenge.

##### Second iteration

As we will have already an Application (Module app.experthero.eus), ideally the expert would be able to join also the challenge through the app.

#### Join the Challenge Form

As discussed above, once the expert receives the email with the challenge details, he has the opportunity to join the challenge and help the entrepreneur. 

```
Hola <nombre del experto>

Gracias por ofrecerte a ayudar a <nombre del Emprendedor> con su reto <nombre del reto>

En que area podrias ayudar
[     ] Text Area

Escribe tu mensaje al Emprendedor
[     ] Text Area

[x] Confirmación *

* Marca la casilla para confirmar que estas dispuesto a ofrecer al menos una hora de ayuda y asesoramiento gratuitos a este emprendedor.

Por supuesto, puede ofrecer mucho trabajo de forma gratuita si lo desea, o puedes ofrecer solo una hora y comunicarle al fundador tus honorarios por si desea contratarte más.

<dynamic Join the community, see below>

| Enviar |


Feedback a la organizacion. Siempre queremos mejorar por lo que si tienes algo que decirnos puedes escribirnos a support@experthero.eus
```

We assume we know already the firstName, lastName and email  of the Expert. We also know if he has join the community or not. 

Therefore if he still has not join the community we will ask him kindly to do so:

```
[x] Quiero formar parte de la comunidad (i) legal note
[ Contraseña ] Input Password 
```

In any case after filling the form we will redirect him to a thank you page / show a message: 

```
Petición de ayuda enviada! 

Nuevamente, gracias por querere ayudar a <nombre de emprendedor> con <nombre del reto>

El acaba de recibir tu ofrecimiento y te responderá en breve si cree que puedes ser ayuda. 

Para cualquier pregunta no dudes en contactarnos support@experthero.eus
```
## Hero Flow: Post Challenge & Signup flow

[[ExpertHero - Hero - Post Challenge & Sign Up Flow]]
### Post a Challenge Form

As discussed previously the entrepreneur can use a form to post a challenge

with the following fields

```

Hola!

Gracias por utilizar ExpertHero para buscar expertos con los que hacer que tus ideas se hagan realidad. 

Por favor, rellena este formulario y nos pondremos en contacto con aquellos expertos que puedan ayudarte comunicandotelo por email con la mayor brevedad posible.

[ Nombre] Input
[ Apellidos] Input
[ Compañia ] Input
[ perfil de LinkedIn ] Input 
[ Email ] Input
[ Telephone ] Input (i) Si añades tu teléfono en el futuro te podremos enviar challenges mediante sms o whatsapp. (No te preocupes te pediremos permiso nuevamente antes)

[x] Quiero formar parte de la comunidad  (i) legal note
[ Contraseña ] Input field Password

Explicanos tu Proyecto:

[ Descripción del tu empresa ] Text Area
[ Titulo del reto ] Input
[ Descripción del reto ] Text Area
[ Descripción del candidato ideal ] Text Area

| Enviar |

Para cualquier duda o pregunta puedes enviarnos un email a support@experthero.com

(i) al formar parte de la comunidad reconoces que blah blah .. (legal things)
```

### First iteration 

Email / password sign up. Sign up experience have to be super smooth and very nice mobil friendly. **UX has to be great. It is the priority.**

**By email Also double opt-in should be applied.** (Validate Email)

Check third party tooling. At best all logic / email opt in / receive MK / etc should be outsourced.
### Second iteration

Sign Up Can support third party authentication platforms (google / apple / etc..) besides the name / email / password login 

Match between third party and internal email has to be taken. By email Also double opt-in should be applied.

# Module App.ExpertHero.eus

// pending

# Module Shop.ExpertHero.eus

// pending
# UX / UI

Everything must be available in Euskadi two official languages: Basque and Spanish.

We build a Web App but UX is the priority, it has to be great both in Mobil and Computer. The tool has to be responsive and forms have to be very easy and smooth to fill in both in Computer and Mobile. 

This is the top priority.

This tool is intended to support the Basque ecosystem and minority communities, giving priority to entrepreneurs/experts who are Basque or from marginalized groups, such as women or LGBTQ+ individuals.

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
