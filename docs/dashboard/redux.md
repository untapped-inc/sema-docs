disqus: sema-docs

The report client application uses React Redux to save the results of SEMA REST API requests to the Redux store. Components that need the various model properties then bind to those properties.

The flow of a user interaction that results in new data being fetched from the SEMA service followed by a component update is shown below.

The example illustrates the flow after a user selects a different kiosk/site while the application is displaying the Water Operations content.

![SEMA Redux Diagram][sema-redux-diagram]

[sema-redux-diagram]: ../assets/images/sema-redux-diagram.png