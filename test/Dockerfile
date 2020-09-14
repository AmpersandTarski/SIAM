FROM ampersandtarski/prototype-framework:development

# Copy SIAM module
COPY src/ /usr/local/project/SIAM/

# Put SIAM templates in right folder
COPY src/templates/ /usr/local/project/templates/

# Copy SIAM test project files
COPY test/ /usr/local/project/

# Generate prototype application from folder
RUN ampersand proto /usr/local/project/SIAMv4.adl \
      --proto-dir /var/www \
      --verbose \
      --ignore-invariant-violations

COPY test/customizations/ /var/www/

RUN chown -R www-data:www-data /var/www/log /var/www/data /var/www/generics \
 && cd /var/www \
 # uncomment lines below if customizations are added to default prototype framework
 # && composer install --prefer-dist --no-dev --optimize-autoloader --profile \
 # && npm install \
 # && gulp build-ampersand \
 && gulp build-project