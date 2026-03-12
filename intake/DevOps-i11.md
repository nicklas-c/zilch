# DevOps Flash Reports Iteration 11

## 2026-01-16 

* Ephemerals
  * Zephyr Zero up and running
  * Data required for storefront population set up
* Incident 441 mitigation
* Upgraded DataDog agents across all clusters
* More resilient image registries via fix to pull-though cache
* Added notification to tests branch deploy to avoid re-running with wrong version
* Fix to the API Gateway deploy to allow custom integrations for product-service

## 2026-01-23

* Firefighting on incidents 446, 447, 448
* FinCrime:
  * New config and rules for 2-way messaging
* DataDog sidecar injection into Fargate pods configured centrally
* Zephyr Zero
  * Branch deploy into Zephyr Zero capability added
  * Image updater done so that Zero tracks latest in main

## 2026-01-30

* Ephemeral Environments
  * Fee & retailer data initialisation for zephyrs done
  * Config for E2E tests: tests now run, but are failing
  * Github webhook integration - will allow tracking branches
* Fraud Engine
  * S3 Schema updates automated
* Incident-449 response

## 2026-02-06

* Ephemerals:
  * ZOE MVP ready pending review by team
  * VGS routes not working, investigation concluded.  Actual fix pending
* Server-Side Rendering
  * Debugging in staging
* Continuing response on Incident-449

## 2026-02-13

* New web/Server side rendering Debugged in staging:
  * Networking issues
  * LD redirect configuration
* Ephemerals
  * VGS - service account created.  Manual set-up for Zephyr Zero.  Needs automation
  * Image updater fixed
* Fraud detection
  * Pre-prod environment set up
  * Versioning of terraform project implemented

## 2026-02-20

* Zephyr Zero:
  * Config for new services, queues, etc, since snapshot
* Deployment of Upwind into staging
  * Data transformation for fraud event - allowing filter by customer
  * Jira config and hygiene work prior to adoption of hybrid Scrum/Kanban model

## 2026-02-27

* Ability to cache base container image in github runners, some issues to work out with performance.
* ephemeral
  *  database backup and restore improvements
* Fraud
  * initial fraud AI agent deployed
* Upwind deployment to production
  * Initial work on certificate management for server side web app - crossplane deployed to dev cluster - acm
  * VGS manually set up for zephyr-zero
* new service deployment (CI/CD ready) - payout-service 
* aggregation flink-apps terraform ready
* ability to cache base container image in github runners, allows to quickly start gh runners to speed up build time of services and alike in github
* ephemeral:
  * created a new database backup from qa-sit and restoring it into zephyr-zero
  * new services added to zephyr zero
  * all other services versions updated to latest staging versions in zephyr-zero
  * VGS manually set up for zephyr-zero
* fraud:
  * initial fraud AI agent deployed
* upwind deployed to production and working
* crossplane deployed to dev cluster for server side web app certificate management

## 2026-03-06

* EWA:
  * (Payout service) Crossplane configured on Sensitive Data Env for deployment of SNS/SQS
  * Deployed RDS proxy to SDE staging and dev
  * Deployed and configured WireMock on SDE staging and dev
  * Update SDE Cluster RBAC to Grant QA Access dev and staging
  * Deployed payout-service
* Flink Apps repository and infrastructure configuration (event aggregation)
* Resolved question with AWS re shortcode for SMS
* Ephemeral Envs:
  * E2E Test config added

