# Stream 2B Flask Material UI application

The purpose of this application is provide an easy way to store, rate and use cooking recipes.

## Prerequisites

You will need the following things properly installed on your computer.

* [Git](https://git-scm.com/)
* [Python3](https://www.python.org/) (with HomeBrew & Venv)
* [Google Chrome](https://google.com/chrome/)

## Installation

* ```git clone git@github.com:ramblingbarney/refactored-funicular.git```
* ```cd refactored-funicular```
* ```pip3 install -r /path/to/requirements.txt```
* ```export YOURAPPLICATION_SETTINGS=config.py``` to load app configuration file to the environment variables
* ```export FLASK_CONFIG=development``` to create FLASK_CONFIG environment variable for development version of the app
* ```export FLASK_CONFIG=production``` to create FLASK_CONFIG environment variable for production version of the app

### Running Tests

* Download the latest chromedriver binary: https://sites.google.com/a/chromium.org/chromedriver/downloads, for linux ensure the binary is in your path or for windows provide a full path 'c:\< >.exe' on line 21 of 'test_front_end.py'.  
* Install and run MongoDB (community edition) locally on the default port: https://docs.mongodb.com/manual/administration/install-community/
  * ```sudo chown -R <user>:<user> /data/db```
  * ```mkdir ~/mongo```
  * ```mkdir ~/mongo/mongodb```
  * ```cp /etc/mongo.conf ~/mongo/```
  * Update paths in mongo.conf to the absolute user path e.g. /home/<user>/mongo
  * ```mongo --host localhost``` Mongo Shell
  * ```use admin```
  * ```db.runCommand({getCmdLineOpts: 1})``` Verify setup of running local Mongo instance with expected output below
    ```
    {
    	"argv" : [
    		"mongod",
    		"--config",
    		"/home/<user>/mongo/mongod.conf"
    	],
    	"parsed" : {
    		"config" : "/home/<user>/mongo/mongod.conf",
    		"net" : {
    			"bindIp" : "127.0.0.1",
    			"port" : 27017
    		},
    		"processManagement" : {
    			"timeZoneInfo" : "/usr/share/zoneinfo"
    		},
    		"storage" : {
    			"dbPath" : "/home/<user>/mongo/mongodb",
    			"journal" : {
    				"enabled" : true
    			}
    		},
    		"systemLog" : {
    			"destination" : "file",
    			"logAppend" : true,
    			"path" : "/home/<user>/mongo/mongod.log"
    		}
    	},
    	"ok" : 1
    }
    ```

  * ```use recipe_app_testing```
  * ```db.createUser({user:"recipeapptester", pwd:"changeme5", roles:[{role: "dbOwner", db: "recipe_app_testing" }]})```

* Run the following commands
  * ```chromedriver --port=9515```
  * ```export FLASK_CONFIG=testing```
  * ```export YOURAPPLICATION_SETTINGS=config.py```
  * ```mongod --config ~/mongo/mongod.conf```
  * ```mongo --host localhost```
    * ```use recipe_app_testing``` Mongo Shell command
    * ```db.createUser( { user: "recipeapptester", pwd: "changeme5", roles: [ "readWrite", "dbAdmin" ] } )``` Mongo Shell command
  * ```python3 -m unittest tests/test_front_end.py```

## Acceptance tests

### Get Category (Show all fixture categories)

* As a user I want to see the categories that have been created from fixtures ['Meal for 1', 'Evening Meal for 2', 'Sunday Lunch for all the family'].

  * Example acceptance criteria:
    * 3 categories will be shown on the page ['Meal for 1', 'Evening Meal for 2', 'Sunday Lunch for all the family']

### Get Category (Show all fixture categories with Delete button)

* As a user I want to see the categories that have been created and each one will be shown with a 'Delete' button.

  * Example acceptance criteria:
    * Each category created will have a 'Delete' link/button
    * The page will have 3 'Delete' link/buttons

### Get Category (Show all fixture categories with Edit button)

* As a user I want to see the categories that have been created and each one will be shown with a 'Edit' button.

  * Example acceptance criteria:
    * Each category created will have a 'Edit' link/button
    * The page will have 3 'Edit' link/buttons

### Delete the first Category

* As a user I want to click on the 'Delete' link/button for the first category, the page refreshes and it disappears

  * Example acceptance criteria:
    * Click on the 'Delete' link/button for the first category line
    * The category entry is no longer shown

### Delete all the Categories

* As a user I want to click on the 'Delete' link/button for all categories, the page refreshes and it disappears

  * Example acceptance criteria:
    * Click on the 'Delete' link/button for the categories shown
    * All deleted categories will disappear
    * No category entries will exist to be shown

### Delete the last Category

* As a user I want to click on the 'Delete' link/button for the last category, the page refreshes and it disappears

  * Example acceptance criteria:
    * Click on the 'Delete' link/button for the last category line
    * The category entry is no longer shown

### Edit Last Category

* As a user I want to click on the 'Edit' link/button on the last category and that category will be shown individually on a page where it can be edited, cancelled and amendments saved.

* Example acceptance criteria:
  * An input box with the existing category text
  * links/buttons to create a 'Cancel' the amendment and 'Edit' (save) the category

* As a user I want to click on the 'Edit' link/button for a category and that category will be shown individually on a page where it can be cancelled and then all categories will be shown.

  * Example acceptance criteria:
    * Each category created will have a 'Delete' and 'Edit' link/button
    * Clicking on Edit will show that category individually with the text in an input box
    * Clicking will return the user to the all categories shown page

### Add Category

* As a user I want to add a category.

* Example acceptance criteria:
  * Entering text into the input box Category Name
  * Clicking button 'Add Category'
  * The recipe name will appear on the 'get_categories' page

### Get Cuisine (Show all fixture cuisines)

* As a user I want to see the cuisines that have been created from fixtures ['Thai','Chinese','Indian'].

  * Example acceptance criteria:
    * 3 cuisines will be shown on the page ['Thai','Chinese','Indian']

### Get Cuisine (Show all fixture Cuisines with Delete button)

* As a user I want to see the cuisines that have been created and each one will be shown with a 'Delete' button.

  * Example acceptance criteria:
    * Each cuisine created will have a 'Delete' link/button
    * The page will have 3 'Delete' link/buttons

### Get Cuisine (Show all fixture Cuisines with Edit button)

* As a user I want to see the cuisines that have been created and each one will be shown with a 'Edit' button.

  * Example acceptance criteria:
    * Each cuisine created will have a 'Edit' link/button
    * The page will have 3 'Edit' link/buttons

### Delete the first Cuisine

* As a user I want to click on the 'Delete' link/button for the first cuisine, the page refreshes and it disappears

  * Example acceptance criteria:
    * Click on the 'Delete' link/button for the first cuisine line
    * The cuisine entry is no longer shown

### Delete all the Cuisines

* As a user I want to click on the 'Delete' link/button for all cuisines, the page refreshes and it disappears

  * Example acceptance criteria:
    * Click on the 'Delete' link/button for the cuisines shown
    * All deleted cuisines will disappear
    * No cuisine entries will exist to be shown

### Delete the last Cuisine

* As a user I want to click on the 'Delete' link/button for the last cuisine, the page refreshes and it disappears

  * Example acceptance criteria:
    * Click on the 'Delete' link/button for the last cuisine line
    * The cuisine entry is no longer shown

### Edit Last Cuisine

* As a user I want to click on the 'Edit' link/button on the last cuisine and that cuisine will be shown individually on a page where it can be edited, cancelled and amendments saved.

* Example acceptance criteria:
  * An input box with the existing cuisine text
  * links/buttons to create a 'Cancel' the amendment and 'Edit' (save) the cuisine

* As a user I want to click on the 'Edit' link/button for a cuisine and that cuisine will be shown individually on a page where it can be cancelled and then all cuisines will be shown.

  * Example acceptance criteria:
    * Each cuisine created will have a 'Delete' and 'Edit' link/button
    * Clicking on Edit will show that cuisine individually with the text in an input box
    * Clicking will return the user to the all cuisines shown page

### Add cuisine

* As a user I want to add a cuisine.

* Example acceptance criteria:
  * Entering text into the input box cuisine Name
  * Clicking button 'Add Cuisine'
  * The recipe name will appear on the 'get_cuisines' page

### Get Recipes Headings (Show all fixture recipes headings)

* As a user I want to see the recipe headings that have been created from fixtures ['Avocado and Tuna Tapas', 'Chinese Pepper Steak', 'Moroccan Chicken with Saffron and Preserved Lemon'].

* Example acceptance criteria:
  * 3 recipes headings will be shown on the page ['Avocado and Tuna Tapas', 'Chinese Pepper Steak', 'Moroccan Chicken with Saffron and Preserved Lemon']

### Get Recipes Descriptions (Show all fixture recipes descriptions)

* As a user I want to see the recipe descriptions that have been created from fixtures.

* Example acceptance criteria:
  * 3 recipe descriptions will be shown on the page

### Add Recipe Name

* As a user I want to add a recipe name.

* Example acceptance criteria:
  * Entering text into the input box Recipe Name
  * Clicking button 'Add Recipe'
  * The recipe name will appear on the 'get_recipes' page

### Add Recipe Description

* As a user I want to add a recipe description.

* Example acceptance criteria:
  * Entering text into the input box Recipe Description
  * Clicking button 'Add Recipe'
  * The recipe description will appear on the 'get_recipes' page

### Show Recipe

* As a user I want to click on the 'show' recipe link/button and be shown the full recipe (name, description, instructions and ingredients).

* Example acceptance criteria:
  * Clicking 'Show' loads page with;
    * Recipe name
    * Recipe description
    * Recipe instructions
    * Recipe ingredients

## Manual Testing

* Open '/add_recipe.html' template, add text to all fields and select an option in the category select box, leave a different field empty or unselected select box each time and attempt to submit the form, a hover message should appear on the empty field or unselected select box stating input text required or selection required.

## Known Issues

* Mongo DB admin password has not been set & database setup is for local testing only
* When running all tests a resource warning is displayed for a number of unclosed sockets
  "ResourceWarning: unclosed <socket.socket fd=9, family=AddressFamily.AF_INET, type=SocketKind.SOCK_STREAM, proto=6, laddr=('127.0.0.1', 55958), raddr=('127.0.0.1', 55261)>"

<!-- TODO: no checks are made for duplicate categories or recipies -->
