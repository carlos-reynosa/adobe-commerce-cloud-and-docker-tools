<div id="top"></div>

<!-- PROJECT SHIELDS -->
<!--
*** I'm using markdown "reference style" links for readability.
*** Reference links are enclosed in brackets [ ] instead of parentheses ( ).
*** See the bottom of this document for the declaration of the reference variables
*** for contributors-url, forks-url, etc. This is an optional, concise syntax you may use.
*** https://www.markdownguide.org/basic-syntax/#reference-style-links
-->
[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]



<!-- PROJECT LOGO -->
<br />
<div align="center">

<h3 align="center">Adobe Commerce Cloud and Docker Tools</h3>

  <p align="center">
    This project contains scripts and configurations for making it easier to work with Adobe's Commerce Cloud servers and Magento docker local environments. 
    <br />
    <a href="https://github.com/carlos-reynosa/adobe-commerce-cloud-and-docker-tools"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/carlos-reynosa/adobe-commerce-cloud-and-docker-tools">View Demo</a>
    ·
    <a href="https://github.com/carlos-reynosa/adobe-commerce-cloud-and-docker-tools/issues">Report Bug</a>
    ·
    <a href="https://github.com/carlos-reynosa/adobe-commerce-cloud-and-docker-tools/issues">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project

This project is a combination of tools and scripts for working with [Magento/Adobe Cloud Commerce](https://github.com/magento/magento-cloud) server environments and the [Magento Cloud Docker](https://github.com/magento/magento-cloud-docker) project for local development. The project contains helpful tools for doing the following in each environment:

### Magento Cloud Commerce
- Replicating an environment into another environment. For example, you may want to setup staging with the latest images and data from production in order to test a new feature. Magento Cloud currently does not have an easy way of doing this, developers must create there own scripts to accomplish this. 
- Flush the cash on a given environment
- Fully reindex a given environment
- Download the database from a local environment
- Get the latest configuration dump from a given environment
- Run the bin/magento command on a given environment
- Sync only images from one environment into another environment
- Replicate and import the database from one environment into another environment 
- Create a db dump export on a remote environment for development  
- Download a copy of the app/etc/env.php file from a given environment 
- Create a remote db backup of a given environment and store it locally
- Create a remote media backup of a given environment and store it locally

### Magento Cloud Docker
- Initialize a local Magento Cloud Docker environment that's an exact replica, including database and images, of a remote Magento Cloud Commerce environment
- Run the deployment process on a local Magento Cloud Docker environment
- Run validation tests on your local environment to ensure that it has the correct tools and files to sucessuflly set up a local Magento Cloud Docker environment
- Run the composer command on the local Magento Cloud Docker environment
- Run the magento command on the local Magento Cloud Docker environment

<p align="right">(<a href="#top">back to top</a>)</p>



### Built With and inspired by

* [kvz/bash3boilerplate](https://github.com/kvz/bash3boilerplate)
    - This project provided templates for creating bash scripts that provided argument parsing and validation, debugging, and logging .
* [markshust/docker-magento](https://github.com/markshust/docker-magento) 
    - This provided inspiration for how to structure much of the code. I also utilized some scripts directly from within this project. 
* [tlatsas/bash-spinner](https://github.com/tlatsas/bash-spinner)
    - This project provided for an easy way to display a spinner to the user during script execution. This was needed in order to show during project initialization that a source database was imported. 
* [jasperes/bash-yaml](https://github.com/jasperes/bash-yaml)
    - This project provided an easy way to work with yaml within bash scripts. This script helped establish the general project configuration at project.ini.dist

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- GETTING STARTED -->
## Getting Started

The requirements for configuring the project will vary depending on if you just want to work with remote Magento Cloud
environments or if your also trying to create a local Magento Docker environment based on a Magento Cloud environment. 

### Installation

1. Clone the repo
   ```sh
   git clone https://github.com/carlos-reynosa/adobe-commerce-cloud-and-docker-tools.git
   ```
2. Setup the project configuration file by providing values to connect to the remote Magento Commerce Cloud Project and code
   ```sh
   cp project.ini.dist project.ini
   ```

<p align="right">(<a href="#top">back to top</a>)</p>


### project.ini Project Configuration Variables

#### SOURCE_DIRECTORY_NAME
- Direction in which the main project code will exist. Example: app

#### PROJECT_ID
- Magento Commerce Project ID used to identify your particular  Commerce Cloud project when establishing a connection

#### CLOUD_VARIABLE_NAME_FORCE_REDEPLOY
- Custom cloud variable name used to  force a redeployment within an environment and that will also skip cache

#### DEFAULT_LOCAL_HOST
- Local host domain used for accessing the local docker development environment. Example test.m2.test

#### PRIMARY_GIT_REPO_URL
- Non Magento Commerce Cloud repo used for managing and storing the application code. This is for use when the Commerce Cloud git repo is only used for publishing changes.

#### MAGENTO_GIT_REPO_URL
- Magento Commerce Cloud git repo URL used for publishing application code into an environment

#### VENDOR_THEME_PACKAGE_NAME
- Vendor package name in the form of vendor/package used for configuring grunt static file generation 

#### THEME_NAME
- Theme name used for local theme development and static file generation with grunt.  

<!-- USAGE EXAMPLES -->
## Usage

### Cloud Environment Management Features
1. Replicate and import the database from one environment into another environment
    - Example: Reinitialize the staging environment with data from source environment production
        - ```bin/cloud/sync-environment-db -e staging -s production```
    - Example: Reinitialize the feature-a environment branch with data from feature-b source environment branch
        - ```bin/cloud/sync-environment-db -e feature-a -s feature-b-environment-branch```
2. Sync media from one environment into another environment
    - Example: Grab the latest media files from production into staging
        - ```bin/cloud/sync-environment-media -e staging -s production```
3. Replicating an environment into another environment. For example, you may want to setup staging with the latest images and data from production in order to test a new feature. Magento Cloud currently does not have an easy way of doing this, developers must create there own scripts to accomplish this.
    - Example: Reinitialize the staging environment with data from source environment production
        - ```bin/cloud/sync-environment-db -e staging -s production```
    - Example: Reinitialize the feature-a environment branch with data from feature-b source environment branch
        - ```bin/cloud/sync-environment-db -e feature-a -s feature-b-environment-branch```
4. Flush the cash on a given environment
      - Example: Flush the cache on integration 
        - ```bin/cloud/cashe-flush -e integration```
      - Example: Flush the cache on integration branch feature-a-integration-branch
        - ```bin/cloud/cashe-flush -e feature-a-integration-branch```
5. Fully reindex an environment
    - Example: Reindex integration  
      - ```bin/cloud/full-reindex -e integration```
6. Run the magento command on a given environment
    - Example: List available magento commands within integration
      - ```bin/cloud/magento -e integration -a 'list'``` 
7. Create a db dump on an environment and store it within it's file directory  at /tmp
    - Example: Create a db dump for development on integration 
      - ```bin/cloud/create-remote-sync-db-dump -e integration```
8. Download the database from an environment into your docker project configuration for initialization
    - Example: Get a db dump from integration and place it in the local project docker directory for docker initialization import  at .docker/mysql/docker-entrypoint-initdb.d/
      - ```bin/cloud/get-db-for-docker -e integration```
9. Get the latest configuration dump from a given environment
   - Example: Grab the application configuration dump from staging and store it in the local project
     - ```bin/cloud/get-latest-config - e staging```
10. Download a copy of the app/etc/env.php file from a given environment
    - Example: Grab the environment configuration file from integration branch feature-branch-a and place it in the local project
       - ```bin/cloud/get-env-file -e feature-branch-a```
11. Create a remote db backup of a given environment and store it locally
    - Example: Create a full backup of production and store it locally within the var directory of the current project
      - ```bin/cloud/backup/backup-db -e production```
12. Create a remote media backup of a given environment and store it locally
    - Example: Create a full backup archive of the media files in staging and store them locally within the project var directory for the environment
      - ```bin/cloud/backup/backup-media -e integration``` 

### Magento Cloud Docker Management Features
1. Initialize a local Magento Cloud Docker environment that's an exact replica, including database and images, of a remote Magento Cloud Commerce environment
      - Example: Initialize a local docker environment based off of staging  for development. Use a fresh db dump form the environment by passing the "-p" flag. 
        - ```bin/docker/init-local-environment -e staging -p```
      - Example: Initialize a local docker environment based off of staging  for development. Omit the "-p" flag in order to used the last used db dump from the environment. 
        - ```bin/docker/init-local-environment -e staging```
2. Run the deployment process on a local Magento Cloud Docker environment according to [Magento Docker Deployment Modes processes](https://devdocs.magento.com/cloud/docker/docker-launch.html)
    - Example: Run the developer deploy process on the currently running Magento Cloud Docker Project
      - ```bin/docker/deploy -m developer```
3. Run validation tests on your local environment to ensure that it has the correct tools and files to successfully set up a local Magento Cloud Docker environment
   - ```bin/docker/local-environment-validation-test```
4. Run the composer command on the local Magento Cloud Docker environment
   - Example: Run composer to install the project code's vendor directory and dependency 
     - ```bin/docker/composer install```
5. Run the magento command on the local Magento Cloud Docker environment
   - Example: Run the magento setup upgrade command on the current local docker application instance
     - ```bin/docker/magento setup:upgrade```
6. Start up the docker project containers
   - ```bin/docker/start```
7. Stop and removal all currently running docker containers and data
   - ```bin/docker/removeall```
8. Setup the local grunt configuratino for local theme development of a particular theme defined within the project.ini configuration  
   - ```bin/docker/setup-grunt```
9. Get the Magento project code referenced within repo PRIMARY_GIT_REPO_URL and place it within the local project directory at SOURCE_DIRECTORY_NAME
    - ```bin/docker/get-core-code```
10. Run the grunt command for the local docker project in order to build a theme
    - ```bin/docker/grunt exec:my-theme```
    - ```bin/docker/grunt less:my-theme```
    
<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ROADMAP -->
## Roadmap

See the [open issues](https://github.com/carlos-reynosa/adobe-commerce-cloud-and-docker-tools/issues) for a full list of proposed features (and known issues).

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTRIBUTING -->
## Contributing

Contributions are what make the open source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".
Don't forget to give the project a star! Thanks again!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- LICENSE -->
## License

Distributed under the GNU General Public License v3.0. See `LICENSE.txt` for more information.

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

Carlos Reynosa - [@carlos_reynosa](https://twitter.com/carlos_reynosa) 

Project Link: [https://github.com/carlos-reynosa/adobe-commerce-cloud-and-docker-tools](https://github.com/carlos-reynosa/adobe-commerce-cloud-and-docker-tools)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ACKNOWLEDGMENTS -->
## Acknowledgments

* []()
* []()
* []()

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/carlos-reynosa/adobe-commerce-cloud-and-docker-tools.svg?style=for-the-badge
[contributors-url]: https://github.com/carlos-reynosa/adobe-commerce-cloud-and-docker-tools/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/carlos-reynosa/adobe-commerce-cloud-and-docker-tools.svg?style=for-the-badge
[forks-url]: https://github.com/carlos-reynosa/adobe-commerce-cloud-and-docker-tools/network/members
[stars-shield]: https://img.shields.io/github/stars/carlos-reynosa/adobe-commerce-cloud-and-docker-tools.svg?style=for-the-badge
[stars-url]: https://github.com/carlos-reynosa/adobe-commerce-cloud-and-docker-tools/stargazers
[issues-shield]: https://img.shields.io/github/issues/carlos-reynosa/adobe-commerce-cloud-and-docker-tools.svg?style=for-the-badge
[issues-url]: https://github.com/carlos-reynosa/adobe-commerce-cloud-and-docker-tools/issues
[license-shield]: https://img.shields.io/github/license/carlos-reynosa/adobe-commerce-cloud-and-docker-tools.svg?style=for-the-badge
[license-url]: https://github.com/carlos-reynosa/adobe-commerce-cloud-and-docker-tools/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/carlosrn
[product-screenshot]: images/screenshot.png
