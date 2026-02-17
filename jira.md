# Jira
This file contains an explanation of the schema used for Jira issues.  It should be useful when connecting to Jira to run queries or inspect work items.
## URL
The root URL for Jira is https://payzilch.atlassian.net/
## Projects
Projects (also now known as Spaces) of interest are:
### Zilch
Using the slug 'ZILCH', this is the main project.  All of my teams' work items are in this project.  Use a `project = Zilch` filter in JQL queries.
### Engineering Changes
Using the slug 'EC', this is a project for tracking changes to production systems.  My involvement tends to be to approve changes.
## Fields
### Team
Jira issues have three team fields, two of which are unused.  The team field to pay attention to is the dropdown field, `Team[Dropdown]`.  Work items for my teams can be identified with the following filters:
* DevOps Team: `Team[Dropdown] = "DevOps Team"`.
* Merchant Team: `Team[Dropdown] = "Merchant Team"`.
### Story Points
I use the `Story Points` field for sizing estimates.  The field allows null values, and I specify that issues should have a null value at some states in the workflow to make a distinction between an item that has not been estimated from one that has an intentional estimate of zero points.  Be aware that the Jira API does not serve null values for this field.  So if you encounter a zero, it may reflect and actual value of zero or a null value.