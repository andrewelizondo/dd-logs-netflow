## Purpose
Show an example of using fluentd as a collector of netflow traffic and output them to datadog using logs

Theres's a docker-compose file in this repo to set up a small proof of concept, it uses the [fluent-plugin-netflow](https://github.com/repeatedly/fluent-plugin-netflow) plugin to output all inbound netflow traffic on 4729 over to [datadog](https://github.com/DataDog/fluent-plugin-datadog). There is also a generator service constantly generating data using [NetFlow-Generator](https://github.com/mshindo/NetFlow-Generator)

## Getting Started
Just export your [api key](https://app.datadoghq.com/account/settings#api) and docker-compose takes care of the rest
  ```
  $ export DD_API_KEY=your-datadog-api-key
  $ docker-compose up
  ```
