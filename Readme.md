## TestLink Jenkins Integration

### Introduction

This project serves as an example guide on how to integrate [TestLink](http://testlink.org/) Test Report Management Tool
with Jenkins in the CI pipeline.

All the services required have been included in the docker-compose.yml file

Each testsuite is output on a separate sheet.

### Instructions

1. Run `docker-compose up -d --build`

2. TestLink
    * TestLink on your browser on port 8008
    * Create a Demo `Test Project`
    * Create a Demo `Test Plan`
    * Create custom field `method_name` and assign to test cases
    * Create a `Test suite`
    * Create sample automated test cases and fill in the `method_name` field with `Class#methodName` from the tests automated in the phpunit-reporter test cases.
 
3. Jenkins
    * Login to Jenkins container and install dependencies for the sample project included in the directory `/var/jenkins_home/phpunit-reporter`
    * Open Jenkins on your browser on port 8088
    * Install proposed plugins
    * Install `TestLink`  plugin
    * Configure the plugin. Read more about the plugin [here](https://wiki.jenkins.io/display/JENKINS/TestLink+Plugin)
    * Install `Copy To Workspace` plugin
    * Configure `Copy To Workspace` plugin to copy from the `/var/jenkins_home/phpunit-reporter` directory before every build
    * Read more about the plugin [here](https://wiki.jenkins.io/display/JENKINS/Clone+Workspace+SCM+Plugin)
    * Create a new job to run the tests for the sample project `phpunit-reporter`.
    * Add a new build strategy `Invoke TestLink`
    * Configure the build to run the test with the bash command `sh run-test.sh` 
    
 With this, you have completed the setup and on every run, the test cases in TestLink will be automatically updated after every run.



If you come across any issues please [report them here](https://github.com/akongnwi02/junit-xml-processor/issues). or email me at 
akongnwi02@gmail.com

Thanks
