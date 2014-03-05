# Broker Registrar

broker-registrar is a simple command-line tool to register service-brokers with Cloud Foundry.
It is intended to be used to perform automatic broker registration during BOSH deployments.

The tool is idempotent, and will update the url and credentials for the broker if they have
changed. Since the broker name is used to reference the broker, this cannot be changed with
this tool.

## Usage

```bash
broker-registrar register --cf-address "http://api.cf.com" --cf-username "admin" \
    --cf-password "password" --broker-name "cassandra" --broker-url "http://10.10.10.10" \
    --broker-username "admin" --broker-password "admin"
```

## Integration test setup

To run the integration tests, you will need to have access to a test Cloud
Foundry instance in which you can safely destroy spaces and organisations.

You must have two Service Brokers running in this instance, at the IPs
10.244.3.58 and 10.244.3.62. The latter is needed such that we can switch
URLs for an existing named service broker.
