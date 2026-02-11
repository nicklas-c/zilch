# Summaries and transcripts from slack on the morning of Wednesday 11th Feb 2026.

## proj-visa-flex channel summary

Visa Flex Implementation
@Saurabh Raman provided an overview of the proposed changes for Visa Flex, including removing certain checks on the secondary credential and relying on Zilch to return the correct public token. They also discussed changes to XML reporting and clearing.

Merchant Affiliate Status
@Andrea Ponte led a discussion on defining and managing the merchant affiliate status, which is a key requirement for Visa Flex. They outlined current assumptions and key outstanding questions to be answered by the relevant teams.

Issuer Team Considerations
@Derek McCallum raised an interesting question on whether the issuer team needs to issue a separate commercial card for each customer, or if they could use a single commercial card for all customers, since Visa does not seem to care about the specific secondary credential as long as it is of the right type.

Tracking Visa Flex Progress
@Tomasz Surowiec created a JIRA initiative to track Visa Flex epics across different teams, and @michael.charash initiated a deep dive into the potential customer experience impact of the Visa Flex launch.

Merchant List Management
@Abhishek Chatterjee and @Sam discussed the approach to maintaining the list of merchants eligible for Visa Flex, including the need to decouple the sales relationship from the Visa Flex eligibility.

## frontend-ssr-project summary

### Configuring the Argo AppSet for Customer Web App
@Chris Walker and the team discussed splitting the Argo AppSet for the customer web app into a more specific one for the legacy monorepo and a more generic one for the new SSR approach.
#### More details
* @Chris Walker mentioned the need to create a specific Argo AppSet for the legacy monorepo and a more generic one for the new SSR approach [1]
* @Chris Walker suggested swapping the customer web app from the existing monorepo AppSet to the new one, as the server-side approach will likely be the norm going forward [2]
* @Chris Walker noted that the existing exclusions for the mobile app and scripts directory may no longer be needed [3]

### Configuring the Docker Image Repository and Tags
@Chris Walker and the team worked on setting up the Docker image repository and tags for the customer web app, including handling the case where the image already exists in the ECR.
#### More details
* @Chris Walker provided an example of how the Docker image repository and tag should be configured in the Argo AppSet [4]
* @Chris Walker mentioned that they were pushing the image with a specific tag and hash, but the AppSet was looking for a different tag [5]
* @Phil Stevenson shared annotations that can be used to configure the Argo image updater [6]

### Troubleshooting Docker Image Pushes
@Chris Walker and the team encountered issues with pushing the Docker image to the repository, including the repository not existing and insufficient permissions. They worked to resolve these issues.
#### More details
* @Phil Stevenson encountered an issue where the Docker image could not be pulled due to authentication errors [7]
* @Phil Stevenson provided an example of how to check if a Docker image already exists in the registry before attempting to push it [8]
* @Chris Walker encountered issues with the repository not existing and insufficient permissions when trying to push the Docker image [9], [10], [11]

### Configuring AWS ALB Ingress for the Customer Web App
@Nick Gilbert and the team worked on adding AWS ALB ingress templating for the customer web app to enable dynamic domain generation and improved health check configuration.
#### More details
* @Nick Gilbert updated the destination for the frontend server AppSet [12]
* @Nick Gilbert fixed an issue with the Argo path variable [13]
* @Nick Gilbert added ingress templating for the customer web app to enable dynamic domain generation and improved health check configuration [14]

### Configuring Environment Variables and Secrets
@Chris Walker and the team discussed how to handle environment variables and secrets, including using AWS Secrets Manager, Helm values, and external secrets.
#### More details
* @Chris Walker and the team discussed how to handle environment variables and secrets, including using AWS Secrets Manager, Helm values, and external secrets [15], [16], [17], [18], [19], [20], [21], [22]
* @Nick Gilbert and @Phil Stevenson provided examples of how to use external secrets to fetch secrets from AWS Secrets Manager [23], [24], [25], [26]

### Deploying the Customer Web App to Staging and Production
@Chris Walker and the team discussed the effort involved in deploying the customer web app to staging and production, ensuring the staging environment is as close to production as possible.
#### More details
* @Chris Walker requested that the customer web app AppSet be updated to point to the main branch [27]
* @Nick Gilbert made corrections to the staging AppSet for the customer web app [28]
* @Nick Gilbert and @Chris Walker discussed the effort involved in deploying the customer web app to staging and production, ensuring the staging environment is as close to production as possible [29], [30], [31], [32]

