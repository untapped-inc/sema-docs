disqus: sema-docs

# The Dashboard Client

The report client application is a React Browser application. It displays various metrics related to water production, sales and customer demographics.

The report client uses MVC pattern, the model is maintained in a Redux store, the views are implemented using React Components and the Sema REST services are used to load the Model Store

A picture of the report client is shown below:

![Report Client Home][report-client-home]

## Components

The report_client 
application consists of three main 'panes', the navigation pane, the 
toolbar pane and the main content pane. The React root component **App** initializes the application and presents either a login page, **SemaLogin,** (if a user login is required), or **SemaContainer** component which hosts, **SemaSidebar**, **SemaToolbar** and **SemaMain**, ( the navigation pane, toolbar pane and main content pane content respectively)

## Navigation Pane, (SemaSidebar)

This React component controls the content of the main view. It also contains a vendor specific logo at the top.

## Toolbar Pane (SemaToolbar)

This
 react component contains, (in left to right order); The version 
information of the client application, a 'Site/Kiosk' selector, a Date 
'filter' selector, the name of the logged in user, a logout button and 
the version of the Sema service.

When the application first starts, the user must first select a Site/Kiosk in order to populate the main content

## Main Pane (SemaMain)

This contains the routing information for the various 'content' components. The root components for each content page are

**SemaWaterOperations** - The root component for "Water Operations"

**SemaSales** - The root component for "Sales"

**SemaVolume** - The root component for "Volumes"

**SemaCustomer** - The root component for customer "Demographics"

The sections that follow describe these root components in more detail

<!-- Images are referenced from here -->
[report-client-home]: ../assets/images/report_client_home.png