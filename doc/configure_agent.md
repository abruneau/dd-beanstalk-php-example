# Configuring the Datadog agent

To enable agent feature, some files need to be modified. 

This is done in `99datadog.config` file in the `/configure_datadog_yaml.sh` section

## Enabling Logs

To enable log collection, `datadog.yaml` needs to be modified. 

```sh
echo -e "logs_enabled: true" >> /etc/datadog-agent/datadog.yaml
```

## Enabling NPM

```sh
echo -e "network_config:\n  enabled: \"true\"\n" > /etc/datadog-agent/system-probe.yaml
```

## Enabling Datadog Process Agent

```sh
echo -e "process_config:\n  enabled: \"true\"\n" >> /etc/datadog-agent/datadog.yaml
```

# Configuring integrations

Although it is possible to copy example conf files and edit them with `sed`, it is not very practical.

Instead, you ca create a directory where you store your config files and copy them in Datadog `config.d` directory

In this example, I created a `ddagent` directory containing configs for NGINX and PHP-FPM.

As the application directory isn't always easy to find, you can add a container command to move this directory in a well known location.

```yaml
container_commands:
    ...
    05load_config_datadog:
        command: "chown -R dd-agent:dd-agent ddagent &&  rsync -av --delete ddagent/config.d/* /etc/datadog-agent/conf.d/"
```