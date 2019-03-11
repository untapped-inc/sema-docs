![SEMA Architecture Diagram][sema-architecture-diagram]

<!-- Images are referenced from here -->
[sema-architecture-diagram]: assets/images/sema-architecture-diagram.png

In a nutshell, the clients communicate with the REST API to gather and send data to the database.

Here are the technologies being used by each of them:

- The web **back office** client: Reactjs
- The **POS** mobile client: React Native
- The **REST API**: Nodejs and Expressjs
- The **Database**: MySQL

The POS mobile client works offline first.