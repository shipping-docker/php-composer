## PHP-Composer

This takes the latest stable official PHP Docker image (currently `php:7.3-cli`), and adds in Git, Composer, and Zip.

This is best  used for when you do not have PHP 7+ installed on your machine, and don't want to install it. In such a case, you may run into a chicken and egg issue with [Vessel](https://vessel.shippingdocker.com) where you cannot start a new Laravel project, nor get [Vessel](https://vessel.shippingdocker.com), until you have PHP 7, but you won't have PHP 7 until you install and setup Vessel.

## Usage

To create a new Laravel project, or run any Composer command, run the following:

```bash
cd ~/Path/To/Projects

# Create a new Laravel app
docker run --rm \
    -v $(pwd):/opt \
    -w /opt \
    shippingdocker/php-composer:latest \
    composer create-project laravel/laravel my-app


# Add Vessel to that new app, or run any composer command
cd ~/Path/To/Projects/my-app

docker run --rm \
    -v $(pwd):/opt \
    -w /opt \
    shippingdocker/php-composer:latest \
    composer require shipping-docker/vessel
```

You may want to replace `$(pwd)` with your actual file path if `$(pwd)` does not correctly expand to your current working directory.

