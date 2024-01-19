<h1 align="center">"TRAEKTORIA" SHOP ANDROID APP TESTING PROJECT</h1>  
<p align="center">
    <a href="https://www.traektoria.ru/">
        <img src="resources/logo_traektoria.svg" height="100" />
    </a>
</p>

<h2 align="center">Used stack</h2>
<p align="center">
    <a href="https://www.atlassian.com/software/jira/">
        <img src="resources/jira-original.svg" height="40" width="40" />
    </a>
    <a href="https://www.python.org/">
        <img src="resources/python-original.svg" height="40" width="40" />
    </a>
    <a href="https://www.jetbrains.com/pycharm/">
        <img src="resources/pycharm-logo.svg" height="40" width="40" />
    </a>
    <a href="https://www.android.com/">
        <img src="resources/Android_robot.svg" height="40" width="40" />
    </a>
    <a href="https://www.selenium.dev/documentation/webdriver/">
        <img src="resources/selenium-original.svg" height="40" width="40" />
    </a>
    <a href="https://appium.io/">
        <img src="resources/appium.svg" height="40" width="40" />
    </a>
    <a href="https://docs.pytest.org/">
        <img src="resources/pytest-original.svg" height="40" width="40" />
    </a>
    <a href="https://git-scm.com/">
        <img src="resources/git-original.svg" height="40" width="40" />
    </a>
    <a href="https://www.jenkins.io/">
        <img src="resources/jenkins-original.svg" height="40" width="40" />
    </a>
    <a href="https://allurereport.org/">
        <img src="resources/allure-report-logo.svg" height="40" width="40" />
    </a>
    <a href="https://qameta.io/">
        <img src="resources/allure-testops.svg" height="40" width="40" />
    </a>
    <a href="https://telegram.org/">
        <img src="resources/telegram-logo.svg" height="40" width="40" />
    </a>
</p>  

<h2 align="center">Content</h2>  

* [Description](#description)  
* [Tests launch](#tests-launch)  
    * [Local launch](#local-launch)  
        * [Preparing the environment](#preparing-the-environment)  
        * [Launch](#launch)  
        * [Generating a test report](#generating-a-test-report)  
    * [Launch using Jenkins](#launch-using-jenkins)  
* [Tests results](#tests-results)  
    * [TestOps report](#testops-report)  
    * [Allure report](#allure-report)  
    * [Telegram notification](#telegram-notification)  

## Description

Tests are developed using [Python](https://www.python.org/) programming language, [Selene](https://github.com/yashaka/selene), [Appium](https://appium.io/) and [PyTest](https://docs.pytest.org/) frameworks. Device emulation is carried out using [Android Studio](https://developer.android.com/studio). Reports are generated by [Allure Report](https://allurereport.org/). Test reports are also sent by [Telegram Bot](https://core.telegram.org/bots) if you launch tests [using Jenkins](#launch-using-jenkins).  
In this project we check the following:  
* Opening "Brands" bar.
* Products' search.  
* Checking "Profile" bar content.  

## Tests launch

### Local launch

#### Preparing the environment

Before launch, you need to install the following (installation guide links are provided):  
* [PyCharm](https://www.jetbrains.com/pycharm/).  
* [PyTest](https://docs.pytest.org/en/7.4.x/getting-started.html#install-pytest).  
* [Selene](https://github.com/yashaka/selene?tab=readme-ov-file#installation).  
* [Appium](https://appium.io/docs/en/2.4/quickstart/).  
* [Android Studio](https://developer.android.com/studio/install).  
* [Allure Pytest](https://pypi.org/project/allure-pytest/).  

Also, download the repository with this project on your PC/laptop:  
* Click on "**<> Code**" on the [project page](https://github.com/engovadzip/traektoria_android_app_test_project).  
* In the opened pop-up menu click on "**Download ZIP**".  
* Download it to preferred directory and unpack downloaded archive there.  

Create ```.env.emulator``` file in the directory. Open it. Insert the following:
```
REMOTE_URL='http://127.0.0.1:4723'
APP='traektoria_app.apk'
UDID='emulator-5554' 
```

Prepare Android Studio and Appium environments as described [here](https://autotest.how/appium-setup-for-local-android-tutorial-md).

#### Launch

Open Android Studio. Create virtual device as described [here](https://developer.android.com/studio/run/managing-avds). Open created virtual device. It will be look like this:

<p align="center">
    <img src="resources/virtual_device.png"/>
</p>

Open command line and run the following command:  
```
appium
```
This command creates an environment for virtual device management by autotests. The successful command's result is appeared URLs as shown below:
<p align="center">
    <img src="resources/appium_success.png"/>
</p>

Open any downloaded project's file in PyCharm (right click on file -> Edit with PyCharm). There will be the following window:  
<p align="center">
    <img src="resources/pycharm_project.png"/>
</p>

Click on **Open in Project**. After that there will be a following window:  
<p align="center">
    <img src="resources/trust_project.png"/>
</p>

Click on **Trust Project**.  

Open a terminal in the opened PyCharm window by clicking on terminal button. The button locates at the bottom of the left sidebar as shown in the following figure:
<p align="center">
    <img src="resources/terminal.png"/>
</p>
The terminal will open in the bottom of PyCharm as shown in the following figure:
<p align="center">
    <img src="resources/opened_terminal.png"/>
</p>

Launch tests using the following command:  
```
pytest --context=emulator
```

After running the command, tests will start in the opened virtual device. Tests process is provided below:  
<p align="center">
    <img src="resources/traektoria_mobile.gif" />  
</p>  

After the last step of tests (profile bar checking), the app will close on the virtual device. There will be tests result line in terminal when tests will finish. Its example:  
<p align="center">
    <img src="resources/tests-result.png"/>
</p>

#### Generating a test report

Tests report is generated by Allure Report. To check it, run the following command after tests:  
```
allure serve allure-results
```  
After that, your system's default browser will open and there will be a [generated report](#allure-report).  

### Launch using Jenkins

Open this project on [Jenkins](https://jenkins.autotests.cloud/job/engovadzip_UI_project/). The project's page example is provided below.
<p align="center">
    <img src="resources/jenkins-window.png" />  
</p>  

Click on "**Build Now**".  

<p align="center">
    <img src="resources/jenkins-build.png" />  
</p>  

There will be a new build below "**Build History**" title as shown in the following figure:  
<p align="center">
    <img src="resources/build.png" />  
</p>  

Build's status will change when tests will finish. And there will appear [TestOps](#testops-report) and [Allure](#allure-report) reports as shown in the following figure:  
<p align="center">
    <img src="resources/passed_tests.png" />  
</p>

## Tests results

### TestOps report
Go to [Jenkins project's page](https://jenkins.autotests.cloud/job/engovadzip_android_app_final/). Click on <img src="resources/allure-testops.svg" height="18" width="20" /> in one of successful builds. Tests report is provided below:
<p align="center">
    <img src="resources/testops_screen_1.png" />  
</p>  

<p align="center">
    <img src="resources/testops_screen_2.png" />  
</p>  

### Allure report

If you generate report locally, follow the [instruction](#generating-a-test-report). If you generate it on Jenkins, click on <img src="resources/allure-jenkins.png" height="18" width="18" /> in one of successful builds. Tests report from Jenkins is provided below:
<p align="center">
    <img src="resources/allure-report.png" />  
</p>  

There will not be **TREND** in the report if you generate report locally. It will be in Jenkins only. 

### Telegram notification

After Jenkins' build will finish, Telegram Bot will send a notification with test results to Telegram chat. The chat is private. It is only for tests developer and responsible members. The notification is provided below:
<p align="center">
    <img src="resources/telegram_notification.png" />  
</p>  
