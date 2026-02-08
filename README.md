<p align="center">
    <a href="https://sylius.com" target="_blank">
        <picture>
          <source media="(prefers-color-scheme: dark)" srcset="https://media.sylius.com/sylius-logo-800-dark.png">
          <source media="(prefers-color-scheme: light)" srcset="https://media.sylius.com/sylius-logo-800.png">
          <img alt="Sylius Logo." src="https://media.sylius.com/sylius-logo-800.png">
        </picture>
    </a>
</p>

<h1 align="center">Sylius Standard Edition</h1>

<p align="center">This is Sylius Standard Edition repository for starting new projects.</p>

## About

Sylius is the first decoupled eCommerce framework based on [**Symfony**](http://symfony.com) and [**Doctrine**](http://doctrine-project.org). 
The highest quality of code, strong testing culture, built-in Agile (BDD) workflow and exceptional flexibility make it the best solution for application tailored to your business requirements. 
Enjoy being an eCommerce Developer again!

Powerful REST API allows for easy integrations and creating unique customer experience on any device.

We're using full-stack Behavior-Driven-Development, with [Behat](http://behat.org)

## Quick local start (recommended)

### One-command setup (recommended)

```bash
make setup-local
```

By default it auto-detects Docker and uses it when available.

Manual mode selection:
```bash
bin/setup-local --mode docker
bin/setup-local --mode native
```

### Docker (recommended for personal computer)

Requirements: Docker + Docker Compose plugin.

```bash
cp compose.override.dist.yml compose.override.yml
cp .env .env.local
make init
```

Open after startup:
- Shop: http://localhost
- Admin: http://localhost/admin
- MailHog: http://localhost:8025

Useful commands:
```bash
make up
make down
make clean
make doctor
make setup-local
```

If port `80` is occupied on your machine, edit `compose.override.yml` and change Nginx mapping, for example to `8080:80`.

### Traditional (without Docker)

Requirements: PHP 8.2+, Composer, Node.js 18+, Yarn, MySQL/MariaDB, Symfony CLI.

```bash
cp .env .env.local
composer install
yarn install
yarn build
php bin/console sylius:install -s default -n
symfony server:start -d
```

Then open http://127.0.0.1:8000.

For Lithuanian step-by-step instructions, see [docs/LOCAL_SETUP_LT.md](docs/LOCAL_SETUP_LT.md).

Tip: run `make doctor` to quickly check local prerequisites and generated files.

You can also preview setup steps without executing them: `bin/setup-local --dry-run`.

## Documentation

Documentation is available at [docs.sylius.com](http://docs.sylius.com).

## Installation

### Traditional
```bash
$ wget http://getcomposer.org/composer.phar
$ php composer.phar create-project sylius/sylius-standard project
$ cd project
$ yarn install
$ yarn build
$ php bin/console sylius:install
$ symfony serve
$ open http://localhost:8000/
```

For more detailed instruction about traditional way of running Sylius please visit [installation chapter in our docs](https://docs.sylius.com/the-book/sylius-ce-installation).

### Docker

You can run Sylius and all associated infrastructure dependencies (PHP, Nginx, MySQL, Node) on your machine using only Docker containers. Make sure you have installed [Docker](https://docs.docker.com/get-docker/) on your local machine.

**Option 1: Get the latest release**
```bash
LATEST=$(curl -s https://api.github.com/repos/Sylius/Sylius-Standard/releases/latest | grep '"tag_name"' | cut -d'"' -f4)
curl -L -o sylius-latest.zip https://github.com/Sylius/Sylius-Standard/archive/refs/tags/$LATEST.zip
unzip sylius-latest.zip
cd Sylius-Standard-*
```

**Option 2: List available versions**
```bash
curl -s https://api.github.com/repos/Sylius/Sylius-Standard/releases | grep '"tag_name"' | cut -d'"' -f4 | head -10
```

**Option 3: Get a specific version**
```bash
VERSION="v2.x.x"  # Replace with desired version
curl -L -o sylius-$VERSION.zip https://github.com/Sylius/Sylius-Standard/archive/refs/tags/$VERSION.zip
unzip sylius-$VERSION.zip
cd Sylius-Standard-*
```

**Initialize the project (required for all options):**
```bash
make init
```

For more detailed instruction about Docker way of running Sylius please visit [Docker installation chapter in our docs](https://docs.sylius.com/getting-started-with-sylius/sylius-ce-installation-with-docker).

## Troubleshooting

If something goes wrong, errors & exceptions are logged at the application level:

```bash
$ tail -f var/log/prod.log
$ tail -f var/log/dev.log
```

## Contributing

Would like to help us and build the most developer-friendly eCommerce framework? Start from reading our [Contribution Guide](https://docs.sylius.com/en/latest/contributing/)!

## Stay Updated

If you want to keep up with the updates, [follow the official Sylius account on Twitter](http://twitter.com/Sylius) and [like us on Facebook](https://www.facebook.com/SyliusEcommerce/).

## Bug Tracking

If you want to report a bug or suggest an idea, please use [GitHub issues](https://github.com/Sylius/Sylius/issues).

## Community Support

Get Sylius support on [Slack](https://sylius.com/slack), [Forum](https://forum.sylius.com/) or [Stack Overflow](https://stackoverflow.com/questions/tagged/sylius).

## MIT License

Sylius is completely free and released under the [MIT License](https://github.com/Sylius/Sylius/blob/master/LICENSE).

## Authors

Sylius was originally created by [Paweł Jędrzejewski](http://pjedrzejewski.com).
See the list of [contributors from our awesome community](https://github.com/Sylius/Sylius/contributors).
