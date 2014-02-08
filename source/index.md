---
title: Baasbox API Reference

language_tabs:
  - shell: cURL
  - objective_c: iOS
  - java: Android

toc_footers:
 - <a href='#'></a>
 - <a href='http://github.com/tripit/slate'>Powered by Slate</a>
---

# Introduction

BaasBox is a complete solution to implement the back end of your applications.

You can access all section using the sidebar on the left. The
documentation explains:

*  the BaasBox features (server side)
   * how to install BaasBox
   *  how to use admin console and has a detailed section about the REST
      API that you can use
   *  REST API

*  the SDK features

   *  iOS SDK

For a complete list of changes and new features, see the [changelog](http://www.baasbox.com/baasbox-server-0-7-2-released)

The Getting Started section will allow you to have rapidly a first
result of what BaasBox can give you. Enjoy!

# Installation

**System Requirements**  [Java VM 6](http://java.com/en/download/) or above. BaasBox is compiled with
Java 1.6.

1. Download the latest version from [here](http://www.baasbox.com/download/), keep
   in mind that until the 1.0 version will be released, BaasBox is not
   production-ready and therefore subject to change. For Windows
   Platforms on the same page you will find the `start.tar.gz` file.
2. Unzip the `baasbox-x.x.zip` file wherever you want.
3. Only for Windows Platforms: unzip the `start.tar.gz` file and put the
   extracted start.bat in the same directory
4. Type:
   * `start.bat` (on Windows)
   * `./start` (on *nix) You might need to grant execution permissions via
   `chmod +x ./start`

BaasBox will start it will listen on port 9000. Visit [http://localhost:9000/](http://localhost:9000/)
with your preferred browser. If everything worked fine, the BaasBox logo
should appear. Now you can open the administrator console: [http://localhost:9000/console](http://localhost:9000/console )
For further details about the console, you can read [console](#console).
That’s all! BaasBox is ready to go and to serve your apps! To stop the server just halt (Ctrl-C) the shell script.


# General Overview

BaasBox is a server that makes available a set of functions for the
backend of mobile applications. All you need is a **Java Virtual Machine
1.6 or higher**. BaasBox already has everything you need
for it to work: an application server and a DB server. 
BaasBox was born to be simple to use and manage. To migrate a BaasBox instance from a
server to another, you just have to zip the database folder and copy it
in the server target folder. Moreover, it is ready to use without
changing the configuration parameters. You just have to
launch the command ``./start`` (or ``start.bat`` on Windows) and BaasBox will
run. Should you need it, you can apply customize configuration parameters. See the [hacking section](#hacking).

## Available Functions

Available functions are:

-  Administration console:

   -  A convenient web based administration console is provided, through
      which the administrator can manage several aspects of BaasBox

-  Content management:

   -  Definition of "objects collection (AKA documents)"
   -  Creation, modification and deletion of objects
   -  Granting and revoking reading/modification/cancellation
      authorization on single objects
   -  Queries that allow specifying selection and
      ordering criteria
   -  Management of "special" contents called Assets, which may be files of any kind, 
      to which you can associate arbitrary JSON data

-  Users management:

   -  Signup, Login, Logout, profiles management (private, public
      features and so on), forgotten password recovery, link and log-in
      through Facebook and Google+
   -  Roles management: administrators, registered users, back-office
      users, creation of new roles.

-  Push notifications:

   -  Push notifications for iOS and Android devices

-  DB management:

   -  Backup/restore and reset of the integrated database
   

## Applied Technology

BaasBox is written mostly in Java, with some code in [Scala](http://www.scala-lang.org/). It uses the [Play! framework](http://www.playframework.com/) and it incorporates the core of the [OrientDB database](http://www.orientechnologies.com/orientdb/). This will allow BaasBox to natively manage the relations between JSON objects and to link
objects and queries without using specific abstractions or having to simulate them on the applicative level. OrientDB was recently surveyed and entered Gartner's Magic Quadrant.


# Console

BaasBox has a web console that allows managing its behavior and performing administrative
tasks. The console is a responsive one-page web application that
performs REST calls to the BaasBox admin APIs. This guide will
illustrate the console for the version **0.7.3**  We suppose that
BaasBox is deployed on localhost with its default parameters. If you
deployed BaasBox in the correct way, you can open your browser and open
the welcome screen: ![Console image](images/Console_0.7.2/home_console.png)

## Login screen

When you are in the start view, the administrator console is reachable
at the /console path. 
![Login image](images/Console_0.7.2/login.png)
To login in the administrative area you must supply the administrator credentials and the Application Code.
By default these values are:

-  Username: admin
-  Password: admin
-  App Code: 1234567890

You can change these values at any time by follow the instructions shown
in the [hacking section](#hacking). By clicking on the question marks, the
fields will be filled with the default values. 

## Dashboard 

Once you logged in, you will see the main dashboard screen: 

![Dashboard image](images/Console_0.7.2/baasbox_0-7-2-console.png)

The web console is based on twitter bootstrap and on the [Charisma Template](https://github.com/usmanhalalit/charisma/) project. The
dashboard is split into several sections:

1.  BaasBox version number
2.  Quick link to the BaasBox site
3.  Main menu to access all the main sections of BaasBox
4.  A trace of where you are located
5.  Number of users and rapid access to the relative section
6.  Number of documents (objects) stored in the embedded database and
    rapid access to the relative section
7.  Quick link to the [download](http://www.baasbox.com/download/) of BaasBox site where you
    can find the latest version
8.  Number of collections, documents and total size in one window.
9.  Here you can see all latest news about BaasBox. These are feeds from
    the BaasBox site |News|
10. System window:

    -  Memory: you can find max allocable memory, current allocated
       memory and current used memory
    -  OS: you can find name, version, architecture and processors
       viewed by your OS
    -  Java: you can find version, vendor and class version of your JDK
    -  Database: you can find version with its path and data size

11. Access to a dialog window to change password or to logout

    -  Change password: Just insert old and new passwords, then confirm
       the new one
    -  Logout: just logout from the console. Remember that you can also
       logout from the left menu.

12. Feedback tab: from there you can send us a feedback about your
    experience with BaasBox
13. DB Management: you can create backup of your DB and import & export
14. Roles: you can view and create roles for users

NOTE: you can hide all tables/sections that have the up-arrow button on
the right.


## Console settings


By selecting the Settings option in the left menu you can access the
settings section. You can choose settings for applications, password
recovery, images and push notifications. Each record has the Edit button
that allows you to modify its action.

NOTE: the starred fields are mandatory.

## Database Management

The item **DB Management** allows you to perform some operations on the
database. 

![Dashboard image](images/Console_0.7.2/baasbox-db-management.png)

1. Restore a previously created backup file
2. Create a new backup
3. View the list of generated backups
4. Reinitialize the database at its initial state. It deletes all the
   database content.

To create a new backup, you have to click on the "Create a new
backup..." button. This operation is asynchronous. BaasBox will freeze
the database and it will stop responding to the clients. When the backup
is ready you will find it in the list. From that list you can download
it or delete it.

To restore a database you have to download a backup file locally, and
then use the restore feature.


## Users


By selecting the Users option on the menu you can access the users
section. 

![Users image](images/Console_0.7.2/users.png)


In this section you have the list of all users. A
single user has a name, a role (admin, anonymoususer, backofficeuser,
registereduser), a creation date, a status and actions. You also have a
search tool. If you want to create a new user, click on the New User
button and you will see this window:

![New user image](images/Console_0.7.2/create_new_user.png)

<aside class="notice">
	Starred fields are mandatory. After you have filled at least the mandatory fields, you have to save the changes.
</aside>



## Collections

By selecting the Collections option on the menu you can access the
collection administration page. Collections are a sort of buckets where
you can store objects, also known as "documents". 

![Collections](images/Console_0.7.2/collections.png)

In this section you have a list of all your collections and you can quickly
find them with the search tool. To create a new collection, click on the
New Collection button and insert its name, then save the changes.

![New collection](images/Console_0.7.2/create_new_collection.png)


## Documents


Documents are objects stored in the embedded NoSQL database ad grouped
in "Collections".

![Documents](images/Console_0.7.2/documents.png)

In this section you have the list of all
your documents, but you have to select an existing collection at first.
In fact you can see all the documents relative to a specific collection.
Of course you also have the search tool. 

![Documents table](images/Console_0.7.2/baasbox-documents-table.png)

Each document has a unique id, generated by the server once it is stored.
Data documents are stored and retrieved JSON format.

Documents are accessible only by the user that created them. APIs exist
to grant and revoke permissions to the single users or roles.


## Assets


Assets are special objects. They are public by default, but only
administrators can create or delete them. They can store arbitrary data
(in JSON format), or entire files. Each Asset can store a file and its
associated data. Assets do not have IDs generated by the server, but you
can, indeed you MUST, assign a unique name to them. You can subsequently
use these names to reference the assets.

![Assets](images/Console_0.7.2/assets.png)

In this section you have the detailed list of all your assets
with information fields like Icon, Name, Meta, Size, Type, Download and
Actions. Of course you also have the search tool. If you want to create
a new asset, click on the New Asset button and you will see the
following window: 

![New asset](images/Console_0.7.2/new_asset.png)

<aside class="notice">
	You have to fill at least the Name
	field and save the changes to create a new asset.
</aside>









# REST API

## General Remarks

These are the general notes about the REST API protocol used by BaasBox
and its JSON format.

### Request Headers

If not specified otherwise, all requests need some custom HTTP headers.
BaasBox, since the 0.57 version supports two authentication method: HTTP Basic Authentication, or via a
Session Token.

### Basic Authentication


It needs to provide the user’s credentials via the basic access authentication method. Username and
password must be combined into a string “username:password” and then
encoded using BASE64. The header must be in the form: 

``Authorization: Basic QWxhZGRpbjpvcGVuIHNlc2FtZQ==``

If the authentication fails, the
server replies with BAD REQUEST http error (code 400)

**X-BAASBOX-APPCODE**  This is the application code, by default this
is: ``1234567890``

## Session Token


To use this authentication method, the client have to call
the [Login](#login) API. The Server will provide a token to use in the
subsequent calls. All tokens will be invalidated if the server is stopped. To pass the session
token to the server, use the following header: 

``X-BB-SESSION: 0000-1111-2222-3333`` 

## The JSON response 

> A sample of a JSON response

```json 
{	
  "result": "ok|ko",
  "http_code": (200|201|204),
  "data": {  }
}
```

> An example of JSON error

```json
{
	"result": "error",
	"bb_code": "",
	"message": "a message explaining the problem in plain English",
	"resource": "the REST API called",
	"method": "the HTTP method used",
	"request_header": { the headers received by the server },
	"API_version": "...the BaasBox API version..."
}
```

Every response generated by BaasBox as a result of a REST call is a JSON
object. In case of error, the data returned are more detailed and are useful to
understand why the request was rejected. 


## Custom error codes


These are custom error codes specific to BaasBox

-  40001: You are attempting to update a database object with older
   data. Version is not the same
-  40101: Authentication info not valid or not provided. HINT: is your
   session expired?
-  50301: Push settings are not properly configured. HINT: go to
   administration console and check the settings
-  50302: The server cannot resolve the host name. HINT: check your
   internet connection 

## Pagination

> Example of paginated query

```shell
curl 'http://localhost:9000/users?page=0&recordsPerPage=1' \
	 -H X-BB-SESSION:f083f676-65d0-45bd-bfe5-e876ef3f659e
	
```

```objective_c
NSDictionary *parameters = @{kPageNumber : @0,
                           kPageSize : [NSNumber numberWithInteger:BAAPageLength]};
[BAAUser loadUsersWithParameters:parameters
                      completion:^(NSArray *users, NSError *error) {
                          
						  if (error == nil) {
                          	NSLog(@"users are %@", users);
					  	  } else {
							// deal with error
					      }
                          
                      }];
```

```java
Filter paginate = Filter.paging("user.name",0,20);
BaasUse.fetchAll(paginate,new BaasHandler<List<BaasUser>>() {
  @Override
  public void handle(BaasResult<List<BaasUser>> res) {
    if (res.isSuccess()) {
      for(BaasUser user:res.value()) {
        Log.d("LOG","User is: "+user);
      }
    } else {
      Log.e("LOG","error",res.error());
    }
  }
});
```

Some queries support pagination. There are two important parameters in paginated calls.

Parameter | Description
--------- | -----------
**page** | O indexed page number. Optional
**recordsPerPage** | Number of elements to be retrieved per page. Optional



## Query Criteria


Some APIs allow to specify query criteria. Accepted parameters are:

-  **where**: set a filter criteria in a SQL-like fashion (i.e.: ``“color=’yellow’ or address.city=’rome’”``). It is possible to use the positional mode, for example: ``“color=? or address.city=?”``. In this case you must supply the parameters’ values using the ``params`` querystring parameter.
-  **params**: an array of value for the where clause. For example:
   ``/API\_URL/WHERECLAUSE/&params=yellow&params=cyan``
-  **orderBy**: set an order by clause in a SQL-like fashion (i.e.:
   orderBy name desc). NOTE: the direction of ordering (asc or desc) is
   mandatory if pagination is used (see below)
-  **page**: a 0 based index indicating the page requested
-  **recordPerPage**: the number of records per page
-  **fields**: allow to specify a subset of fields (projections) to return instead of the entire record. It is also possibile to specify aggregate functions and execute all the operations allowed by OrientDB into the "select" statements. An exaustive list of available functions is available at https://github.com/orientechnologies/orientdb/wiki/SQL-Where#wiki-field-operators, meanwhile the explanation of how to specify projections is at https://github.com/orientechnologies/orientdb/wiki/SQL-Query#projections
-  **groupBy**: allow to indicate a "group by" criteria to group the result-set by one or more fields just like in standard SQL statements. This criteria is used in conjunction with the aggregate functions expressed into the "fields"

**Example of valid calls**:

* ``/document/mycollection/count?where=color%3D’yellow’``
* ``/document/mycollection/count?where=color%3D%3F&params%3dyellow``
* ``/document/documents/count?where=color%3D%3F%20or%20color%3D%3F&params=yellow&params=cyan``

<aside class="notice">
	The value of the parameter must be URL encoded.
</aside>


## Sign up

> Sample request to create a user

```shell
curl http://localhost:9000/user \
	-d '{"username" : "cesare", "password" : "password"}' \
	-H Content-type:application/json \
	-H X-BAASBOX-APPCODE:1234567890  
```

```objective_c
BAAClient *client = [BAAClient sharedClient];
[client createUserWithUsername:@"cesare"
                      password:@"password"
                    completion:^(BOOL success, NSError *error) {

                          if (success) {
                              NSLog(@"user is %@", client.currentUser);
                          } else {
                              // display error
                          }

 }];
```

```java
BaasUser user = BaasUser.withUserName("andrea");
user.setPassword("password");
user.signup(new BaasHandler<BaasUser>(){
  @Override
  public void handle(BaasResult<BaasUser> result){
    if(result.isSuccess()) {
      Log.d("LOG","Current user is: "+result.value());
    } else {
      Log.e("LOG","Show error",result.error());
    }
  }
});
```

> Sample response when a user is created

```json
{
  "result": "ok",
  "data": {
    "user": {
      "name": "cesare",
      "status": "ACTIVE",
      "roles": [
        {
          "name": "registered"
        }
      ]
    },
    "signUpDate": "2014-01-23 23:00:18",
    "X-BB-SESSION": "db7634df-1002-45a2-b2ab-0f6b8556a1fe"
  },
  "http_code": 201
}
```

``POST /user``

**Headers**: See authorization header in the [General Remarks](#general-remarks)

**Description**: This API allows a user to sign up to the App. Users will belong to the registered user role and
they will post new content, will retrieve their own content, will change their password. 

Parameter | Description
--------- | -----------
**username** | The username for the user. Mandatory
**password** | Password. Mandatory
**visibleByTheUser** | an object whose fields are private and  visible only by the user
**visibleByFriends** | an object whose fields are visible by the user and his/her friends (for future friendship management)
**visibleByRegisteredUsers** | is an object whose fields are visible by the user, his/her friends, any registered user
**visibleByAnonymousUsers** | an object whose fields are public and visible by everyone, even anonymous users



## Login

> Sample request to login 

```shell
curl http://localhost:9000/login \
	-d "username=cesare" \
	-d "password=password" \
	-d "appcode=1234567890"
```

```objective_c
BAAClient *client = [BAAClient sharedClient];
[client authenticateUser:@"user"
                password:@"password"
              completion:^(BOOL success, NSError *error) {
                  
			if (success) {
				NSLog(@"user is %@", client.currentUser);
			} else {
				// show error
			}
}];
```

```java
BaasUser user = BaasUser.withUserName("andrea");
user.setPassword("password");
user.login(new BaasHandler<BaasUser>() {
  @Override
  public void handle(BaasResult<BaasUser> result) {
    if(result.isSucces()) {
      Log.d("LOG", "The user is currently logged in: "+result.value());
    } else {
      Log.e("LOG","Show error",result.error());
    }
  }
});
```
> Sample response when a user is logged in

```json
{
  "result": "ok",
  "data": {
    "user": {
      "name": "cesare",
      "status": "ACTIVE",
      "roles": [
        {
          "name": "registered"
        }
      ]
    },
    "signUpDate": "2014-01-23 23:00:18",
    "X-BB-SESSION": "41b7ce0f-be44-4737-b346-907483155ad8"
  },
  "http_code": 200
}
```

``POST /login``

Checks username/password and grants the user the right to execute other calls. 
This API returns a session token (**X-BB-SESSION**) that must be provided into 
all authenticated calls.

Parameter | Description
--------- | -----------
**username** | The username for the user. Mandatory
**password** | Password. Mandatory
**appcode** | The appcode of your server instance


## Logout

> Example of logout call

```shell
curl -X POST http://localhost:9000/logout \
	-H X-BB-SESSION:da506029-4512-45a9-9606-43fcdda4121a
```

```objective_c
[BAAUser logoutWithCompletion:^(BOOL success, NSError *error) {
           
	if (success) {
	    // user logged out
	} else {
	    // error logging out
	}
            
}];
```

```java
BaasUser.current().logout(new BaasHandler<Void>() {
  @Override
  public void handle(BaasResult<Void> result) {
    if(result.isSuccess()) {
      Log.d("LOG", "Logged out: "+(BaasUser.current() == null));
    } else{
      Log.e("LOG","Show error",result.error());
    }
  };
});
```

> Sample response when a user logs out

```json
{
 "result":"ok",
 "data":"user logged out",
 "http_code":200
}
```

``POST /logout/:pushToken`` 

Allows a user to logout from the app on a specific device. Push notification will not be sent to the user through the specified device.

Parameter | Description
--------- | -----------
**pushToken** | Optional. The push notification token that you have used to activate push notifications.


## Logged user profile

> Request to fetch user profile currently logged in

```shell
curl http://localhost:9000/me \
	-H X-BB-SESSION:196f48ed-6154-4b49-8dc6-8b9b2ce4900a
```

```objective_c
[BAAUser loadCurrentUserWithCompletion:^(BAAUser *user, NSError *error) {
    
	if (error == nil) {
		// deal with user object
	} else {
		// deal with error
	}
		
}];
``` 

```java
BaasUser.current().refresh(new BaasHandler<BaasUser>() {
  @Override
  public void handle(BaasResult<BaasUser> result) {
    if(result.isSuccess()) {
      BaasUser user = result.value();
      JsonObject data = user.getScope(Scope.PRIVATE);
      Log.d("LOG","Log some private data: "+data);
    } else {
      Log.e("LOG","error:",result.error());
    }
  }
});
```
> Sample response 

```json
{
  "result": "ok",
  "data": {
    "user": {
      "name": "cesare",
      "status": "ACTIVE",
      "roles": [
        {
          "name": "registered"
        }
      ]
    },
    "signUpDate": "2014-01-24T11:28:09.009+0100"
  },
  "http_code": 200
}
```

``GET /me``

Retrieves details about the logged in user.







## Update user profile

> PUT request to update the logged in user profile

```shell
curl -X PUT http://localhost:9000/me \
	-d '{"visibleByFriends" : {"phoneNumber" : "+1123456"}}' \
	-H Content-type:application/json \
	-H X-BB-SESSION:a30e8f43-4d90-4324-91d2-6065fa6ca63c
```

```objective_c
TO BE IMPLEMENTED
```

```java
BaasUser user = BaasUser.current();
user.getScope(Scope.PRIVATE).putString("property","value");
user.save(new BaasHandler<BaasUser>() {
  @Override
  public void handle(BaasResult<BaasUser> res) {
    if(res.isSuccess()) {
      Log.d("LOG", "User data has been saved");
    } else {
      Log.e("LOG", error,res.error());
    }
  }
});
```


> Sample JSON response

```json
{
  "result": "ok",
  "data": {
    "user": {
      "name": "cesare",
      "status": "ACTIVE",
      "roles": [
        {
          "name": "registered"
        }
      ]
    },
    "signUpDate": "2014-01-24T11:28:09.009+0100",
    "visibleByFriends": {
      "phoneNumber": "+1123456"
    }
  },
  "http_code": 200
}
```

``PUT /me``

Updates details about the logged in user.

The body payload to send has the following form:

```{
    "visibleByTheUser": {},
    "visibleByFriend": {},
    "visibleByRegisteredUsers": {},
    "visibleByAnonymousUsers": {}
}```

All the four properties are optional. You can send just
one of them or all four. See example on the right.
The values for this fields can be anything you like: string, numbers, arrays
or JSON encoded objects.

Parameter | Description
--------- | -----------
**visibleByTheUser** | fields private and visible only by the user
**visibleByFriend** | fields are visible by the user and his friends
**visibleByRegisteredUsers** | fields are visible by the user, his friends and any registered user
**visibleByAnonymousUsers** | fields are public and visible by everyone, even anonymous users

<aside class="warning">
	The previously stored content for each of the four fields will be overwritten.
</aside>




## Change password

> Example of request

```shell
curl -X PUT http://localhost:9000/me/password \
	-d '{"old" : "password", "new" : "newpassword"}' \
	-H Content-type:application/json \
	-H X-BB-SESSION:a30e8f43-4d90-4324-91d2-6065fa6ca63c
```

```objective_c
TO BE IMPLEMENTED
```

```java
BaasUser current = BaasUser.current();
current.changePassword("newpassword",new BaasHandler<Void>() {
  public Void handle(BaasHandler<Void> res) {
    if(res.isSuccess()) {
      Log.d("LOG", "New password updated, you should relogin");
    } else {
      Log.e("LOG","error",res.error());
    }
  }
});
```
> Example of response

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```

``PUT /me/password`` 

To change the password of the logged in user.

Parameter | Description
--------- | -----------
**old** | The old password. Mandatory.
**new** | The new password. Mandatory.

<aside class="warning">
	After you call this API the authentication token is not valid anymore and should should call [Login](#login) again.
</aside>









## Follow a user

> Example of request to follow the user "cesare"

```shell
curl -X POST http://localhost:9000/follow/cesare \
	 -H X-BB-SESSION:c6fb7001-ccb5-4048-8935-80ef197e1390
```

```objective_c
BAAUser *user = ...; // Instance of user to be followed

[BAAUser followUser:user
         completion:^(BAAUser *user, NSError *error) {
             
             if (error == nil) {
                 NSLog(@"now following user %@", user);                 
             } else {
                 // deal with error             
             }
                          
         }];
```

```java
BaasUser user = BaasUser.withUsername("cesare");
user.follow(new BaasHandler<BaasUser>() {

  @Override
  public void handle(BaasResult<BaasUser> res) {
    if(res.isSuccess()) {
     JsonObject profile = res.value().getScope(Scope.FRIEND);
     Log.d("LOG", "It's profile "+profile);
    } else{
      // there was an error
    }
  } 
});
```
> Example response

```json
{
  "result": "ok",
  "data": {
    "user": {
      "name": "cesare",
      "roles": [
        {
          "name": "registered"
        },
        {
          "name": "friends_of_cesare"
        }
      ],
      "status": "ACTIVE"
    },
    "signUpDate": "2014-01-24T11:28:09.009+0100",
    "visibleByFriends": {
      "phoneNumber": "+1123456"
    }
  },
  "http_code": 201
}
```

``POST /follow/:username``

This API allows a user to follow another user. Once the relation is established
the follower will be able to see the documents and files created by the followed 
user as well as its `visibleByFriends` data in the user profile.

Parameter | Description
--------- | -----------
**username** | Username of the user to be followed. Mandatory.








## Unfollow a user

> Example of unfollow request

```shell
curl -X DELETE http://localhost:9000/follow/cesare \
 	 -H X-BB-SESSION:c6fb7001-ccb5-4048-8935-80ef197e1390
```

```objective_c
BAAUser *user = ...; // Instance of user to be unfollowed

[BAAUser unfollowUser:user
           completion:^(BAAUser *user, NSError *error) {
             
	             if (error == nil) {
	                 NSLog(@"not following anymore user %@", user);                 
	             } else {
	                 // deal with error             
	             }
                          
         }];
```

```java
BaasUser.withUserName("cesare").unfollow(
  new BaasHandler<BaasUser>() {
    @Override
    public void handle(BaasResult<BaasUser> res) {
      if(res.isSuccess()) {
        JsonObject data = res.value().getScope(Scope.FRIEND);
        Log.d("LOG", "No more friend data:"+(data==null));
      } else {
        // there was an error
      }
    }
  });
```
> Example of response

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```

``DELETE /follow/:username``

This API allows a user to unfollow another user. Once the relation has been deleted, the user 
won't be able anymore to see documents and files created by the unfollowed user.

Parameter | Description
--------- | -----------
**username** | Username of the user to be unfollowed. Mandatory.







## Fetch following

> Example of request to fetch who "cesare" is following

```shell
curl http://localhost:9000/following/cesare \
 	 -H X-BB-SESSION:c6fb7001-ccb5-4048-8935-80ef197e1390
```

```objective_c
BAAUser *user = ... // user representing "cesare"

[user loadFollowingWithCompletion:^(NSArray *following, NSError *error) {
                        
            for (BAAUser *u in following) {
                NSLog("cesare is following %@", u)
            }
            
        }];
```

```java
BaasUser user = ... // the user representing "cesare"

user.following(new BaasHandler<List<BaasUser>>() {
  @Override
  public void handle(BaasResult<List<BaasUser>> res) {
    if(res.isSuccess()){
      for(BaasUser u: res.value()) {
        Log.d("LOG","Cesare is follwing: "+u.getName());
      }
    }
  }
});
```

> Example of response

```json
{
  "result": "ok",
  "data": [
    {
      "user": {
        "roles": [
          {
            "name": "registered"
          }
        ],
        "name": "a",
        "status": "ACTIVE"
      },
      "signUpDate": "2014-01-24T12:13:08.008+0100"
    }
  ],
  "http_code": 200
}
```

``GET /following/:username``

This API returns a list of users that are followed by the user with `username` passed as parameter. The method returns in its `data` property an array filled with the user profiles representing its “friends”. Each profile will contain the `visibleByFriends` data which would be otherwise hidden.

Parameter | Description
--------- | -----------
**username** | Username of the user whose following list has to be fetched. Mandatory.








## Fetch followers

> Example of request to fetch who "cesare"'s followers

```shell
curl http://localhost:9000/followers/cesare \
	 -H X-BB-SESSION:c6fb7001-ccb5-4048-8935-80ef197e1390
```

```objective_c
BAAUser *user = ... // user representing "cesare"

[user loadFollowersWithCompletion:^(NSArray *following, NSError *error) {
                        
            for (BAAUser *u in following) {
                NSLog("%@ is following cesare", u)
            }
            
        }];
```

```java
BaasUser user = ... // the user representing "cesare"

user.followers(new BaasHandler<List<BaasUser>>() {
  @Override
  public void handle(BaasResult<List<BaasUser>> res) {
    if(res.isSuccess()){
      for(BaasUser u: res.value()) {
        Log.d("LOG", u.getName()+ " is following cesare");
      }
    }
  }
});
```


> Example of response with "cesare"'s followers


```json
{
  "result": "ok",
  "data": [
    {
      "user": {
        "roles": [
          {
            "name": "registered"
          }
        ],
        "name": "a",
        "status": "ACTIVE"
      },
      "signUpDate": "2014-01-24T12:13:08.008+0100"
    }
  ],
  "http_code": 200
}
```

``GET /followers/:username``

This API returns the list of followers for the user with `username` specified in the parameter. The method returns in its `data` property an array filled with the user profiles representing its “friends”. Each profile will contain the `visibleByFriends` data which would be otherwise protected. 

Parameter | Description
--------- | -----------
**username** | Username of the user whose followers list has to be fetched. Mandatory.



## Password reset

> Example of request for password reset

```shell
curl http://localhost:9000/user/cesare/password/reset \
	 -H X-BAASBOX-APPCODE:1234567890
```

```objective_c
TO BE IMPLEMENTED
```

```java
BaasUser.requestPasswordReset("cesare",new BaasHandler<Void>() {
  @Override
  public void handle(BaasResult<Void> res) {
    if(res.isSuccess()) {
      Log.d("LOG","Password reset has been requested");
    } else{
      Log.e("LOG","Error",res.error());
    }
  }
};
```

> Example of error

```json
{
  "result": "error",
  "message": "Cannot reset password, the \"email\" attribute is not defined into the user's private profile",
  "resource": "/user/cesare/password/reset",
  "method": "GET",
  "request_header": {
    "Accept": [
      "*/*"
    ],
    "Host": [
      "localhost:9000"
    ],
    "X-BAASBOX-APPCODE": [
      "1234567890"
    ]
  },
  "API_version": "0.7.3-snapshot"
}
```


``GET /user/:username/password/reset``

Allows to reset a user password. This API is useful when a user forgot their password and needs to reset it. This is the workflow: 

- the server checks if the email address is present within the `visibleByTheUser` fields in the user profile 
- the server sends an email to that address with a generated link to follow to reset the password 
- the user opens the email and opens the given link in a web browser. That shows a form with two html password fields. 
- The user fills in the two fields and submits the form 
- A confirmation message is shown by the server 
- The settings (SMTP configuration, email message to be sent, html form, confirmation and error web page) can be setup by the administrator via the [Settings](#settings) menu in the admin console.

Parameter | Description
--------- | -----------
**username** | Username of the user who wants to reset the password. Mandatory.

<aside class="warning">
This API works only if there is an `email` field (populated with a valid email address) in the `visibleByTheUser` field of the user profile
</aside>


## Fetch a user profile

> example of request to get a user profile

```shell
curl http://localhost:9000/user/a \
	 -H X-BB-SESSION:f083f676-65d0-45bd-bfe5-e876ef3f659e
```

```objective_c
[BAAUser loadUserDetails:@"a"
              completion:^(BAAUser *user, NSError *error) {
    
    if (error == nil) {
    
        NSLog(@"user details are %@", user);
        
    } else {
    
        // deal with error
        
    }
    
}];
```

```java
BaasUser.fetch("a",new BaasHandler<BaasUser>() {
  @Override
  public void handle(BaasResult<BaasUser> res) {
    if(res.isSuccess()){
      BaasUser user = res.value();
      Log.d("LOG","The user: "+user);
    } else {
      Log.e("LOG","Error",res.error());
    }
  }
});
```

> Example of response

```json
{
  "result": "ok",
  "data": {
    "user": {
      "name": "a",
      "status": "ACTIVE",
	  "visibleByFriends": {"phoneNumber":"+1985478562"}},
      "roles": [
        {
          "name": "registered"
        }
      ]
    },
    "signUpDate": "2014-01-24T12:13:08.008+0100"
  }
```



``GET /user/:username``

Allows to retrieve information about a user profile.

Parameter | Description
--------- | -----------
**username** | Username of the user. Mandatory.






## Fetch users

> example of request to get a list users

```shell
curl http://localhost:9000/users \
	 -H X-BB-SESSION:f083f676-65d0-45bd-bfe5-e876ef3f659e
```

```objective_c
NSDictionary *parameters = @{kPageNumber : @0,
                           kPageSize : [NSNumber numberWithInteger:BAAPageLength]};
[BAAUser loadUsersWithParameters:parameters
                      completion:^(NSArray *users, NSError *error) {
                          
						  if (error == nil) {
                          	NSLog(@"users are %@", users);
					  	  } else {
							// deal with error
					      }
                          
                      }];
```

```java
BaasUser.fetchAll(new BaasHandler<List<BaasUser>>() {
  @Override
  public void handle(BaasResult<List<BaasUser>> res) {
    if(res.isSuccess()) {
      for(BaasUser u: res.value()) {
        Log.d("LOG", "The user is: "+u.getName());
      }
    } else {
      Log.e("LOG","error");
    }
  }
});
```

> Example of response

```json
{
  "result": "ok",
  "data": [
    {
      "user": {
        "roles": [
          {
            "name": "registered"
          }
        ],
        "name": "cesare",
        "status": "ACTIVE"
      },
      "signUpDate": "2014-01-24T11:28:09.009+0100",
      "visibleByTheUser": {
        "email": "cesare@email.com"
      },
      "visibleByFriends": {
        "phoneNumber": "+1123456"
      }
    },
    {
      "user": {
        "roles": [
          {
            "name": "registered"
          }
        ],
        "name": "e",
        "status": "ACTIVE"
      },
      "signUpDate": "2014-01-24T12:10:37.037+0100"
    }
  ],
  "http_code": 200
}
```

``GET /users``

Allows to retrieve a list of users. This API supports [pagination](#pagination) and [query criteria](#query-criteria).




## Collections

A collection is a sort of bucket where you can store documents. Documents are schema-less, which means that there are no constraints on their fields definition or data type.
Another very important feature to know about collections is that the records stored have a per-user-record-security-level, meaning that each record can be accessed only by the user who created it. There are APIs to grant or revoke privileges to other users. TODO link


## Create a new Collection

> Example of request to create a collection

```shell
curl -X POST http://localhost:9000/admin/collection/mycollection \
	 -H X-BB-SESSION:53331bd8-3dbb-40af-8bcb-252ac908f142
```

```objective_c
TO BE IMPLEMENTED
```

```java
TO DO
```

> Example of response

```json
{
  "result": "ok",
  "data": "",
  "http_code": 201
}
```

``POST /admin/collection/:collection-name``

Creates a new collection. The user calling this API must be admin or belong to the admin role.

Parameter | Description
--------- | -----------
**collection-name** | The name of the new collection. Mandatory.




## Delete a Collection

> Example of request to delete a collection

```shell
curl -X DELETE http://localhost:9000/admin/collection/mycollection \
	 -H X-BB-SESSION:53331bd8-3dbb-40af-8bcb-252ac908f142
```

```objective_c
NOT SUPPORTED
```

```java
TODO
```

> Example of response

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```

`DELETE /admin/collection/:collection-name`

Deletes an existing collection with the name specified in the URL. The user calling this API must be admin or belong to the admin role.

Parameter | Description
--------- | -----------
**collection-name** | The name of the collection to be deleted. Mandatory.

<aside class="warning">
	The deletion of a collection deletes all the objects belonging to that. 
</aside>



## Documents

A document belongs to a [Collection](#collections34). You can create, read, update and delete a document, provided you have access to it.
Here are the APIs.

## Create a document

> Example of request to create a document.

```shell
curl -X POST http://localhost:9000/document/mycollection \
	 -d '{"title" : "My new post title", "body" : "Body of my post."}' \
	 -H Content-type:application/json \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
// Assumes post is an instance of Post, which subclasses BAAObject with properties "title" and "body".
Post *post = [[Post alloc] init];
post.title = @"My new post title";
post.body = @"Body of my post.";
[post saveObjectWithCompletion:^(Post *p, NSError *error) {
    
    if (error == nil) {
        NSLog(@"saved post is %@", p)
    } else {
        // deal with error
    }
    
}];
```

```java
BaasDocument doc = new BaasDocument("mycollection");
doc.putString("title","My new post title")
   .putString("body","Body of my post.");
doc.save(new BaasHandler<BaasDocument>() {
  @Override
  public void handle(BaasResult<BaasDocument> res) {
    if(res.isSuccess()) {
      Log.d("LOG","Saved: "+res.value());
    } else {

    }
  }
});
```

> Example of response

```json
{
  "result": "ok",
  "data": {
    "@rid": "#25:0",
    "@version": 2,
    "@class": "mycollection",
    "title": "My new post title",
    "body": "Body of my post.",
    "id": "090dd688-2e9a-4dee-9afa-aad72a1efa93",
    "_creation_date": "2014-01-30T21:13:16.016+0100",
    "_author": "cesare"
  },
  "http_code": 200
}
```

`POST /document/:collection-name`

Creates a document in the collection specified in the parameter. The collection must have been created in advance. See [here](#create-a-new-collection).
The `id` field is unique. By default only the owner can update and delete the documents he created. All the other users (except admins) cannot have any kind of access to those documents.

Parameter | Description
--------- | -----------
**collection-name** | The name of the collection. Mandatory.
 | A valid JSON as the body of the POST call. Mandatory.








## Retrieve a document

> Example of request to retrieve a specific document

```shell
curl http://localhost:9000/document/mycollection/090dd688-2e9a-4dee-9afa-aad72a1efa93 \
 	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
// Assuming Post is a subclass of BAAObject
[Post getObjectWithId:@"090dd688-2e9a-4dee-9afa-aad72a1efa93"
           completion:^(Post *post, NSError *error) {
               
               if (error == nil) {
                   NSLog(@"Post is %@", post);
               } else {
                   // deal with error
               }
               
           }];
```

```java
```

> Example of response

```json
{
  "result": "ok",
  "data": {
    "@rid": "#25:0",
    "@version": 2,
    "@class": "mycollection",
    "title": "My new post title",
    "body": "Body of my post.",
    "id": "090dd688-2e9a-4dee-9afa-aad72a1efa93",
    "_creation_date": "2014-01-30T21:13:16.016+0100",
    "_author": "cesare"
  },
  "http_code": 200
}
```


`GET /document/:collection/:ID`

Retrieves the document in the collection specified with the ID provided as parameter. 
Only the owner of the document (besides his friends and users with admin role) can retrieve it.

Parameter | Description
--------- | -----------
**collection** | The name of the collection. Mandatory.
**ID** | The unique ID of the document. Mandatory.




## Modify a document

> Example of request to modify a document.

```shell
curl -X PUT http://localhost:9000/document/mycollection/090dd688-2e9a-4dee-9afa-aad72a1efa93 \
	 -d '{"title" : "My new post title", "body" : "New body of post.", "tags" : "tag1"}' \
	 -H Content-type:application/json \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
// Assumes post is an instance of Post, which subclasses BAAObject with properties "title", "body" and "tags".
Post *post = [[Post alloc] init];
post.title = @"My new post title";
post.tags = @"tag1"
post.body = @"Body of my post.";
[post saveObjectWithCompletion:^(Post *p, NSError *error) {
    
    if (error == nil) {
        NSLog(@"saved post is %@", p)
    } else {
        // deal with error
    }
    
}];
```

```java
BaasDocument.fetch("mycollection",
                   "090dd688-2e9a-4dee-9afa-aad72a1efa93",
               new BaasHandler<BaasDocument>() {
                 @Override
                 public void handler(BaasResult<BaasDocument> res) {
                   if(res.isSuccess()) {
                     BaasDocument doc = res.value();
                     Log.d("LOG","Document: "+doc);
                   } else {
                     Log.e("LOG","error",res.error());
                   }
                 }});
```

> Example of response

```json
{
  "result": "ok",
  "data": {
    "@rid": "#25:0",
    "@version": 3,
    "@class": "mycollection",
    "title": "My new post title",
    "body": "New body of post.",
    "tags": "tag1",
    "id": "090dd688-2e9a-4dee-9afa-aad72a1efa93",
    "_creation_date": "2014-01-30T21:13:16.016+0100",
    "_author": "cesare"
  },
  "http_code": 200
}
```

`PUT /document/:collection/:ID`

Updates the document with the ID provided in the specified collection. 
Only the owner of the document (besides the admin and backoffice users), can call this API.

Parameter | Description
--------- | -----------
**collection** | The name of the collection. Mandatory.
**ID** | The unique ID of the document. Mandatory.
  | A valid JSON as the body of the PUT. 


<aside class="warning">
	The document is fully replaced with the new content. 
</aside>



## Delete a document

> Example of request to delete a document

```shell
curl -X DELETE http://localhost:9000/document/mycollection/090dd688-2e9a-4dee-9afa-aad72a1efa93 \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
// Assumes post is an instance of Post, which subclasses BAAObject 
[post deleteObjectWithCompletion:^(BOOL success, NSError *error) {
    
    if (success) {
        NSLog(@"object deleted");
    } else {
        // deal with error
    }
    
}];
```

```java
// Assumes doc is an instance of BaasDocument
doc.delete(new BaasHandler<Void>() {
  @Override
  public void handle(BaasResult<Void> res) {
    if (res.isSuccess()) {
      Log.d("LOG", "Document deleted");
    } else {
      Log.e("LOG", "error",res.error());
    }
  }
});
```
> Example of response

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```

`DELETE /document/:collection/:ID`

Deletes the document with the ID specified in the collection provided as parameter. Only the owner of the document (besides the admin or backoffice users) can delete it.

Parameter | Description
--------- | -----------
**collection** | The name of the collection. Mandatory.
**ID** | The unique ID of the document. Mandatory.



## Count documents

> Example of request to count documents in a collection

```shell
curl http://localhost:9000/document/mycollection/count \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
NOT IMPLEMENTED
```

```java
BaasDocument.count("collection",new BaasHandler<Long> () {
  @Override
  public void handle(BaasResult<Long> res) {
    if (res.isSuccess()) {
      Log.d("LOG","visible document count is: "+res.value());
    } else {
      Log.e("LOG","Error",res.value());
    }
  }
});
```
> Example of response

```json
{
  "result": "ok",
  "data": {
    "count": 1
  },
  "http_code": 200
}
```

`GET /document/:collection/count`

Returns the number of documents that the **user can red** in a collection. 

Parameter | Description
--------- | -----------
**collection** | The name of the collection. Mandatory.

<aside class="notice">
	A collection could contain documents that the user cannot read and therefore are not included in the count.
</aside>







## Retrieve documents 

> Example of request to retrieve a list of documents using default pagination

```shell
curl http://localhost:9000/document/mycollection \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
	
// Version with pagination
curl 'http://localhost:9000/document/mycollection?page=0&recordsPerPage=1' \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
// Assumes Post as a subclass of BAAObject
[Post getObjectsWithCompletion:^(NSArray *posts, NSError *error) {
    
    if (error == nil) {
        NSLog(@"Posts are %@", posts);
    } else {
        // deal with error
    }
    
}];

// Version with pagination
NSDictionary *parameters = @{kPageNumber : @0,
                             kPageSize : @20};
[Post getObjectsWithParams:parameters
                completion:^(NSArray *posts, NSError *error) {

                    if (error == nil) {
                        NSLog(@"Posts are %@", posts);
                    } else {
                        // deal with error
                    }

                }];
```

```java
BaasDocument.fetchAll(new BaasHandler<List<BaasDocument>() {
  @Override
  public void handle(BaasResult<List<BaasDocument>> res) {
    
    if (res.isSuccess()) {
      for (BaasDocument doc:res.value()) {
        Log.d("LOG","Doc: "+doc);
      }
    } else {
      Log.e("LOG","Error",res.error());
    }
  }
});

// using pagination and selection
Filter filter = Filter.paging("title",0,20)
                      .setWhere("_author = ?","Cesare");

BaasDocument.fetchAll(filter,new BaasHandler<List<BaasDocument>() {
  @Override
  public void handle(BaasResult<List<BaasDocument>> res) {
    
    if (res.isSuccess()) {
      for (BaasDocument doc:res.value()) {
        Log.d("LOG","Doc: "+doc);
      }
    } else {
      Log.e("LOG","Error",res.error());
    }
  }
});

```

> Example of response

```json
{
  "result": "ok",
  "data": [
    {
      "@rid": "#25:1",
      "@version": 5,
      "@class": "mycollection",
      "title": "My new post title",
      "body": "Body of my post.",
      "id": "af1d66fe-c8b6-436f-866b-e4c823ae7666",
      "_creation_date": "2014-01-30T22:22:36.036+0100",
      "_author": "cesare"
    },
	{
      "@rid": "#26:1",
      "@version": 5,
      "@class": "mycollection",
      "title": "My second post title",
      "body": "Body of my second post.",
      "id": "af1236fe-c8bs-4r6f-866b-e4cnkutd8636",
      "_creation_date": "2014-01-30T22:22:38.031+0100",
      "_author": "cesare"
    }
  ],
  "http_code": 200
}
```

`GET /document/:collection`

Returns the documents that the **user can read** in a collection. This API supports [pagination](#pagination)

Parameter | Description
--------- | -----------
**collection** | The name of the collection. Mandatory.

<aside class="notice">
	A collection could contain documents that the user cannot read and therefore are not included in the result.
</aside>
















## Grant permissions on a Document

> Example of request to grant read access to user "a" on document "090dd688"

```shell
curl -X PUT http://localhost:9000/document/mycollection/090dd688/read/user/a \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
NOT YET IMPLEMENTED
```

```java
// assuming doc is an instance of the document
doc.grant(Grant.READ,"a",new BaasHandler<Void>() {
  @Override
  public void handle(BaasResult<Void> res) {
    if (res.isSuccess()) {
      Log.d("LOG","Permission granted");
    } else {
      Log.e("LOG","Error",res.error());
    }
  }
});
```


> Example of request to grant update access to all registered users on a document

```shell
curl -X PUT http://localhost:9000/document/mycollection/090dd688/update/role/registered \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
NOT YET IMPLEMENTED
```

```java
// assumes doc is an instance of the document
doc.grantAll(Grant.UPDATE,Role.REGISTERED,
   new BaasHandler<Void>() {
     @Override
     public void handle(BaasResult<Void> res) {
       if (res.isSuccess()) {
         Log.d("LOG","Permission granted");
       } else {
         Log.e("LOG","Error",res.error());
       }
     }
   });
```

> Example of response

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```

`PUT /document/:collection/:id/:action/user/:username`

`PUT /document/:collection/:id/:action/role/:rolename`

Grants permission on a document. You can set permissions for a single user or a role name.

Parameter | Description
--------- | -----------
**collection** | The name of the collection. Mandatory.
**id** | The ID of the document. Mandatory.
**action** | The grant you want to assign. One of: 	`read`, `update`, `delete`, `all`. Mandatory.
**username** | The username of the user to which you want to assign the grant
**rolename** | The name of role to which you want to grant the permission. One of: `anonymous`, `registered`, `administrator`









## Revoke permissions on a Document


> Example of request to revoke read access to user "a" on document "090dd688"

```shell
curl -X DELETE http://localhost:9000/document/mycollection/090dd688/read/user/a \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
NOT YET IMPLEMENTED
```

```java
// assuming doc is an instance of the document
doc.revoke(Grant.READ,"a",new BaasHandler<Void>() {
  @Override
  public void handle(BaasResult<Void> res) {
    if (res.isSuccess()) {
      Log.d("LOG","Permission granted");
    } else {
      Log.e("LOG","Error",res.error());
    }
  }
});
```


> Example of request to revoke update access to all registered users on a document

```shell
curl -X PUT http://localhost:9000/document/mycollection/090dd688/update/role/registered \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
NOT YET IMPLEMENTED
```

```java
// assumes doc is an instance of the document
doc.revokeAll(Grant.UPDATE,Role.REGISTERED,
   new BaasHandler<Void>() {
     @Override
     public void handle(BaasResult<Void> res) {
       if (res.isSuccess()) {
         Log.d("LOG","Permission granted");
       } else {
         Log.e("LOG","Error",res.error());
       }
     }
   });
```

> Example of response

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```

`DELETE /document/:collection/:id/:action/user/:username`

`DELETE /document/:collection/:id/:action/role/:rolename`

Revokes permission on a document. You can revoke permissions to a single user or a role name.

Parameter | Description
--------- | -----------
**collection** | The name of the collection. Mandatory.
**id** | The ID of the document. Mandatory.
**action** | The grant you want to assign. One of: 	`read`, `update`, `delete`, `all`. Mandatory.
**username** | The username of the user to which you want to assign the grant
**rolename** | The name of role to which you want to grant the permission. One of: `anonymous`, `registered`, `administrator`






## Update a Document's field

> Example of a request to change the value of the field 'title'

```shell
curl -X PUT http://localhost:9000/document/mycollection/af1d66fe-c8b6-436f-866b-e4c823ae7666/.title  \
	 -d '{"data" : "Updated title"}' \
	 -H Content-type:application/json \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
NOT IMPLEMENTED
```

```java
NOT IMPLEMENTED
```

> Example of response

```json
{
  "result": "ok",
  "data": {
    "@rid": "#25:1",
    "@version": 6,
    "@class": "mycollection",
    "title": "Updated title",
    "body": "Body of my post.",
    "id": "af1d66fe-c8b6-436f-866b-e4c823ae7666",
    "_creation_date": "2014-01-30T22:22:36.036+0100",
    "_author": "cesare"
  },
  "http_code": 200
}
```

> Example of a request to add a new value named 'tags'

```shell
curl -X PUT http://localhost:9000/document/mycollection/af1d66fe-c8b6-436f-866b-e4c823ae7666/.tags  \
	 -d '{"data" : ["tag1", "tag2"]}' \
	 -H Content-type:application/json \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
NOT IMPLEMENTED
```

```java
NOT IMPLEMENTED
```

> Example of response

```json
{
  "result": "ok",
  "data": {
    "@rid": "#25:1",
    "@version": 7,
    "@class": "mycollection",
    "title": "Updated title",
    "body": "Body of my post.",
    "id": "af1d66fe-c8b6-436f-866b-e4c823ae7666",
    "_creation_date": "2014-01-30T22:22:36.036+0100",
    "_author": "cesare",
    "tags": [
      "tag1",
      "tag2"
    ]
  },
  "http_code": 200
}
```

> Example of a request to add a new value to the 'tags' array property

```shell
curl -X PUT http://localhost:9000/document/mycollection/af1d66fe-c8b6-436f-866b-e4c823ae7666/.tags[3]  \
	--globoff \
	 -d '{"data" : "newly added tag"}' \
	 -H Content-type:application/json \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
NOT IMPLEMENTED
```

```java
NOT IMPLEMENTED
```

> Example of response

```json
{
  "result": "ok",
  "data": {
    "@rid": "#25:1",
    "@version": 10,
    "@class": "mycollection",
    "title": "Updated title",
    "body": "Body of my post.",
    "id": "af1d66fe-c8b6-436f-866b-e4c823ae7666",
    "_creation_date": "2014-01-30T22:22:36.036+0100",
    "_author": "cesare",
    "tags": [
      "tag1",
      "tag2",
      "newly added tag"
    ]
  },
  "http_code": 200
}
```

> Example of a request to add a JSON object as a property.

```shell
curl -X PUT http://localhost:9000/document/mycollection/af1d66fe-c8b6-436f-866b-e4c823ae7666/.address  \
	--globoff \
	 -d '{"data" : {"street" : "5th Avenue", "zip" : 10021}}' \
	 -H Content-type:application/json \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
NOT IMPLEMENTED
```

```java
NOT IMPLEMENTED
```

> Response includes new property

```json
{
  "result": "ok",
  "data": {
    "@rid": "#25:1",
    "@version": 15,
    "@class": "mycollection",
    "title": "Updated title",
    "body": "Body of my post.",
    "id": "af1d66fe-c8b6-436f-866b-e4c823ae7666",
    "_creation_date": "2014-01-30T22:22:36.036+0100",
    "_author": "cesare",
    "tags": [
      "tag1",
      "tag2",
      "newly added tag"
    ],
    "address": {
      "zip": 10021,
      "street": "5th Avenue"
    }
  },
  "http_code": 200
}
```

> Example of request to change a nested property

```shell
curl -X PUT http://localhost:9000/document/mycollection/af1d66fe-c8b6-436f-866b-e4c823ae7666/.address/.street  \
	--globoff \
	 -d '{"data" : "6th Avenue"}' \
	 -H Content-type:application/json \
	 -H X-BB-SESSION:4cbfe03c-632b-4d3e-9a2b-0d4a0326d89e
```

```objective_c
NOT IMPLEMENTED
```

```java
NOT IMPLEMENTED
```

> Response includes new value for the property

```json
{
  "result": "ok",
  "data": {
    "@rid": "#25:1",
    "@version": 15,
    "@class": "mycollection",
    "title": "Updated title",
    "body": "Body of my post.",
    "id": "af1d66fe-c8b6-436f-866b-e4c823ae7666",
    "_creation_date": "2014-01-30T22:22:36.036+0100",
    "_author": "cesare",
    "tags": [
      "tag1",
      "tag2",
      "newly added tag"
    ],
    "address": {
      "zip": 10021,
      "street": "6th Avenue"
    }
  },
  "http_code": 200
}
```


`PUT /document/:collection/:id/.:fieldname`

Updates a single field of an existing object. The field can be a simple property, 
a complex JSON object or even an array using the notation `.array[index]` .

Parameter | Description
--------- | -----------
**collection** | The name of the collection. Mandatory.
**id** | The ID of the document. Mandatory.
**fieldname** | The name of the field that you want to update
**data** | A JSON object in the body of the PUT. The new value must have a key named `data`.

<aside class="warning">
The fieldName must start with a .
</aside>


## Files

Users can upload files. Only the user who created it, besides administrators and users who have the role of “BackOffice” can access such file. 
The maximum size of a file is 2GB, but we do not recommend reaching such size, since BaasBox is software that provides backend services for mobile Apps. Currently we do not support resume functions for upload and download.







## Create a file

> Example of request to create a file

```shell
curl -X POST http://localhost:9000/file \
	 -F file=@test.jpg \
	 -H X-BB-SESSION:9952384d-8d78-4399-82d0-7039f832a786
```

```objective_c
NSData *data = ...; // data for file
BAAFile *file = [[BAAFile alloc] initWithData:data];
file.contentType = @"image/jpeg";
[file uploadFileWithCompletion:^(BAAFile *uploadedFile, NSError *error) { 
	
	if (error == nil) {
		NSLog(@"Uploaded file is %@", uploadedFile)
	} else {
		// Deal with error
	}
	
}];
```

```java
InputStream data = ...; // input stream to upload
BaasFile file = new BaasFile();

file.upload(data,new BaasHandler<BaasFile> file) {
  @Override
  public void handle(BaasResult<BaasFile> res) {
    if( res.isSuccess() ) {
      Log.d("LOG","File uploaded with permissions");
    } else {
      Log.e("LOG","Deal with error",res.error());
    }
  }
}
```

> Example of response when a file is created

```json
{
  "result": "ok",
  "data": {
    "@version": 2,
    "_creation_date": "2014-02-03T18:54:17.017+0100",
    "id": "be81f25d-c954-498e-84a2-6f43a94a9d8f",
    "_author": "cesare",
    "fileName": "test.jpg",
    "contentType": "image/jpeg",
    "contentLength": 283808,
    "metadata": { },
    "attachedData": { }     
  },
  "http_code": 201
}
```

> Example of request to create a file with attached data

```shell
curl -X POST http://localhost:9000/file \
	 -F 'attachedData={"test_key":"test_value"}' \
	 -F file=@test.jpg \
	 -H X-BB-SESSION:9952384d-8d78-4399-82d0-7039f832a786
```

```objective_c
TO BE IMPLEMENTED 
```

```java
byte[] data = ...; // in memory data to upload
JsonObject attachedData = new JsonObject()
                              .putString("someInfo","value);

BaasFile file = new BaasFile(attachedData);

file.upload(data,new BaasHandler<BaasFile> file) {
  @Override
  public void handle(BaasResult<BaasFile> res) {
    if( res.isSuccess() ) {
      Log.d("LOG","File uploaded with permissions");
    } else {
      Log.e("LOG","Deal with error",res.error());
    }
  }
}
```

> Example of request to create a file with attached data and acl

```shell
curl -X POST http://localhost:9000/file \
	 -F '"attachedData"={"test_key":"test_value"}' \
	 -F '"acl"={"read":{"roles":["registered"]}' \
	 -F file=@test.jpg \
	 -H X-BB-SESSION:9952384d-8d78-4399-82d0-7039f832a786
```

```objective_c
TO BE IMPLEMENTED 
```

```java
InputStream data = ...; // input stream to upload
JsonObject attachedData = new JsonObject();
attachedData.putString("key","value")
            .putString("num",1);
BaasFile file = new BaasFile(attachedData);
BaasACL acl = new BaasACL().grantUsers(Grant.READ,"andrea");

file.upload(acl,data,new BaasHandler<BaasFile> file) {
  @Override
  public void handle(BaasResult<BaasFile> res) {
    if( res.isSuccess() ) {
      Log.d("LOG","File uploaded with permissions");
    } else {
      Log.e("LOG","Deal with error",res.error());
    }
  }
}
```

`POST /file`

API to create and upload a file. By default the uploaded file will be accessible only by the owner, backoffice and admin users.

Parameter | Description
--------- | -----------
**file** | The file itself. Mandatory.
**attachedData** | A valid JSON string to store data associated to a file. Optional.
**acl** | A valid JSON string to declare access to the file. Optional. TODO: link to ACL


<aside class="notice">
	The metadata field of the JSON response may vary according to the type of file uploaded.
</aside>


## Delete a file

> Example of request to delete a file

```shell
curl -X DELETE http://localhost:9000/file/a57b33ce-7f4d-4ff7-bf8c-f8c0f973b9d8 \
	 -H X-BB-SESSION:9952384d-8d78-4399-82d0-7039f832a786
```

```objective_c
BAAFile *picture = ...; // instance or subclass of BAAFile
[picture deleteFileWithCompletion:^(BOOL success, NSError *error) {
   
    if (success) {
        NSLog(@"Pic deleted");
    } else {
		// Deal with error
	}
	
}
    
}];
```

```java
BaasFile file = ...; // a file reference
file.delete(new BaasHandler<Void>() {
  @Override
  public void handle(BaasResult<Void> res) {
    if( res.isSuccess() ) {
      Log.d("LOG","File has been downloaded");
    } else {
      Log.e("LOG","Deal with error",res.error());
    }
  }
});
```

> Example of response when a file is deleted

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```

`DELETE /file/:id`

API to delete a file. 

Parameter | Description
--------- | -----------
**id** | The id of the file to be deleted. Mandatory.






## Retrieve a file

> Example of request to retrieve a file.

```shell
curl http://localhost:9000/file/f18e4343-5100-4398-b32f-2e634220bf99 \
	 -H X-BB-SESSION:9952384d-8d78-4399-82d0-7039f832a786
```

```objective_c
BAAFile *picture = ...; // instance or subclass of BAAFile, previously saved on the server
[picture loadFileWithCompletion:^(NSData *data, NSError *error) {
    
    self.imageView.image = [[UIImage alloc] initWithData:data];
    
}];
```

```java
BaasFile file = ...;
file.stream(new BaasHandler<BaasFile>() {
  @Override
  public void handle(BaasResult<BaasFile> res) {
    if ( res.isSuccess() ) {
      Log.d("LOG","File received");  
    } else {
      Log.e("LOG","Error while streaming",res.error());
    }
  }
});
```

> Example of response

```json
// Binary of the file
```

> Example of request to suggest the browser to download an app

```shell
curl http://localhost:9000/file/f18e4343-5100-4398-b32f-2e634220bf99 \
	 -H X-BB-SESSION:9952384d-8d78-4399-82d0-7039f832a786?download=true
```

> Example of request to retrieve a resized version of an app. TODO: explain this

```shell
curl http://localhost:9000/file/f18e4343-5100-4398-b32f-2e634220bf99 \
	 -H X-BB-SESSION:9952384d-8d78-4399-82d0-7039f832a786?sizeId=0
```

`GET /file/:id`

Parameter | Description
--------- | -----------
**id** | The id of the file to be retrieved. Mandatory.
**download** | Set it to `true` to download a file (useful from browser). Optional. 
**resize** | Index to retrieve an element from the array of resize options. Optional TODO: explain




## Retrieve details of a file

> Example of request to retrieve details of a file

```shell
curl http://localhost:9000/file/details/f18e4343-5100-4398-b32f-2e634220bf99  \
	 -H X-BB-SESSION:9952384d-8d78-4399-82d0-7039f832a786
```

```objective_c
[BAAFile loadFileDetails:p.fileId
              completion:^(BAAFile *file, NSError *error) {
                  
                  if (error == nil) {
                      NSLog(@"file %@", file);
                  } else {
                      // Deal with error
                  }
                  
              }];
```

```java
BaasFile.fetch(fileId, new BaasHandler<BaasFile> () {
  @Override
  public void handle(BaasResult<BaasFile> res) {
    if (res.isSuccess()) {
      Log.d("LOG","Your file details"+res);
    } else {
      Log.e("LOG","Deal with eror",res.error());
    }
  }
});
```

> Example of response with file details

```json
{
  "result": "ok",
  "data": {
    "@version": 6,
    "id": "f18e4343-5100-4398-b32f-2e634220bf99",
    "_creation_date": "2014-02-03T23:41:59.059+0100",
    "_author": "cesare",
    "fileName": "test.jpg",
    "contentType": "image/jpeg",
    "contentLength": 283808,
    "metadata": { },
    "attachedData": { }
  },
  "http_code": 200
}
```

`GET /file/details/:id`

Retrieves the details of a file, including `attachedData` and `metadata`.


Parameter | Description
--------- | -----------
**id** | The id of the file whose details are to be retrieved. Mandatory.




## Retrieve details of files

> Example of request to retrieve details of files

```shell
curl http://localhost:9000/file/details \
	 -H X-BB-SESSION:45640ea7-f57f-4ade-b781-4aebc0c364b6
```

```objective_c
TO BE IMPLEMENTED
```

```java
BaasFile.fetchAll(new BaasHandler<List<BaasFile>>() {
  @Override
  public void handle(BaasResult<List<BaasFile>> res) {
    if (res.isSuccess()) {
      Log.d("LOG","Received result");
    } else {
      Log.e("LOG","Error",res.error());
    }
  }
});
```

> Example of response with details of files

```json
{
  "result": "ok",
  "data": [
    {
      "@version": 4,
      "id": "338ad9e6-1a70-4483-bd46-9764be05def4",
      "_creation_date": "2014-02-04T00:50:13.013+0100",
      "_author": "a",
      "fileName": "41EAE238-0E8F-491D-BA34-C7BFB4EFF595.image/jpeg",
      "contentType": "image/jpeg",
      "contentLength": 75642,
      "metadata": { },
      "attachedData": { }
    },
	{  }
  ],
  "http_code": 200
}
```

`GET /file/details`

Returns a list of details about the files that the user has access to.
Supports [pagination](#pagination).




## Grant access to a file

> Example of request to grant read access to user “a” on a file

```shell
curl -X PUT http://localhost:9000/file/41368ee4/read/user/a \
     -H X-BB-SESSION:b24fa187-797d-49d1-87fb-c99fee3a6588
```

```objective_c
BAAFile *file = ... ; // instance of file, already saved on the server
[file grantAccessToUser:@"a"
                 ofType:kAclReadPermission
             completion:^(id object, NSError *error) {
                 
                 if (error == nil) {
                     NSLog(@"Permission granted");
                 } else {
                     // Deal with error
                 }
                 
             }];
```

```java
BaasFile file=...; // reference to a file already saved on the server
file.grant(Grant.READ,"andrea",new BaasHandler<Void>(){
  @Override
  public void handle(BaasResult<Void> res){
    if (res.isSuccess()) { 
      Log.d("LOG","andrea can read the file");
    } else {
      Log.e("LOG","deal with error",res.error());
    }
  }
});
```

> Example of request to grant write access to role “registered” on a file

```shell
curl -X PUT http://localhost:9000/file/41368ee4/update/role/registered \
     -H X-BB-SESSION:b24fa187-797d-49d1-87fb-c99fee3a6588
```

```objective_c
BAAFile *file = ... ; // instance of file, already saved on the server
[file grantAccessToRole:kAclRegisteredRole
                 ofType:kAclUpdatePermission
             completion:^(id object, NSError *error) {
                 
                 if (error == nil) {
                     // Permission granted
                 } else {
                     // Deal with error
                 }
                 
             }];
```

```java
BaasFile file=...; // reference to a file already saved on the server
file.grantAll(Grant.READ,"registered",new BaasHandler<Void>(){
  @Override
  public void handle(BaasResult<Void> res){
    if (res.isSuccess()) { 
      Log.d("LOG","andrea can read the file");
    } else {
      Log.e("LOG","deal with error",res.error());
    }
  }
});

```

> Example of response 

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```


`PUT /file/:id/:action/user/:username` 

`PUT /file/:id/:action/role/:rolename`

API to grant access on a file to a specific user or role.

Parameter | Description
--------- | -----------
**id** | The ID of the file. Mandatory.
**action** | The grant you want to assign. One of: 	`read`, `update`, `delete`, `all`. Mandatory.
**username** | The username of the user to which you want to assign the grant. Mandatory.
**rolename** | The name of role to which you want to grant the permission. One of: `anonymous`, `registered`, `administrator`. Mandatory.







## Revoke access to a file

> Example of request to revoke read access to user “a” on a file

```shell
curl -X DELETE http://localhost:9000/file/41368ee4/read/user/a \
     -H X-BB-SESSION:b24fa187-797d-49d1-87fb-c99fee3a6588
```

```objective_c
BAAFile *file = ... ; // instance of file, already saved on the server
[file revokeAccessToUser:@"a"
                  ofType:kAclReadPermission
              completion:^(id object, NSError *error) {
                  
                  if (error == nil) {
                      NSLog(@"Permission revoked");
                  } else {
                      // Deal with error
                  }
                  
              }];
```

```java
BaasFile file=...; // reference to a file already saved on the server
file.revoke(Grant.READ,"andrea",new BaasHandler<Void>(){
  @Override
  public void handle(BaasResult<Void> res){
    if (res.isSuccess()) { 
      Log.d("LOG","andrea can read the file");
    } else {
      Log.e("LOG","deal with error",res.error());
    }
  }
});

```

> Example of request to revoke write access to role “registered” on a file

```shell
curl -X DELETE http://localhost:9000/file/41368ee4/update/role/registered \
     -H X-BB-SESSION:b24fa187-797d-49d1-87fb-c99fee3a6588
```

```objective_c
BAAFile *file = ... ; // instance of file, already saved on the server
[file revokeAccessToRole:kAclRegisteredRole
                  ofType:kAclUpdatePermission
              completion:^(id object, NSError *error) {
                  
                  if (error == nil) {
                      NSLog(@"Permission revoked");
                  } else {
                      // Deal with error
                  }
                  
              }];
```

```java
BaasFile file=...; // reference to a file already saved on the server
file.revokeAll(Grant.READ,"registered",new BaasHandler<Void>(){
  @Override
  public void handle(BaasResult<Void> res){
    if (res.isSuccess()) { 
      Log.d("LOG","andrea can read the file");
    } else {
      Log.e("LOG","deal with error",res.error());
    }
  }
});

```

> Example of response 

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```


`DELETE /file/:id/:action/user/:username or DELETE /file/:id/:action/role/:rolename`

API to revoke access on a file to a specific user or role.

Parameter | Description
--------- | -----------
**id** | The ID of the file. Mandatory.
**action** | The grant you want to revoke. One of: 	`read`, `update`, `delete`, `all`. Mandatory.
**username** | The username of the user to which you want to revoke the grant. Mandatory.
**rolename** | The name of role to which you want to revoke the permission. One of: `anonymous`, `registered`, `administrator`. Mandatory.



## Assets

Assets can be either files or JSON objects. **They are public and accessible by anyone**, even if not authenticated. 
They are useful to create publicly accessible elements such as images or configuration settings. 

## Create an asset

> Example of request to create a JSON asset.

```shell
curl http://localhost:9000/admin/asset \
	 -d 'name=margherita&meta={"pizzaname": "Margherita", "price": 5}' \
	 -H X-BB-SESSION:f24c0ccb-e2bd-4741-8133-86fea6ea1e01
```

```objective_c
TO BE IMPLEMENTED
```

```java
TODO
```

> Example of response 

```json
{
  "result": "ok",
  "data": {
    "@rid": "#19:3",
    "@version": 18,
    "@class": "_BB_Asset",
    "_creation_date": "2014-02-08T10:52:51.051+0100",
    "id": "98510f1c-a558-4901-9550-71e8add0a6c2",
    "_author": "admin",
    "name": "margherita",
    "meta": {
      "pizzaname": "Margherita",
      "price": 5
    }
  },
  "http_code": 201
}
```

> Example of request to create a file asset with JSON metadata attached.

```shell
curl http://localhost:9000/admin/asset \
	 --form file=@pizza.jpg \
	 --form name=margherita \
	 --form meta='{"name": "Margherita", "price": 5}' \
	 -H X-BB-SESSION:f24c0ccb-e2bd-4741-8133-86fea6ea1e01
```

```objective_c
TO BE IMPLEMENTED
```

```java
TODO
```

> Example of response 

```json
{
  "result": "ok",
  "data": {
    "@rid": "#20:0",
    "@version": 16,
    "@class": "_BB_FileAsset",
    "_creation_date": "2014-02-08T11:04:15.015+0100",
    "id": "00cced22-680d-45d4-944e-28ac9a140572",
    "_author": "admin",
    "name": "margherita",
    "fileName": "pizza.jpg",
    "contentType": "image/jpeg",
    "contentLength": 975404,
    "meta": {
      "name": "Margherita",
      "price": 5
    }
  },
  "http_code": 201
}
```

`POST /admin/asset`

Parameter | Description
--------- | -----------
**name** | The name of the asset. Must be unique. Mandatory. 
**meta** | A string representing a valid JSON object. Here you can store any data associated with the asset. Optional.
**file** | The file you want to upload. Optional.

Allows to create an asset.

<aside class="notice">
	The `name` field must be unique. An error will be returned if an asset with the same name has already been uploaded.
	
	Only a user with an admin role can create an asset.
</aside>








## Retrieve an Asset

> Example of request to retrieve an asset.

```shell
curl http://localhost:9000/asset/margherita \
	 -H X-BAASBOX-APPCODE:1234567890
```

```objective_c
TO BE IMPLEMENTED
```

```java
TODO
```

> Example of response

```json
The file itself.
```

`GET /asset/:name`

To retrieve an asset by name. 

Parameter | Description
--------- | -----------
**name** | The name of the asset. Mandatory.




## Delete an asset

> Example of request to delete an asset

```shell
curl -X DELETE http://localhost:9000/admin/asset/margherita  \
	 -H X-BB-SESSION:f24c0ccb-e2bd-4741-8133-86fea6ea1e01
```

```objective_c
TO BE IMPLEMENTED
```

```java
TODO
```

> Example of response

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```

`DELETE /admin/asset/:name`

Allows to delete an asset.

Parameter | Description
--------- | -----------
**name** | The name of the asset. Mandatory.

<aside class="notice">	
	Only a user with an admin role can delete an asset.
</aside>





## Fetch assets

> Example of request to fetch assets

```shell
curl http://localhost:9000/admin/asset  \
	 -H X-BB-SESSION:f24c0ccb-e2bd-4741-8133-86fea6ea1e01
```

```objective_c
TO BE IMPLEMENTED
```

```java
TODO
```

> Example of response

```json
{
  "result": "ok",
  "data": [
    {
      "@rid": "#19:7",
      "@version": 18,
      "@class": "_BB_Asset",
      "_creation_date": "2014-02-08T11:54:09.009+0100",
      "id": "63db6a92-5e74-4bbe-aeff-982eaba10d3e",
      "_author": "admin",
      "name": "margherita",
      "meta": {
        "pizzaname": "Margherita",
        "price": 5
      }
    },
    {
      "@rid": "#19:8",
      "@version": 27,
      "@class": "_BB_Asset",
      "_creation_date": "2014-02-08T11:56:20.020+0100",
      "id": "591c583c-dd78-4ba1-acab-331b9559b8fd",
      "_author": "admin",
      "name": "marinara",
      "meta": {
        "pizzaname": "Marinara",
        "price": 4
      }
    }
  ],
  "http_code": 200
}
```

`GET /admin/asset` 

Allows to retrieve all the assets. Supports [pagination](#pagination).

<aside class="notice">	
	Only a user with an admin role can call this API.
</aside>



## Settings

Settings are app related configuration options. They are intended to set up many app specific parameters, like the app name, the push notification certificate supplied by Apple, and so on. Settings are split in different sections or topics.

* PasswordRecovery: this section contains many settings that affect the password recovery workflow
* Application: Application specific parameters, such as the App Name
* Push: Push notifications related settings
* Images: specific settings for images (Assets file) processing


<aside class="notice">	
	Only users belonging to administrator roles can call these APIs.
</aside>

## Fetch current settings

```shell
curl http://localhost:9000/admin/configuration/dump.json  \
	 -H X-BB-SESSION:4efcd048-8865-4047-94c9-8ac58e511b4b \
	 -H X-BAASBOX-APPCODE:1234567890
```

```objective_c
TO BE IMPLEMENTED
```

```java
TODO
```

> Example of response

```json
{
  "result": "ok",
  "data": [
    {
      "section": "PasswordRecovery",
      "description": "Configurations for password recovery related properties",
      "sub sections": {
        "email": [
          {
            "email.template.text": "Hi ...",
            "type": "String"
          }

        ],
        "network": [ ]
      }
    },
    {
      "section": "Application",
      "description": "Configurations for general App(lication) related properties",
      "sub sections": { }
    },
    {
      "section": "Push",
      "description": "Configurations for push related properties",
      "sub sections": { }
    },
    {
      "section": "Images",
      "description": "Configurations for Images related stuffs",
      "sub sections": { }
    },
    {
      "section": "Social",
      "description": "Configurations for Social Login related stuffs",
      "sub sections": { }
    }
  ],
  "http_code": 200
}
```

`GET /admin/configuration/dump.json`

Returns a JSON representing the current configuration.


## Fetch a section of the Settings

> Example of request to retrieve the `Application` section

```shell
curl http://localhost:9000/admin/configuration/Application  \
	 -H X-BB-SESSION:4efcd048-8865-4047-94c9-8ac58e511b4b \
	 -H X-BAASBOX-APPCODE:1234567890
```

```objective_c
TO BE IMPLEMENTED
```

```java
TODO
```

> Example of response

```json
{
  "result": "ok",
  "data": [
    {
      "key": "application.name",
      "value": "BaasBox",
      "description": "The App name",
      "type": "String"
    },
    {
      "key": "session_tokens.timeout",
      "value": "0",
      "description": "The expiration time of the session tokens (in minutes). WARNING: the admin console refreshes the session token every 5 minutes, if you set a value lower than 5, you may experience disconnection from the console. To disable expiration set it to 0.",
      "type": "Integer"
    },
    {
      "key": "network.http.ssl",
      "value": "false",
      "description": "Set to TRUE if the BaasBox server is reached via SSL through a reverse proxy.",
      "type": "Boolean"
    },
    {
      "key": "network.http.url",
      "value": "localhost",
      "description": "The public url of the BaasBox server. I.e. the url used by the App to contact BaasBox, without the protocol prefix (i.e. http://) and PORT",
      "type": "String"
    },
    {
      "key": "network.http.port",
      "value": "9000",
      "description": "The public TCP port used by the App to contact BaasBox. Please note: when behind a reverse proxy, this could be different from the port used by BaasBox.",
      "type": "Integer"
    }
  ],
  "http_code": 200
}
```

`GET /admin/configuration/:section`

Returns a JSON representing a section of the configuration.

Parameter | Description
--------- | -----------
**section** | The name of a section. One of: `PasswordRecovery`, `Application`, `Push`, `Images`. Mandatory.


## Update a value in settings

> Example of request to update the key `application.name`

```shell
curl -X PUT http://localhost:9000/admin/configuration/Application/application.name/NewName \
	 -H X-BB-SESSION:4efcd048-8865-4047-94c9-8ac58e511b4b  \
	 -H X-BAASBOX-APPCODE:1234567890
```

```objective_c
TO BE IMPLEMENTED
```

```java
TODO
```

> Example of response

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```


`PUT /admin/configuration/:section/:key/:value`

Updates a specific value in the settings.

Parameter | Description
--------- | -----------
**section** | The name of a section. One of: `PasswordRecovery`, `Application`, `Push`, `Images`. Mandatory.
**key** | The name of the key to update. Mandatory.
**value** | The new value for the key. Mandatory.


## Push Notifications

Push notifications are messages that a user can receive using an APP that has BaasBox as back-end. Supported platforms are Android and iOS. 

## Enable push notifications

> Example of request to enable push notifications

```shell
curl -X PUT  http://localhost:9000/push/device/ios/123  \
 	 -H X-BB-SESSION:2605d809-03f0-4751-8f8e-5f658e179a23
```

```objective_c
// Assumes there is a logged in user
BAAClient *client = [BAAClient sharedClient];
[client askToEnablePushNotifications];
```

```java
TODO
```

> Example of response

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```

`PUT /push/device/:os/:pushToken`

Allows to enable the reception of push notifications.

Parameter | Description
--------- | -----------
**os** | The operative system. One of: `ios`, `android`. Mandatory.
**pushToken** | The token returned by either Apple or Google to enable push notifications. Mandatory.





## Send a push notification

```shell
curl -X POST  http://localhost:9000/push/message/cesare  \
	 -d '{"message" : "hi"}' \
	 -H Content-type:application/json \
 	 -H X-BB-SESSION:2605d809-03f0-4751-8f8e-5f658e179a23
```

```objective_c
TO BE IMPLEMENTED
```

```java
TODO
```

> Example of response

```json
{
  "result": "ok",
  "data": "",
  "http_code": 200
}
```


`POST /push/message/:username`

Allows to send a push notification. It will be sent to every device the user has enabled push notifications.

Parameter | Description
--------- | -----------
**username** | The username of the user that has to receive the notification. Mandatory.





# Hacking

You can override many default value and options by providing them to the JVM. To do so, you have to use the -D parameter in this way

`./start -DBAASBOX_PARAMETER=NEW_VALUE`

Where `BAASBOX_PARAMETER` is the key of the parameter to override and `NEW_VALUE` is the value you want to use. 
Please note that there is no space between the D and the parameter name. Overridable keys are:


Key | Description | Example
--------- | ----------- | -------------
**http.port** |	The port used by BaasBox |	`-Dhttp.port=80`
**https.port** |	The SSL port used by BaasBox. By default SSL is disabled |	`-Dhttp.port=443`
**application.code** |	Your Application Code. You should override the default one and choose a very unique code |	`-Dapplication.code=Zh54re3`
**orient.baasbox.path** |	The path of the embedded database. By default this is {BAASBOX_HOME/db/baasbox}  |	`-Dorient.baasbox.path=./mydb`
**logger.application** |	The default level of the logger. By default is DEBUG. Possible values are ERROR, WARNING, INFO, DEBUG, TRACE |	`-Dlogger.application=INFO`
**config.file** | 	An external configuration file. You can put all your parameters in a file. This file MUST include the include classpath(“application.conf”) directive, otherwise BaasBox will not work | `-Dconfig.file=baasbox.config` then you have to create a file named baasbox.config

Regarding the `config.file` key, a possible example of an external configuration file may be:

```
include classpath("application.conf")
application.code="1234-56789"
orient.baasbox.path=db/baasbox
logger.application=DEBUG
```

## The Play! Framework

Since BaasBox is based upon the Play! Framework, many configuration options available by Play! could be used with BaasBox. Please refer to the [Play! documentation](http://www.playframework.com/documentation/2.1.x/Configuration) to know how to perform such operations and to customize the default behavior.