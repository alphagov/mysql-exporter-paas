## mysql-exporter-paas

A GOV.UK PaaS application that exports MySQL metrics to Prometheus.

## Overview

This is a tiny application that can be deployed into a GOV.UK PaaS space to
expose metrics for MySQL databases backing other applications in that space.
This includes metrics such as number of active connections and the rate of
transactions. These metrics are useful to expose to developers so they can
diagnose problems and understand how their backing databases cope with traffic.

## Setup

1. Clone this repository
2. Set a name in `manifest.yml`, for example `mysql-exporter-my-app`
3. Run `cf services` to find the name of your mysql database
4. Change `rails-mysql` in `manifest.yml` to your database name
5. Run `cf push` to deploy the exporter to your space
6. Visit the [MySQL dashboard](https://grafana-paas.cloudapps.digital/d/YJsEPTgmk/mysql) in Grafana
7. Select your exporter's name from the dropdown menu (top-left of the screen)

It can take up to 5 minutes for your exporter to appear in the dropdown menu.

## Custom Queries

Unlike the [Postgres exporter](https://github.com/alphagov/postgres-exporter-paas),
this one doesn't support custom queries, unfortunately.
