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

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
