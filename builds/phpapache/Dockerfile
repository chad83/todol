FROM php:apache

# Get basic dependecies.
RUN apt-get update -y && apt-get install zip unzip wget git -y

# Install Composer.
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" && \
 php composer-setup.php && \
 php -r "unlink('composer-setup.php');" && \
 mv composer.phar /usr/local/bin/composer

# Install Symphony CLI.
RUN wget https://get.symfony.com/cli/installer -O - | bash && mv /root/.symfony/bin/symfony /usr/local/bin/symfony


# PHP Dependencies.
RUN docker-php-ext-install pdo_mysql

WORKDIR /var/www/html/

CMD symfony server:start