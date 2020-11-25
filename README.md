# Keycloak
*Open Source Identity and Access Management for Modern Applications and Services*

## Resources
* [Homepage](https://www.keycloak.org/)
* [Documentation](https://www.keycloak.org/documentation)
* [Container Specific Documentation](https://github.com/keycloak/keycloak-containers/blob/master/server/README.md)

## kustomization
This kustomization will create the following Kubernetes Resources
* A [Namespace](https://kubernetes.io/docs/concepts/overview/working-with-objects/namespaces/) named `keycloak` in which the whole application resides.
* Resources for the main server backend:
    * A [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) + [Service](https://kubernetes.io/docs/concepts/services-networking/service/) both named `keycloak`.
    * An example [ConfigMap](https://kubernetes.io/docs/concepts/configuration/configmap/) + [Secret](https://kubernetes.io/docs/concepts/configuration/secret/) both named `keycloak`.
* Resources for the database:
    * A [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) + [Service](https://kubernetes.io/docs/concepts/services-networking/service/) both named `keycloak-postgres`.
    * A [PersistentVolumeClaim](https://kubernetes.io/docs/concepts/storage/persistent-volumes/) named `keycloak-postgres` in which the database is persisted.
    * An example [ConfigMap](https://kubernetes.io/docs/concepts/configuration/configmap/) + [Secret](https://kubernetes.io/docs/concepts/configuration/secret/) both named `keycloak-postgres`.

## Configuration
The application can be configured by overwriting the ConfigMap *dex-server*s key *config.yml* with a valid Dex
configuration file. 
This file can have references to environment variables via `$KEY` syntax.
In addition the Secret *dex-server* serves as a provider for the servers environment.
