![SEMA Architecture Diagram][sema-architecture-diagram]

<!-- Images are referenced from here -->
[sema-architecture-diagram]: assets/images/sema-architecture-diagram.png

In a nutshell, the clients communicate with the REST API to gather and send data **from** and **to** the database.

Here are the technologies currently being used by each of the components that make up SEMA:

- The **back office** web client: Reactjs
- The **POS** mobile client: React Native
- The **REST API**: Nodejs and Expressjs
- The **Database**: MySQL

The POS mobile client works offline first.