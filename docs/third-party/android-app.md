# Android application

## Introduction

This is a cross platform application. This application allow to list and handle tickets and computers.

## List of pages

* Home page : default page which contains Ticketing report (group by status / late / latest 24h) in a bar chart and Computer report (group by status) in a pie chart.
* Ticket page : display the list of tickets 
* Computer page: display the list of computers
* Add tciket : page to create a new ticket
* Add computer : page to create a new computer
* Ticket detail : give more information about a ticket
* Computer detail : give more information about a computer
* Configuration: this page is used to set the ITSM-NG configuration (URL / App token / User token)

## Application features

* Reporting 
    * Ticketing
        * Ticket per status (New, Assigned, Planned, Pending)
        * Late ticket
        * Latest 24h ticket
    * Computer
        * Computer per status

* List of ticket
    * Display all tickets
    * Let to change the default field (Name, Status, Open date) 
    * Sort by Name or by the second field
    * Filter by status
    * Search a ticket
    * Add a new ticket

* List of computer
    * Display all computer
    * Let to change the default field (Name, Status, Open date) 
    * Sort by Name or by the second field
    * Filter by status
    * Search a computer
    * Add a new computer

* Ticket detail
    * Give more information about a ticket (Title / Priority / Entity / Location / Assigned etc...)
    * Allow to delete or modify the ticket
    * List of the associated Followup and Task
    * Add new Followup and Task for the current ticket

* Computer detail
    * Give more information about a computer (Name / Update source / Serial / Location / Assigned etc...)
    * Allow to delete or modify the computer
    * List of the associated Ticket
    * Add new Fticket associated to the current computer

* Configuration    
    * Change the ITSM-NG configuration

* Language
    * The default language depends on the device language
    * Allow the change the language

* Logout
    * kill the session and redirect to the authentification page

## Configurations

### ITSM-NG configuration


To use the application, you should configure the API feature of your ITSM-NG.

Go to `Setup > General > API`, and enable the `Rest API`.

To allow a user to connect to the API, there are two options but currently our application is setting up to to use the second option:

* `Enable login with credentials` : allows the user to connect through the couple login and password separated by `:` in a Base64 string.
* `Enbale login with external token` : allows the user to connect through the `API token` configure directly in the user page configuration.

`Note: we recommend to only enable the login with external token for more security.`

![](../img/android-app/android-app_api_configuration.png)

Next, you need to configure an `API client` to allow the application to issue API calls to your ITSM-NG.

Click on `Add API client`.

Set a `name`, `Active` to `YES`, an `IPv4  address range` if you want to limit access to specific clients and check `Regenerate` for `Application token`.

Click on `Add`.

Then, go to the configuration page of the user who will be authorized to connect via the API and check `Regenerate` for the `API token`.

![](../img/android-app/android-app_api_user.png)

Click on `Save`.


### Application configuration

Run the application  and fill the form with `URL` , `API token` and `User token`

![](../img/android-app/android-app_authentification.png)

Click on `Send`.

## Somes samples

![](../img/android-app/android-app_example.png)


## Error handling

* Make a alert if ticket or computer data are empty
* In the form control the empty field and an incorrect parameter
* Generate a time out if connexion is not established
