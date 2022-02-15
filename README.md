<div id="top"></div>

[![Contributors][contributors-shield]][contributors-url]
[![Forks][forks-shield]][forks-url]
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![MIT License][license-shield]][license-url]
[![LinkedIn][linkedin-shield]][linkedin-url]



<!-- PROJECT LOGO -->
<br />
<div align="center">

<h3 align="center">dd-beanstalk-php-example</h3>

  <p align="center">
    Instrumenting AWS beanstalk PHP example with Datadog
    <br />
    <a href="https://github.com/abruneau/dd-beanstalk-php-example"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/abruneau/dd-beanstalk-php-example/issues">Report Bug</a>
    ·
    <a href="https://github.com/abruneau/dd-beanstalk-php-example/issues">Request Feature</a>
  </p>
</div>



<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li>
        <a href="#installation">Installation</a>
        <ul>
            <li><a href="#with-eb-cli">With EB cli</a></li>
            <li><a href="#in-aws-console">In AWS console</a></li>
        </ul>
        </li>
      </ul>
    </li>
    <li><a href="#documentation">Documentation</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#acknowledgments">Acknowledgments</a></li>
  </ol>
</details>



<!-- ABOUT THE PROJECT -->
## About The Project
The goal of this project is to show how to add and configure Datadog to an AWS Beanstalk environment. The code is based on [AWS Elastic Beanstalk PHP sample](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/tutorials.html)

<p align="right">(<a href="#top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting Started

### Prerequisites

AWS:
* An AWS account
* EB cli installed ([Install the EB CLI](https://docs.aws.amazon.com/elasticbeanstalk/latest/dg/eb-cli3-install-advanced.html)) (optional)

Datadog:
* An account. If you don't already have one, you can create a trial on [Datadog website](https://www.datadoghq.com/).
* An [API key](https://docs.datadoghq.com/account_management/api-app-keys/)
* Configure [AWS integration](https://docs.datadoghq.com/integrations/amazon_web_services/?tab=roledelegation) (optional)


### Installation

Add your API key in `.ebextensions/99datadog.config`

#### With EB cli

```sh
# Initialize eb
eb init

# Deploy the application
eb create php-beanstalk-example
```

to update the deployment

```sh
eb deploy
```

To clean it up

```sh
eb terminate
```

#### In AWS console
1. Open the Elastic Beanstalk console using this link: https://console.aws.amazon.com/elasticbeanstalk/home#/gettingStarted?applicationName=getting-started-app
2. Optionally add application tags.
3. For Platform, choose PHP, and then choose Create application
4. On the application overview page, choose Create a new environment.
5. Next, for environment tier, choose the **Web server environment**
6. For Platform, select the latest PHP
7. For Application code, choose the archive and upload a zip version of your repo
8. Choose Create environment.

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- Documentation EXAMPLES -->
## Documentation

- [Configuring the agent](./doc/configure_agent.md)
- [Add PHP Tracer](./doc/add_php_tracer.md)

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- ROADMAP -->
## Roadmap

- [ ] Add examples for other agent feature

See the [open issues](https://github.com/abruneau/dd-beanstalk-php-example/issues) for a full list of proposed features (and known issues).

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

Distributed under the MIT License. See `LICENSE.txt` for more information.

<p align="right">(<a href="#top">back to top</a>)</p>



<!-- CONTACT -->
## Contact

Project Link: [https://github.com/abruneau/dd-beanstalk-php-example](https://github.com/abruneau/dd-beanstalk-php-example)

<p align="right">(<a href="#top">back to top</a>)</p>


<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->
[contributors-shield]: https://img.shields.io/github/contributors/abruneau/dd-beanstalk-php-example.svg?style=for-the-badge
[contributors-url]: https://github.com/abruneau/dd-beanstalk-php-example/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/abruneau/dd-beanstalk-php-example.svg?style=for-the-badge
[forks-url]: https://github.com/abruneau/dd-beanstalk-php-example/network/members
[stars-shield]: https://img.shields.io/github/stars/abruneau/dd-beanstalk-php-example.svg?style=for-the-badge
[stars-url]: https://github.com/abruneau/dd-beanstalk-php-example/stargazers
[issues-shield]: https://img.shields.io/github/issues/abruneau/dd-beanstalk-php-example.svg?style=for-the-badge
[issues-url]: https://github.com/abruneau/dd-beanstalk-php-example/issues
[license-shield]: https://img.shields.io/github/license/abruneau/dd-beanstalk-php-example.svg?style=for-the-badge
[license-url]: https://github.com/abruneau/dd-beanstalk-php-example/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/antoninbruneau