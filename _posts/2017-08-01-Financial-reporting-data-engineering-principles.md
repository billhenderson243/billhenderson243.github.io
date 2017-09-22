---
layout: post
title: "Financial Reporting data engineering principles"
date: 2017-08-01
---
Financial reporting is a critical function for almost every organization. A small number of documents must accurately represent a financial picture of that organization. Over the last twenty years Perkins Consulting has worked on financial reporting with clients of all sizes and industries. We believe that by following a core set of principles in storing and structuring data for financial reporting our clients will have quicker and more automated reporting processes. An additional objective of this paper is to outline an approach that is independent of any particular reporting or analytical tool and provides the best possible support for a wide range of software tools. We’ll be following up with an additional post around specific techniques for implementing these principles.

THE CHALLENGE
We’ve seen systems of linked spreadsheets that comprise hundreds of spreadsheet files with hundreds of megabytes of data that support financial reporting. Often these systems have grown organically over a period of many years and there is no longer any one person who understands the complete scope of the financial reporting system. These systems have few underlying design principles or architecture so it can be difficult for new hires to develop an understanding of how they work.

Although it would seem obvious that organizations should perform financial reporting using the built-in capabilities of their Enterprise Resource Planning (ERP) software – we’ve found that this is the exception rather than the rule. Some of the reasons why the financial reporting capabilities are not used include:

The organization may need to consolidate financial data from multiple ERP systems.
The ERP system imposes limits on the structure of the Chart of Accounts (COA)
The financial reporting capabilities of the ERP system are evolving too slowly to meet changing financial reporting regulatory requirements.
The financial reporting toolset provided with the ERP system is too limiting. We see this particularly when the organization wants to have multiple variations or versions of various financial statements based on the same underlying data.
Financial reporting teams are still frequently doing their financial reporting from Excel because they feel that only Excel gives them sufficient flexibility in three key areas:

Format – the ability to control exactly how the information is formatted on the page. Being able to bold some things and italicize others.
Structure – managing how accounts or groups of accounts roll up to summary levels as well as creating very specific subsets of accounts.
Annotation – adding metadata (data about data) in the form of notes and comments is crucial to explaining the financial statements.
BEST PRACTICE PRINCIPLES
In order to address these issues we’ve come up with a small set of best practice principles that carry through all of our tips and techniques.

Data driven not code driven
Separate data from structure
Separate drivers from results
Transparency
Data driven not code driven
The benefit of being data driven is ease of maintenance and transparency. Here is a simple example. Think of an Excel spreadsheet that contains a formula like this:

=IF(A1<200,1,0)
This might be a simple formula to determine if an account number is an Asset account or not. If the account number is less than 200 it is an Asset account. This formula might be sprinkled liberally throughout a big complicated financial reporting spreadsheet. What if the organization changes the chart of accounts so that only accounts less than 180 are Assets?

This could be better handled in Excel by the use of VLOOKUPs. Then when the definition of an Asset account changes – you only have to modify the lookup table. Using a database to store the definitions of accounts makes this even simpler and more reusable than VLOOKUPs.

Often financial reporting involves not just coding accounts for rollups or summarization but also encoding accounts that should appear together even if they are not summarized.
For example, a given GL account might:

Rollup to Inventory
Rollup to Current Assets
Be included on one departmental balance sheet but not another.
Think about the maintenance headache if you have hundreds of accounts – each with several such rules. Capturing the rules as reusable data will really help!

Separate data from structure
Separating data from structure provides similar benefits in maintenance, flexibility and ease of understanding. By storing the balances or transaction amounts at their lowest level of grain (detail) and storing the structure of how those values roll up separately you simplify maintenance. Bringing in a new month’s worth of data is simple.

By storing the structure of the data separately from the data you also facilitate having multiple reporting structures available for the same data.

Transparency
For everyone to feel confident about financial data we need to allow anyone to see where the data came from and trace it through any transformations. This is a variation of the old teacher’s saying, “show your work!” This is also important if we want our meetings and discussions to focus on changing the business outcome rather than arguing about where the data came from.

Make Room for Change
It is also important to be transparent about change and to recognize that over time accounts will come and go, groupings and financial reporting formats will change and definitions of customers and products may get more complex. Rather than trying to anticipate all possible changes upfront we’ve found the best solution is to incorporate source control and change tracking on all financial reporting infrastructure components.