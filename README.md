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
- Run through the Magento Cloud Docker configuration build process using defaults 

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

This is an example of how you may give instructions on setting up your project locally.
To get a local copy up and running follow these simple example steps.

### Prerequisites

This is an example of how to list things you need to use the software and how to install them.
* npm
  ```sh
  npm install npm@latest -g
  ```

### Installation

1. Get a free API Key at [https://example.com](https://example.com)
2. Clone the repo
   ```sh
   git clone https://github.com/carlos-reynosa/adobe-commerce-cloud-and-docker-tools.git
   ```
3. Install NPM packages
   ```sh
   npm install
   ```
4. Enter your API in `config.js`
   ```js
   const API_KEY = 'ENTER YOUR API';
   ```

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- USAGE EXAMPLES -->
## Usage

Use this space to show useful examples of how a project can be used. Additional screenshots, code examples and demos work well in this space. You may also link to more resources.

_For more examples, please refer to the [Documentation](https://example.com)_

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
