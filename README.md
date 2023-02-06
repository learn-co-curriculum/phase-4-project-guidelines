# Phase 4 Project Guidelines

## Learning Goals

- Build a full-stack project with a React frontend and a Rails backend

## Introduction

You've made it! You're ready to build a full-stack application with a _powerful_
backend framework! The goals of this project are to:

- put together all the skills you've learned throughout the program
- prepare you for building a capstone project in Phase 5
- build a quality project to include in your portfolio

The instructions below will walk you through the process of ideating and
planning your app: deciding on your models and relationships, planning how the
information will be laid out on the page, etc. You should work through all the
planning steps before you start doing any coding.

## Requirements

For this project, you must:

- Use a Rails API backend with a React frontend.
  - Follow best practices for both front and back end
  - Proper RESTful routing
  - Do not rely on redirects and reloads to refresh data
  - No document.reload or window.reload in your application
  - Do not use GET requests to update state after a POST, PATCH, or DELETE request. You should be adding to, updating, or removing from state instead.
- Have at least three models on the backend, that include:
  - at least one many-to-many relationship
    - You need a join table with two foreign keys
    - You will need two has many/belongs to relationships to implement
    - Implement many to many by writing two has many through relationships
    - YOU MUST DISPLAY AT LEAST ONE SIDE OF THIS RELATIONSHIP IN YOUR APPLICATION AND SHOW IT WORKS PROPERLY, other half can be evaluated in console
- Separation of concerns → don’t force the front end to do the work of the back end. Pass needed associated objects in your JSON rather than asking the front end to figure out which items are associated with which - example of what not to do: using useEffect to retrieve all of two separate but associated items and using filter to find the associated items for a given thing.  Sending nested JSON allows the front end to directly access the associated items without filtering through them all. 
- full CRUD actions for at least one resource
  - A ‘like’ functionality will not count for an update, you must use a form that is pre-filled with existing values for the object. On submission of update form, the object updates appropriately.
  - Validations and error messages also expected to be present
- Have at least three different client-side routes using React Router. Be sure to include a nav bar or other UI element that allows users to navigate between routes.
  - RESTful routing where applicable
- Implement authentication/authorization, including password protection. A user should be able to log in to the site with a secure password and stay logged in via user ID in the session hash.
  - Ensure you are able to walk through and explain the authentication process
  - Ensure that one user is unable to edit or delete a resource created by another user. Only if the logged in user is the creator should they have this ability. 

**Note**: a user should only be able to edit and delete resources if they are
logged in and the creator of that resource. For example, if we consider the
example described below with models of User, DogHouse, and Review, I would only
be able to edit or delete the reviews that I created.

## Project Setup

Once you've got a solid plan in place for your app and you're ready to start
coding, it's recommended that you use this project template:

- [https://github.com/learn-co-curriculum/project-template-react-rails-api][project template]

The project template is set up the same way as all of the labs from this phase.
It has also been configured to enable you to deploy the app to Render using a
similar process to the one described in the Deploying module.

Make sure to follow the setup instructions in the template's readme to get
started.

Alternately, if you'd like to set everything up from scratch, you can use this
project setup guide:

- [https://github.com/learn-co-curriculum/react-rails-project-setup-guide][project setup]

## Project Guidance

### Planning

#### User Stories

Start by deciding on a domain for your app (such as "AirBNB for dogs"). Then,
decide what **user stories** your app will need. It is helpful to break up your
user stories between what is required for the [**Minimum Viable Product** (MVP)][mvp]
version of your app, and what you'd like to save for stretch features after
you've met your MVP goals.

For example:

- MVP: As a user, I can:
  - Sign up for an account,
  - Log in to the site & remain logged in,
  - Log out,
  - View a list of all available dog houses in my area and their respective
    reviews,
  - Create a review for one specific dog house,
  - Modify or delete a review that I left,
  - Create a new dog house listing.
- Stretch: As a user, I can:
  - View dog houses on a map,
  - Search dog houses based on their distance from my location,
  - Filter dog houses based on their average rating.

#### Models and Relationships

After deciding on your app's user stories, you can design the **models** that
your application will need in order to represent these user stories.

Look at the list of your user stories, and pick out the different nouns/objects
that you need to represent these user stories. These objects inform what models
you need. For example, from the list above, we have:

- User
- Dog House
- Review

You can also get a sense of the relationships between the models and use that as
the basis of your **Entity Relationship Diagram** (ERD). For example, we can
tell based on the user stories above that a **review** belongs to a specific
**user** — since a user is able to create a review — and a **review** belongs to
a specific **dog house**.

You can use a website like [dbdiagram.io][] to help make an ERD and represent
these relationships, or draw out something simple:

```txt
User -< Review >- DogHouse

DogHouse >- User
```

This is also a good time to think about what attributes your models will need.
What foreign keys are needed to establish relationships? What other attributes
might you need to display data in your frontend, or make other aspects of your
user stories work?

#### Wireframes

For your frontend, it's a good idea to follow the ideas from
[Thinking in React][] as you're designing your React application. That means
starting with a visual representation of what your application should look like,
in the form of a wireframe. The wireframe should give you a basic visual
representation of what each page of your application should look like, and it
should capture all of your user stories.

Here are some tools for wireframing (pen and paper is also a fine choice!):

- [Excalidraw - basic hand-drawn wireframes](https://excalidraw.com/)
- [Figma - professional design tool](https://www.figma.com/)
- [Balsamiq - professional wireframe tool](https://balsamiq.com/)

Use your wireframe to plan out what components you'll need and design your
component hierarchy, following the ideas from [Thinking in React][].

### Execution

Once you have your plan in place, and have a sense of your:

- User stories
- Models (including relationships and attributes)
- Wireframes

It's time to start building! As you're building, work on each feature in
[vertical slices](https://agileforall.com/vertical-slices-and-scale/) rather
than horizontal. For example, rather than building out **all** the models,
routes and controller actions in the backend, then working on the components in
the frontend and finally styling everything, work on one **feature** at a time,
such as working on login, then displaying a list of dog houses, then leaving a
review.

You can visualize all the parts of an app you need to build as a grid, with the
desired features in columns and the different layers of the stack in rows:

|                    | Sign in flow | View dog houses | Leave a review |
| ------------------ | ------------ | --------------- | -------------- |
| Migrations         |              |                 |                |
| Models             |              |                 |                |
| Seed Data          |              |                 |                |
| Controller actions |              |                 |                |
| View Logic         |              |                 |                |
| Data Fetching      |              |                 |                |
| Styling            |              |                 |                |

You may be tempted to order your project timeline row-by-row. Do not do this! If
you try to build all your migrations, then all your models, then all your
controllers, then all your fetch calls, then all your view logic you will have
a bad time. Inevitably, your view logic ends up requiring changes to the
underlying layers, and you end up building models that you never use. If you
instead build **each feature** (each **vertical slice**) in its entirety before
moving on to the next feature, you'll minimize rewriting, and end up with
working features without waste.

- Add feature by feature, not model by model or layer by layer.
- Test each feature, add styles, and create seed data as you go (not all at once
  at the end)

Also, remember to prioritize your MVP features. It can be tempting to try and
build everything at once, but that is a sure-fire way to end up with many broken
features instead of a solid core of working features.

## Deploying

The template project has all the starter code needed to help you deploy your
application to Render. It's recommended to deploy your project early and push up
changes often to ensure that your code works equally well in production and
development environments.

Follow the instructions in the template to deploy your app!

## Resources

- [Project Template: React/Rails API][project template]
- [ERD Visualizations: dbdiagram.io][dbdiagram.io]
- [Excalidraw - basic hand-drawn wireframes](https://excalidraw.com/)
- [Figma - professional design tool](https://www.figma.com/)
- [Balsamiq - professional wireframe tool](https://balsamiq.com/)

[mvp]: https://blog.crisp.se/2016/01/25/henrikkniberg/making-sense-of-mvp
[dbdiagram.io]: https://dbdiagram.io/
[thinking in react]: https://reactjs.org/docs/thinking-in-react.html
[project template]: https://github.com/learn-co-curriculum/project-template-react-rails-api
[project setup]: https://github.com/learn-co-curriculum/react-rails-project-setup-guide
