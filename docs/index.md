# SEMA <small>Introduction</small>

The System for Emerging Market Analytics is an IT platform designed for Safe Water Enterprises (SWE) across all sectors and regions.

See the <a href="http://semawater.org" target="_blank">official home page</a> for more info.

[Click here](getting-started.md) to quickly get started.

!!! warning "Under Construction"
    This documentation currently goes under frequent updates. If you notice any missing part, it's probably being rewritten or updated at the moment.

## What is a Safe Water Enterprise?

For those who just want to contribute to the codebase, you may want to know the impact of your contributions, so here's a quick background:

A Safe Water Enterprise (SWE) is a sustainable solution to supply rural and peri-urban communities with safe drinking water. The concept combines a low-cost and low-maintenance membrane-based water treatment technology with an entrepreneurial approach for the sustainable management of the utility.

SWEs are designed to meet the urgent need for access to safe water globally as well as to provide water related health knowledge through trainings and social marketing.

Through their community based social enterprise approach, the SWEs are designed to provide a long-term sustainable solution at the kiosk level.

Here's, for example, the organizational structure (at the time of writing) of dloHaiti, which is an SWE in Haiti:

- An HQ team that analyzises the kiosks data, makes decisions based on this data and provides support to kiosk staffs
- For each kiosk, a kiosk staff which comprises of at least 2 operators and 1 driver (for deliveries)

There's more to it, but we keep it simple here.

Now, SEMA aims to digitize the procedures that make up this structure and help SWEs scale faster with accurate and on-demand data by providing a set of useful tools through a mobile POS app (used by the kiosk operators) and a back office web app (used by the HQ team).

You may want to do more research to get more accustomed to the users of the components that make up SEMA.

## Features

Here's what's included in SEMA:

- A mobile POS - React Native - (Only Android **for now**) that allows to:
    - Browse and pick products
    - Manage customers
    - Manage inventory
    - Process and manage (with limited actions) sales
    - Process and manage loans
    - Do all the above offline
- A back office on the web - Reacjs - that allows to:
    - Make administrative actions:
        - Manage Products
        - Manage Users/Employees
    - View Water Operations Reports
    - View Sales Reports
    - View Demographics Data
    - View Volume Reports
- An API server - Nodejs/Expressjs - that acts as an intermediate between all the clients and the database

See the [Architecture and Components](architecture-and-components-overview.md) section for more.

<!-- ## Join our Community Chat!

!!! note ""
    This documentation will not be complete without a community and we strongly urge you to join us over at Gitter - you can use your Github account to login - for any questions and suggestions that you may have:

    <a href="https://gitter.im/sema-dev/" target="_blank"><img src="https://badges.gitter.im/untapped-inc/sema-core.png"></a>

    **You will be able to instantly chat with our core team for anything you need about SEMA.** -->

## How is this doc structured?

This technical documentation was designed to be easily browsable. Here's what to expect:

- On the left side, you will find the listing of each main section.
- In the middle resides the content of the current section. In the top right corner of every content, you'll notice a pencil icon that links directly to the source code of the current content so you can edit the content and make a pull request so you can contribute to it.
- On the right side, there is a table of contents that lists sub-sections of the current section.
- In the top right, you can search throughout the whole documentation and also get basic information about our main repository from Github. You can also click on the link to visit it.
- Right before the footer, at the end of each page, you can easily go to the previous or the next section.
- Most sections have their own <a href="https://disqus.com" target="_blank">Disqus</a> comment[^about-comments] sub-section at the end where developers and people who read the docs can ask questions about the section.
- Each sub-section has the paragraph symbol `¶` link at the end of its headline - when you hover your cursor over it - that makes it possible to directly link to that sub-section.
- Some pages on the navigation menu have sub-pages and they are listed in a dropdown list. Some sub-pages even have their own sub-pages.
- This whole documentation site is responsive, it'll look good and browsable on both desktop and mobile devices.

And that's it. We hope you enjoy browsing around this doc as much as we enjoyed writing it. Feel free to leave a comment on a section if you see anything wrong or if something is not clear enough. Our core developers will get back to you shortly and this will definitely help others who come after.

[^about-comments]: Comments go under moderation before they are made public because we don't like spammers.