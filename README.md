# one-press-chart

## Overview

This project is designed to provide the chart support deploy a containerized application in CICD processor by Helm.

## Table of Contents

- [Installation](#installation)
- [Usage](#usage)
- [Modules](#modules)
- [Contributing](#contributing)
- [License](#license)

## Installation

## Usage

Follow the bash script to execute the chart.

```bash
helm upgrade --install --wait --force <DEPLOYMENT_APP> <CHART_PATH> \
-f <DEPLOYMENT_APP_RESOURCE_PATH>/<BASE_ENV>/values.yaml \
-f <DEPLOYMENT_APP_RESOURCE_PATH>/<SPECIFIC_ENV>/values.yaml \
--set deployment.containers.mainApp.image.repository=<DOCKER_SERVER_URI>/<IMAGE_NAME> \
--set deployment.containers.mainApp.image.tag=<IMAGE_TAG> \
--set deployment.containers.mainApp.env.common.<NON_SECURE_ENV1>=<NON_SECURE_ENV1_VALUE> \
--set deployment.containers.mainApp.env.common.<NON_SECURE_ENV2>=<NON_SECURE_ENV2_VALUE> \
--set deployment.containers.mainApp.env.secret.<SECURE_ENV1>=<SECURE_ENV1_VALUE> \
--set deployment.containers.mainApp.env.secret.<SECURE_ENV2>=<SECURE_ENV2_VALUE>
```

Example:

```bash

```

## Modules

Show detail of components in the chart.

### Structure when compile.

The time when you either pull or package it in Helm registry.

```bash
one-press-chart
├── Chart.yaml
├── LICENSE
├── README.md
├── deploy.yaml
├── templates
│   ├── NOTES.txt
│   ├── _helpers.tpl
│   ├── configmap.yaml
│   ├── deployment.yaml
│   ├── hpa.yaml
│   ├── ingress.yaml
│   ├── secret.yaml
│   ├── service.yaml
│   ├── serviceaccount.yaml
│   └── tests
│       └── test-connection.yaml
└── values.yaml

3 directories, 15 files
```

### Structure when runtime.

The time when you execute it.

```bash
one-press-chart
├── Chart.yaml
├── LICENSE
├── README.md
├── deploy.yaml
├── resources
│   ├── configmap
│   │   ├── nginx.conf
│   │   └── report.csv
│   └── secret
│       ├── application-uat.properties
│       ├── appsettings.json
│       └── cred.pem
├── templates
│   ├── NOTES.txt
│   ├── _helpers.tpl
│   ├── configmap.yaml
│   ├── deployment.yaml
│   ├── hpa.yaml
│   ├── ingress.yaml
│   ├── secret.yaml
│   ├── service.yaml
│   ├── serviceaccount.yaml
│   └── tests
│       └── test-connection.yaml
└── values.yaml

6 directories, 20 files
```

### Values.yaml's properties

This document provides detailed descriptions for the properties defined in the `values.yaml` file.

#### replicaCount

- **Description**: Number of replicas for the deployment.
- **Type**: Integer
- **Example**: 1

#### nameOverride

- **Description**: Override the name of the application.
- **Type**: String
- **Example**: ""

#### fullnameOverride

- **Description**: Override the full name of the application.
- **Type**: String
- **Example**: "weather-forecast-api"

#### deployment.containers.mainApp.name

- **Description**: Name of the main application container.
- **Type**: String
- **Example**: "main-app"

#### deployment.containers.mainApp.image.repository

- **Description**: Repository for the container image.
- **Type**: String
- **Example**: "docker.io/weather-forecast-api"

#### deployment.containers.mainApp.image.tag

- **Description**: Tag for the container image.
- **Type**: String
- **Example**: "latest"

#### deployment.containers.mainApp.image.imagePullPolicy

- **Description**: Image pull policy.
- **Type**: String
- **Example**: "Always"

#### deployment.containers.mainApp.ports

- **Description**: List of ports exposed by the container.
- **Type**: List of objects
- **Example**:
  ```yaml
  - name: http
    containerPort: 8080
    protocol: TCP
  ```

#### deployment.containers.mainApp.env.common

- **Description**: Common environment variables
- **Type**: Dict of objects
- **Example**:
  ```yaml
  BUILD_NUMBER: <BUILD_NUMBER>
  GIT_COMMIT_ID: <GIT_COMMIT_ID>
  GIT_SHORT_COMMIT_ID: <GIT_SHORT_COMMIT_ID>
  GIT_URL: <GIT_URL>
  PIPELINE_NAME: <PIPELINE_NAME>
  ```

#### deployment.containers.mainApp.env.secret

- **Description**: Secret environment variables
- **Type**: Dict of objects
- **Example**:
  ```yaml
  SECRET_WEATHER_FORECAST_API_VAULT_CLIENT_ID=<SECRET_WEATHER_FORECAST_API_VAULT_CLIENT_ID>
  SECRET_WEATHER_FORECAST_API_VAULT_CLIENT_SECRET=<SECRET_WEATHER_FORECAST_API_VAULT_CLIENT_SECRET>
  SECRET_WEATHER_FORECAST_API_VAULT_TENANT_ID=<SECRET_WEATHER_FORECAST_API_VAULT_TENANT_ID>
  SECRET_WEATHER_FORECAST_API_VAULT_URL=<SECRET_WEATHER_FORECAST_API_VAULT_URL>
  ```

#### deployment.containers.mainApp.readinessProbe.httpGet.path

- **Description**: Path for the readiness probe.
- **Type**: String
- **Example**: "/version"

#### deployment.containers.mainApp.readinessProbe.httpGet.port

- **Description**: Port for the readiness probe.
- **Type**: Integer
- **Example**: 8080

#### deployment.containers.mainApp.readinessProbe.initialDelaySeconds

- **Description**: Initial delay before the readiness probe starts.
- **Type**: Integer
- **Example**: 45

#### deployment.containers.mainApp.readinessProbe.periodSeconds

- **Description**: Period between readiness probes.
- **Type**: Integer
- **Example**: 60

#### deployment.containers.mainApp.readinessProbe.timeoutSeconds

- **Description**: Timeout for the readiness probe.
- **Type**: Integer
- **Example**: 10

#### deployment.containers.mainApp.readinessProbe.failureThreshold

- **Description**: Number of consecutive failures for the probe to be considered failed.
- **Type**: Integer
- **Example**: 3

#### deployment.containers.mainApp.readinessProbe.successThreshold

- **Description**: Number of consecutive successes for the probe to be considered successful after having failed.
- **Type**: Integer
- **Example**: 1

#### deployment.containers.mainApp.livenessProbe.httpGet

- **Description**: HTTP GET action for the liveness probe.
- **Type**: Object
- **Example**: Not specified in the provided excerpt.

```

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
```
