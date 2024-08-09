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
- **Example**: "weather-forecast-ap"

#### deployment.containers.mainApp.name

- **Description**: Name of the main application container.
- **Type**: String
- **Example**: "main-app"

#### deployment.containers.mainApp.image.repository

- **Description**: Repository for the container image.
- **Type**: String
- **Example**: "docker.io/weather-forecast-ap"

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

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
