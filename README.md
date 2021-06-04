# Phase 4 Project Requirements

## Learning Goals

- Build a full-stack project with a React frontend and a Rails backend

## Introduction

You've made it! You're ready to build a full-stack application with a _powerful_
backend framework! The goals of this project are to:

- put together all the skills you've learned throughout the program
- prepare you for building a capstone project in Phase 5
- build a quality project to include in your portfolio

Before you start ideating, think about some of the project requirements.

## Requirements

For this project, you must:

- Use a Rails API backend with a React frontend.
- Have at least two resources (two DB tables) on the backend and your
  application must have full CRUD actions for at least one resource.
- Have at least two different client-side routes using React Router.
- Implement authentication/authorization. At a minimum, a user should be able to
  log into the site and stay logged in via user ID in the session hash. Password
  protection is optional.

## Project Setup

To help get started on this project, the repository with the project guidelines
(the one you're reading right now!) has all the starter code needed for a Rails
API with a React frontend. It's set up the same way as all of the labs from this
phase. To set it up for your project:

- Fork and clone this repository
- Run `rails install` to download the Rails and React dependencies

You can use the following commands to run the application:

- `rails s`: run the backend on [http://localhost:3000](http://localhost:3000)
- `npm start --prefix client`: run the frontend on
  [http://localhost:4000](http://localhost:4000)
- `rails start`: run the frontend and backend together with one command

## Project Guidance

### Planning

#### User Stories

Start by deciding a domain for your app (such as "AirBNB for dogs"). Then,
decide what **user stories** your app will need. It is helpful to break up your
user stories between what is required for the [**Minimum Viable Product** (MVP)][mvp]
version of your app, and what you'd like to save for stretch features after
you've met your MVP goals.

For example:

- MVP: As a user, I can:
  - Log into the site
  - View a list of all available dog houses in my area and their reviews
  - Create a review for one specific dog house
  - Delete a review that I left
  - Create a new dog house listing
- Stretch: As a user, I can:
  - View dog houses on a map
  - Search dog houses based on their distance from my location
  - Filter dog houses based on their average rating

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
**user**, since a user is able to create a review; and a **review** belongs to a
specific **dog house**.

You can use a website like [dbdiagram.io][] to help make a ERD and represent
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

You can visualize all the parts you of an app you need to build as a grid, with
the features along the x axis (columns) and the different layers of the stack
along the y axis.

|                    | Sign in flow | View dog houses | Leave a review |
| ------------------ | ------------ | --------------- | -------------- |
| Migrations         |              |                 |                |
| Models             |              |                 |                |
| Seed Data          |              |                 |                |
| Controller actions |              |                 |                |
| View Logic         |              |                 |                |
| Data Fetching      |              |                 |                |
| Styling            |              |                 |                |

A strong temptation is to order your project timeline row-by-row. Do not do
this! If you try to build all your migrations, then all your models, then all
your controllers, then all your fetch calls, then all your view logic, you will
have a bad time. Inevitably, your view logic ends up requiring changes to the
underlying layers, and you end up building models that never end up using. If
you instead build all the **vertical slices** involved in **one feature** before
moving on to the next feature, you'll minimize rewriting, and end up with
working features without waste.

- Add feature by feature, not model by model or layer by layer.
- Test each feature, add styles, and create seed data as you go (not all at once
  at the end)

Also, remember to prioritize your MVP features. It can be tempting to try and
build everything at once, but that is a sure-fire way to end up with many broken
features instead of a solid core of working features.

## Resources

- [ERD Visualizations: dbdiagram.io][dbdiagram.io]
- [Excalidraw - basic hand-drawn wireframes](https://excalidraw.com/)
- [Figma - professional design tool](https://www.figma.com/)
- [Balsamiq - professional wireframe tool](https://balsamiq.com/)

[mvp]: https://blog.crisp.se/2016/01/25/henrikkniberg/making-sense-of-mvp
[dbdiagram.io]: https://dbdiagram.io/
[thinking in react]: https://reactjs.org/docs/thinking-in-react.html
