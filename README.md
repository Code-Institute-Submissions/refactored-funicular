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

### Running Tests

* Download the latest chromedriver binary: https://sites.google.com/a/chromium.org/chromedriver/downloads, for linux ensure the binary is in your path or for windows provide a full path 'c:\< >.exe' on line 21 of 'test_front_end.py'.  

* Run the following commands
  * ```chromedriver --port=9515```
  * ```python3 -m unittest tests/test_front_end.py```

## Acceptance tests


### Get Category (Show all categories)

* As a user I want to see the categories that have been created.

  * Example acceptance criteria:
    * Each category created will have a 'Delete' and 'Edit' link/button
    * A link/button to create a 'Add Category' is below the created Categories

### Edit Category

* As a user I want to click on the 'Edit' link/button for a category and that category will be shown individually on a page where it can be edited, cancelled and amendments saved.

* Example acceptance criteria:
  * An input box with the existing category text
  * links/buttons to create a 'Cancel' the amendment and 'Edit' (save) the category

* As a user I want to click on the 'Edit' link/button for a category and that category will be shown individually on a page where it can be cancelled and then all categories will be shown.

  * Example acceptance criteria:
    * Each category created will have a 'Delete' and 'Edit' link/button
    * Clicking on Edit will show that category individually with the text in an input box
    * Clicking will return the user to the all categories shown page

### Delete A Category

  * As a user I want to click on the 'Delete' link/button for a category, the page refreshes and it disappears

  * Example acceptance criteria:
    * Click on the 'Delete' link/button for the category line
    * The category entry is no longer shown

## Manual Testing



## Known Issues
