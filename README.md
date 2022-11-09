<!---
Links
-->
[Start For Free]: https://jfrog.co/devops-6693#saas "https://jfrog.co/devops-6693#saas"
[Access Tokens]: https://www.jfrog.com/confluence/display/JFROG/Access+Tokens
[awesome-micro-npm-packages]:https://github.com/parro-it/awesome-micro-npm-packages
[jfrog-npm-tools]:https://github.com/jfrog/jfrog-npm-tools
[frogbot]: https://github.com/jfrog/frogbot
[IDEA Plugin]:https://www.jfrog.com/confluence/display/JFROG/JFrog+IntelliJ+IDEA+Plugin
[Docker Desktop Extension]:https://jfrog.com/blog/get-peace-of-mind-about-security-when-deploying-containers-from-docker-desktop/

# dependencies-workshop

[About](#about) 

[Agenda](#agenda)
* [Free Tier jFrog Platform](#free)
* [Configure your environment](#config-free)
  + [Login credentials](#login)
  + [Create NPM repository](#repo)
    - [Configure .npmrc](#config-npm)
  + [Auth & Tokens](#auth)
    - [Generate Token](#token)
  + [Integrations (jfrog-cli)](#cli)
    - [Configure (jfrog-cli)](#config-cli)
* [NPM project](#demo-npm)
  + [Clone a NPM project](#demo-npm-clone)
  + [Install the dependencies](#demo-npm-install)
  + [Audit](#demo-npm-audit)
     - [NPM Audit](#demo-npm-audit-npm)
     - [JFrog Audit](#demo-npm-audit-jfrog)
*  [Frogbot](#frogbot)
*  [IDE plugins](#ide)
*  [Docker Desktop Extension](#docker)
*  [jfrog-npm-tools](#npm-tools)

  

## About <a id='about'></a>
The benefit of software dependencies is that they allow developers to deliver software faster by  building on previous code. 
Dependencies are an integral part of the software development cycle, and they will be used at different stages i.e. development, execution or testing. 
Yet dependencies not only may introduce risks that are often overlooked, but their fast resolution and compliance with license types must be taken into consideration. In the session that accompanies this repository we will review the types of dependencies out there, tools that help us resolve them quickly and securely.


## Agenda <a id='agenda'></a>

### Free Tier jFrog Platform <a id='free'></a>

* [Start For Free]
* Select **CLOUD** ( use the SaaS version i.e. Cloud )
* ```Server Name``` An easy name you will remember
* ```Vendor``` Choose **AWS &  EU-Central**    :point_left:
* **Confirm your account**  by email   :email:

### Configure your environment <a id='config-free'></a>

#### 1. Login credentials <a id='login'></a>

On the **Verification Required** email:
* Platform URL: ```<platform url>``` :grey_exclamation:
* Username: ```<username>``` :grey_exclamation:

Go to the ```<platform URL>``` and log in with the ```username```

---
**NOTE**

:bulb:

Create a new __Admin__ user is a great idea! 

---

#### 2. Create NPM repository <a id='repo'></a>

**Quick Setup** > NPM 

* Create new Repository
* Repository prefix : **workshop**  :pencil: *this is just a suggestion*

##### Configure ~/.npmrc <a id='config-npm'></a>

**Main** *Tab* > **Set Me up** 

* Select the *NPM repository* i.e. virtual repository ```<repository_prefix>```
* On the **Configure** *Tab*   copy the snippet to your ~/.npmrc file.

:pencil: If you authenticate you can copy the snippet with your ```_auth``` information.

:fire: *It's your* ```_auth``` *information, be careful!*

#### Auth & Tokens <a id='auth'></a>

**Administration** *Tab* > **User Management** > **Access Tokens**

##### Generate Token <a id='token'></a>
Token scope: **User**
Service: **All**

:ledger:
:pencil: [Access Tokens]

:fire: *The token information won't be available after the window is closed, keep it available until you configure* ```jfrog-cli```  

#### Integrations (jfrog-cli) <a id='cli'></a>

**Main** *Tab* > **Integrations** > **jfrog-cli**

* Install the ```jfrog-cli``` with the terminal command
i.e. 
```
curl -fL "https://install-cli.jfrog.io" | sh; jf setup <user_context>
```
##### Configure (jfrog-cli) <a id='config-cli'></a>
:pencil:
You will need:
* Access token [Access Tokens]
* Select the NPM repositories 
  + Publish use:  ```<repository_prefix>-local```
  + Resolving use: ```<repository_prefix>-remote```


### NPM project <a id='demo-npm'></a>
#### Clone a NPM project <a id='demo-npm-clone'></a>

Clone a npm repo of your preference. 

We can use any demo found under [awesome-micro-npm-packages]

#### Install the dependencies <a id='demo-npm-install'></a>

Use verbose to verify the registry in use
```npm install --ddd```

#### Audit <a id='demo-npm-audit'></a>

All about dependencies.... 

##### NPM Audit <a id='demo-npm-audit-npm'></a>
Run the npm audit on the repository
```npm audit```

:pencil: *You may need to lock the dependencies resolution*

```npm i --package-lock-only```

Common error in many NPM projects: *lockfile for dependency resolution*
```
npm ERR! code EAUDITNOLOCK
npm ERR! audit Neither npm-shrinkwrap.json nor package-lock.json found: Cannot audit a project without a lockfile
npm ERR! audit Try creating one first with: npm i --package-lock-only
```

##### JFrog Audit <a id='demo-npm-audit-jfrog'></a>

:green_heart: Just be happy!! :green_heart:

```jf audit```


### Frogbot <a id='frogbot'></a>

#### What is Frogbot?

Frogbot is a Git bot that does the following:

Scans pull requests for security vulnerabilities.
Opens pull requests with fixes for security vulnerabilities.

Frogbot uses JFrog Xray (version 3.29.0 or above is required) to scan your pull requests. It adds the scan results as a comment on the pull request. If no new vulnerabilities are found, Frogbot will also add a comment, confirming this. For pull requests scanning, please note that GitHub, GitLab and Bitbucket Server are supported. Projects that use one of the following tools to download their dependencies are currently supported.

* Npm
* Maven
* Gradle
* Go
* Pip
* Pipenv
* Nuget
* Dotnet

:pencil:

More information about  [frogbot]

### IDE plugins <a id='ide'></a>

**Main** *Tab* > **Integrations** > **IDE plugins**

#### IDE plugins: IDEA <a id='ide'></a>

In addition to IntelliJ IDEA, the JFrog IDEA plugin also supports the following IDEs.
* WebStorm
* PyCharm
* Android Studio
* GoLand

Since version 1.6.2, the plugin requires version 2020.1 of IDEA.

The plugin allows developers to see valuable information about the status of their code by continuously scanning it locally with JFrog Xray. 

Currently, Maven, Gradle, npm, Python and Go are supported by the plugin.

:pencil:

More information about  [IDEA Plugin]

### Docker Desktop Extension <a id='docker'></a>

The JFrog Xray integration with the Docker Desktop Extension actually allows you to set a free tier instance and connect it automatically. After installing the JFrog extension within Docker Desktop Extensions, you can easily connect your JFrog Platform to your Docker Desktop application.

:pencil:

More information about  [Docker Desktop Extension]

### JFrog NPM Tools <a id='npm-tools'></a>

A collection of tools to help audit your NPM dependencies for suspicious packages or
continuously monitor dependencies for future security events.

The tools:

1. [npm-secure-install](npm-secure-installer/README.md) - Validate dependencies are locked down
   to the exact versions before installation of global tools
2. [package-checker](package_checker/README.md) - Python command line tool that checks a
   dependency string for what will actually be installed and whether it is suspicious
3. [npm_issues_statistics](npm_issues_statistics/README.md) - Analyzes github comments to find
   unusual activity that might correlate to compromised dependency

More information about  [jfrog-npm-tools]