---
Title: WEB Journal 
categories: [WEB, Journal]
tags: [WEB]
---

# Topic : Finals Journal

In this project, we embarked on developing a full-stack web application that models a popular digital service marketplace(Website for Auction place). The aim was to create a platform similar to eBay, Craigslist, or Etsy, incorporating essential features such as pagination, user authentication and authorization, RESTful API endpoints, and real-time data communication using WebSockets. This journal documents the journey, including the development process, challenges encountered, and how we addressed them as a group and individual by doing out parts in the project.

## Planning and Design

Before planning and designing we went onto looking foe a website inspiration as sir instructed and it looks like this:

- https://www.figma.com/community/file/1012786849389587697

Our initial step was to plan and design the application's architecture. We chose the following technology stack:

- Frontend: React.js and Next.js for building a responsive user interface.
- Backend: Use Typescript to create the server and RESTful API.
- Database: sqlite for storing user, product and marketplace data.
- Authentication: JWT (JSON Web Tokens) for secure user authentication and authorization.
- Real-Time Communication: WebSockets (Socket.io) for enabling active chatting.

We outlined the core features and divided them into manageable tasks:

1. User Authentication and Authorization
2. RESTful API Development
3. Pagination Implementation
4. Real-Time Data Communication

And from this part individual members of the group will share how there journey was while doing the project:

### Tandin Zangmo's Journal

I set up the Signup and Login page using React by having the code run on the client-side with the command used, “use client”. For state, I imported the useState hook which is one of the hooks provided built-in hooks which can be used by default in functional components, and I also imported a BUTTON component from a UI library. I took state for user input (name, phone number, email and password) and state for errors (for validation) using useState. I defined a handleSubmit function to stop the form submission, and with the help of formik library to validate the inputs and with the help of axios library I made a POST request to the server with the data of the user and logged the responses accordingly. Also, the handleChange function modifies the form data as the user is inputting data. The form created using the JSX and designed on the Tailwind CSS contains the forms’ input, prompts the errors, users’ assistance links, a primary submit button, the Google sign-in option, and the link for creating the new account to make the form easily navigable and functional.

### Kelden Phuntsho Dorji's Journal 

While assembling the home page of RabsAuction, I learned about the necessary steps which contribute to the creation of an intuitive interface of an online auction site. Integrating React and Next. It made me able to manage the state of the application using hooks like useState when like when it came to interactions such as selecting the auction rooms and managing the visibility of the modal. By implementing the responsive design in the layout of the UI made it possible making the platform accessible in the different devices, increasing the usability factor. Further, utilizing TypeScript for type-checking ensured strength and precision when declaring the Room interface due to the conformity it offered across the application domain. Components like Modal made it easy to show extra pertinent information about certain rooms; it proved helpful for making the notion of the direct participation in certain auctions exclusive enough. In conclusion, what this project has shown is that when it comes to UI/UX design, state management, and matters of component reusability, the end goal of an online auctions application cannot be achieved flippantly.

### Kuenzang Rabten's Journal

During this phase of our project, we made good
ade good progress. We started by finishing our Figma designs and setting up our GitHub repository. I worked on designing the frontend welcome page, making changes to its layout and functionality. We had discussions with the team to plan our next steps once everyone had finished their tasks. A major achievement was connecting my welcome page with Tandin's login and signup features, making sure they worked with the backend endpoints and updating the frontend design as needed. Additionally, I worked on the UI designs using shadows on websockets and collaborated with Tenzin Namgay on the chatroom feature. By the end of this phase, I had finished the UI design and then tried linking the frontend with the backend.

### Tshering Phuntsho's Journal

In my final assignment for WEB101 and WEB102, I did the frontend part. Our group was task to develop an auction website. It was really interesting to do real time project and working with team members. Although we started the project with the little knowledge, now we learned lots of things after completing the project. I knew how to work collaboratively and what kind of challenges are faced which improved me for the upcoming projects and for the job market.

### Sonam Dorji Ghallay's Journal 

On the first day I started off with discussing the framework of our project and how to go about with the project and after that I started working on the backend with my members. There we firstly set up our server and the hono framework and prisma ORM. and we made a rough sketch of our database scheme  and after that we proceeded on making the schema for our database. 
After completion of the schema we consulted it with our tutor and made further changes to our schema. 
On the next day we started working on our endpoint for the with respect to our schema and there we faced of problem while making the endpoint because we applied protected routing and handling the jwt token was a bit difficult for us but our tutor again helped us with that
After completion of the endpoint we processed on the websocket for our chat room and were this the main issue with us because it was bit new to us but we completed that as well 
Finally connecting all the frontend, backend and websocket was the real deal because connecting all of them was a bit hard because we had little idea on connecting them and in this part was where we stuck the most but after the consultation from our tutor we we again able to complete it . 
However we were successfully able to complete this project with all the up and downs and from this I got experience on how to work in a group and mostly how to build a fully functional web page.

### Tenzin Namgay's Journal 

We focused on several important tasks. We started by discussing what needed to be added to the schema, with a particular focus on the auction room. We had multiple discussions on websockets, including a Zoom meeting with Douglas Sir to get a clearer understanding. I was able to make good progress coding the websocket. Tashi and I planned how to use JWT tokens for user IDs and room IDs. The entire backend team collaborated to connect the backend with the frontend, and we talked with Sir about how to obtain tokens. Kuenzang Rabten and I discussed the design of the chatroom for websockets and updated the code to include JWT tokens. Finally, we used Tashi's endpoint to get tokens needed to enter the chatroom and made a good progress.

### Kinley Palden's Journal

Integrating the interfaces for different parts of RabsAuction’s application helped me to consolidate important lessons about structuring and implementing coherent and effective frontends with React and Next. js. By the usage of reusables such as Button and Card classes, I was able to create and sustain the homogeneity of the design across the pages – Home, LoginPage, SignUpPage—, and the reduced code duplication. Using state hooks like useState for handling state locally was possible to control the form inputs on the go and at the same time, provide easy to comprehend feedback in case of errors. Substituting calls for common
operations such as login and registration illustrated the critical responsibility of API errors and responses when resulting in unreliable validation and, in turn, eroding user confidence. Responsive design fundamentals and client-side routing (Next.Link) maintained consistent and compatible device-agnostic user experience and made prompt improvements in the frontend web application development.

### Tashi Penjor's Journal

We focused on refining our database schema and made significant progress on the endpoints for uploading products. After thoroughly testing these endpoints, we handed them over to the frontend team. Additionally, we created endpoints for the auction room and passed them along to the frontend group. Tenzin Namgay and I discussed the websocket implementation with Douglas via Google Zoom for the server side. Since there was an issue with my auction endpoints assigning room IDs before creation, I re-edited and tested them before handing them to the frontend team. Tenzin Namgay, the other backend members, and I collaborated to resolve websocket issues highlighted during the Zoom meeting. We also worked together to connect the backend and frontend using the repository provided by Sir. Overall, our teamwork greatly improved the integration between the backend and frontend.

### Challeneges faced doing the project

Here are all the challenges we faced doing the project:

- Identifying the endpoints in the frontend design was difficult.
- Incubation WiFi was very slow, causing delays.
- Coding in the backend server was challenging, but Sir provided guidance.
- Difficulties in coding the workflow in schema, but Sir helped us.
- Facing many errors while using Shadcn, which was tough to work with.
- Had little difficulties with JWT tokens.
- Issues with user and product IDs took a lot of time to resolve.
- Most errors were related to Shadcn, including trouble positioning error messages.
- Unable to run the websocket server.
- Connecting ideas among team members was challenging at times.
- Coding took longer than expected, especially connecting registration with the backend.
- Not knowing how to connect frontend and backend.
- Difficulties with getting tokens for userID and roomID.
- Port problems.
- Could not merge the websocket server with the backend's server.
- Still faced difficulties in getting tokens and connecting some frontend parts.
- Hard to design based on the endpoints.
- Connecting frontend components resulted in many errors.
- Problem with one-to-one communication.
- Difficulties in connecting the websocket backend with Kunzang Rabten's frontend.
- Had a hard time understanding how to use Tailwind CSS.
- Integrating websocket into the main project was challenging.

### Conclusions

Throughout our project journey, we encountered several challenges that tested our problem-solving skills and teamwork. From grappling with slow WiFi and coding complexities in both frontend and backend servers, to navigating issues with Shadcn and JWT tokens, each obstacle provided valuable learning opportunities. Despite these difficulties, collaboration and guidance from our mentor played a crucial role in overcoming hurdles related to endpoint identification, websocket integration, and design implementation. While some tasks took longer than anticipated and required extensive troubleshooting, our persistence and collective effort led to significant improvements in connecting frontend components and resolving server-side issues. These challenges underscored the importance of adaptability and communication in achieving our goal of creating a functional auction website, preparing us well for future projects and endeavors in web development.