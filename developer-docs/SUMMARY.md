# Table of contents

* [Developer Documentation](README.md)
* [ilagent CLI](ilagent.md)

## REST API

* [API Reference](rest-api/api-reference/README.md)
  * ```yaml
    type: builtin:openapi
    props:
      models: false
    dependencies:
      spec:
        ref:
          kind: openapi
          spec: ilert-api-docs
    ```
* [API Reference v2](rest-api/api-reference-v2/README.md)
  * ```yaml
    type: builtin:openapi
    props:
      models: false
    dependencies:
      spec:
        ref:
          kind: openapi
          spec: ilert-api-docs-v2
    ```
* [Alert Source Throttle](rest-api/alertsource-throttle.md)

## Client Libraries

* [Overview](rest-api/client-libraries/README.md)
* [Go Client](rest-api/client-libraries/go-client.md)
* [JavaScript/Node.js Client](rest-api/client-libraries/javascript-node.js-client.md)
* [Rust Client](rest-api/client-libraries/rust-client.md)
* [ilagent](rest-api/client-libraries/ilagent.md)

## API Samples

* [Overview](rest-api/api-samples/README.md)
* [Creating Alerts Through Events](rest-api/api-samples/creating-alerts-through-events.md)
* [Importing Public Status Page Subscribers](rest-api/api-samples/importing-public-status-page-subscribers.md)

## API Version History

* [Overview](rest-api/api-version-history/README.md)
* [API User Preference Migration 2023](rest-api/api-version-history/api-user-preference-migration-2023.md)
* [Discontinuation of Uptime Monitoring](rest-api/api-version-history/discontinuation-of-uptime-monitoring.md)

## Developing ilert Apps

* [Overview](rest-api/developing-ilert-apps/README.md)
* [Get Started with ilert Apps](rest-api/developing-ilert-apps/get-started-with-ilert-apps.md)
* [Understanding OAuth2](rest-api/developing-ilert-apps/understanding-oauth2.md)
* [Developing a Backend App with OAuth2](rest-api/developing-ilert-apps/developing-a-backend-app-with-oauth2.md)
* [Developing a Web or Native App with OAuth2 and PKCE](rest-api/developing-ilert-apps/developing-a-web-or-native-app-with-oauth2-and-pkce.md)
* [Token Lifetimes, Error Codes, App Verification, etc.](rest-api/developing-ilert-apps/token-lifetimes-error-codes-app-verification-etc..md)

## Terraform

* [Overview](rest-api/terraform/README.md)
* [Importing ilert UI Resources into Terraform State](rest-api/terraform/importing-ilert-ui-resources-into-terraform-state.md)
