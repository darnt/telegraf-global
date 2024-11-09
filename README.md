# telegraf-global

Basic telegraf configuration



Steps

Setup secrets using systemd secretstores plugin (https://github.com/influxdata/telegraf/tree/master/plugins/secretstores/systemd)

`systemd-ask-password -n | sudo systemd-creds encrypt --name=  - /etc/credstore.encrypted/telegraf.influx_token_hosts`

For systemd < v254 you need to provide an empty name to make it compatible.

For systemd version between v250 and v254 you need to specify the credentials using `LoadCredentialEncrypted` in a service-override. 

In `/lib/systemd/system/telegraf.service` add under Service

`LoadCredentialEncrypted=telegraf.influx_token_hosts`

URL can be configured in `/etc/default/telegraf` with

`INFLUX_URL="https://myinfluxdbserver.com"`




