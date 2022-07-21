FROM drupal:9-php7.4

# Install packages.
RUN apt-get update && apt-get install -y \
  zlib1g-dev \
  libssl-dev \
  mariadb-client \
  curl \
  wget \
  git \
  msmtp \
  libzip-dev \
  nano \
  p7zip-full \
  vim && \
  apt-get clean

# Install extensions
RUN docker-php-ext-install zip bcmath exif sockets

# Install Open Social via composer.
RUN \
  unlink /var/www/html && \
  rm -rf /opt/drupal
WORKDIR /var/www
RUN \
  composer create-project goalgorilla/social_template:dev-master ./ --no-interaction && \
  chown -R www-data:www-data *

# Fix shell.
RUN echo "export TERM=xterm" >> ~/.bashrc
