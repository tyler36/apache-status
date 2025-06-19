# Apache web server <!-- omit in docs -->

## Overview

This project is a basic DDEV apache webserver setup.
It is designed to be used as a playground.

## Server status

1. Ensure `status` module is enabled

    ```shell
    # Enable module
    a2enmod status

    # List all modules
    a2query -m
    ```

2. Add endpoint

    ```conf
    Listen 8080

    <VirtualHost *:8080>
        DocumentRoot /var/www/html

        <Location "/server-status">
            SetHandler server-status
            Require all granted
        </Location>

        # Optional: Logging
        ErrorLog /var/log/apache2/server-status-error.log
        CustomLog /var/log/apache2/server-status-access.log combined
    </VirtualHost>
    ```

3. Restart Apache to apply changes.

    ```shell
    sudo service apache2 restart
    ```

4. Visit `:8080/server-status` to see status data.
