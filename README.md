Cucumber School - Series 1
==========================

This is the source code from [Cucumber School](https://cucumber.pro/school), a video series 
that teaches you about BDD and Cucumber.

This branch is for series 1. You'll find the source code for the Shouty application developed during this series.

User Stories
------------

1. People can shout messages to one another
2. Messages are only heard within a certain range

======================================
xhttps://github.com/cucumber-ltd/shouty.rb
 
 Gustavo-Macbook-Pro:shouty gustavo.suarezmunoz$ pwd
 /Users/gustavo.suarezmunoz/Documents/test/automation/API/FW/shouty
 
 rvm --default use ruby-2.3.0
 
 
 -------------------
 #Setup
 ##Pre-requisites
 Bundler
     bundler install
 
     gem install bundler
 
 Ruby - using rbenv is recommended - https://cbednarski.com/articles/installing-ruby/
 
 Use Ruby 2.3.0
 
 Installation Steps for Ruby:
 
 curl -L https://get.rvm.io | bash -s stable --ruby
 
 rvm get stable --autolibs=enable
 
 rvm install ruby-2.3.0
 
 rvm --default use ruby-2.3.0
 
 Install git:
 
     Go to https://git-scm.com/downloads and download the version for your Operating System
 
 Install Homebrew:
 
     ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
 
 #Installation
 Clone this git project to your local machine. Within the project folder you'll need to create these folders:
 
     mkdir results
     mkdir logs
     mkdir results/XXXX
     mkdir config/apikeys
     mkdir results/junit
     mkdir results/failed
     mkdir results/failed/xxxxx
     mkdir results/json
 
 Then install all the Ruby dependencies for the project:
 
     bundle install
 
 Then install phantomjs (a very small set of tests uses this to visit a webmail inbox):
 
     brew install phantomjs
 
 ###For Leads Checker
 
 Please refer to the connector/readme.md file
     
 
 ###Running the tests across different endpoints apart from leads
 
 Run tests for a brand
 
     rake api_tests:execute_regression[<environment>,<brand>]
 
 e.g running tests for against UAT for Nissan would be
 
     rake api_tests:execute_regression[uat,xxxx]
 
  ***Note:  Some cmd line shells require you to escape the brackets e.g
 
     rake api_tests:execute_regression\[uat,xxxxx\]
     
 For running smoke tests
     
     rake api_tests:execute_regression[uat,xxxxx,smoke]
 
 
 You can run tests for a particular market by calling cucumber directly and passing in:
 
 - the necessary API versions through environment variables
 
 - test environment and market details as environment variables
 
 - tags for the API/functionality you want to run against
 
 - and any Cucumber options that you like
 
 Below is an example that runs offers V2 tests on UAT for Renault Great Britain
 
     bundle exec cucumber --r features features/feature_files/ --tags @xxxxxx environment=uat brand=xxx country_name=Great-Britain country_code=GB language=en offers=v2
 
 ####Test Results
 The results can be found under results/{brand}. Each result file will have the environment, brand, country and timestamp in the filename
 
 ##Useful Info
 All the market/brand config data for a test run is declared in the {brand}_run_config.yml under config/run_config/
 
 Environment URLs are defined in environment.yml file under features/conig
 
 Client keys are defined in config/clientkeys/{environment}.yml
 
 Test data is are stored in yml files under config/test_data/
 
 API end points are defined in config/paths.yml
 
 Feature files should be generic enough to use across all the brands and markets
 
 To set which features to run for a brand/market edit the 'tags' attribute inside {brand}_run_config.yml
 
 If we do not specify any tags for a market then by default it runs all the features in the framework
 
 Feature files are organised in to folders for each API under test. You'll find that some API's have folders for V0, V1, and V2 because the functionality between API versions can be so different that using the same feature file to run against different versions is not possible. This is especially true for version 0 of the APIs.
 
 ------------------
 
 ## IDE
 
 IDE Options
 
 1, Rubymine (Community Version) - RECOMMENDED
 
    * [RUBYMINE](https://www.jetbrains.com/ruby/)
 
 2, IntelliJ (You need licence )
 
    * [IntelliJ](https://www.jetbrains.com/idea/)
 
 ## License
 
 Movember Foundation API Acceptance Test is released under Mo Licence.
