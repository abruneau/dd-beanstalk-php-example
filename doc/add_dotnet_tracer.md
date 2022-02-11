# Adding .Net tracer

When the application isn’t containerized and the Datadog Agent is configured with `99datadog.config`, tracing is enabled without any additional configuration.

To install the tracer, the following lines need to be added to `99datadog.config` in a new `/install_apm.sh` section

```sh
tracer_version=0.69.0

# Check if a tracer is already installed
if rpm -q datadog-php-tracer &>/dev/null; then

    # compare version to know if it needs to be reinstalled
    version=$(yum info datadog-php-tracer | grep "Version" | awk '{print $3}')
    if [ "$tracer_version" != "$version" ]; then
        # remove previous tracer
        rpm -e datadog-php-tracer

        # download the new tracer
        wget -O /datadog/datadog-php-tracer.rpm https://github.com/DataDog/dd-trace-php/releases/download/$tracer_version/datadog-php-tracer-$tracer_version-1.x86_64.rpm

        # Install the tracer for PHP-FPM
        DD_TRACE_PHP_BIN=$(which php-fpm) rpm -ivh /datadog/datadog-php-tracer.rpm
    fi
else
    # download the new tracer
    wget -O /datadog/datadog-php-tracer.rpm https://github.com/DataDog/dd-trace-php/releases/download/$tracer_version/datadog-php-tracer-$tracer_version-1.x86_64.rpm

    # Install the tracer for PHP-FPM
    DD_TRACE_PHP_BIN=$(which php-fpm) rpm -ivh /datadog/datadog-php-tracer.rpm
fi

# Add unified service tags to the application
echo -e "\nenv[DD_SERVICE] = beanstalk-demo" >> /etc/php-fpm.d/www.conf
echo "env[DD_ENV] = demo" >> /etc/php-fpm.d/www.conf
echo "env[DD_version] = 1.0.0" >> /etc/php-fpm.d/www.conf

# restart the application for apm to work
systemctl restart php-fpm
```

And then add it to the list of container commands

```yaml
container_commands:
    ...
    07setup_apm:
        command: "/install_apm.sh"
```