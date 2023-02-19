
Installation concluded, copy these values and store them, you'll use them later in this exercise:
-> Resource Group Name: mslearn-gh-pipelines-6901
-> ACR Name: contosocontainerregistry21267
-> ACR Login Username: contosocontainerregistry21267
-> ACR Password: 3Vrk2NrnLT0vC51rWPKLiiKHhBYxL2Ho9cyb26RDGx+ACRB11+Pw
-> AKS Cluster Name: contosocontainerregistry21267
-> AKS DNS Zone Name: e5a674ccc4214e29855a.eastus.aksapp.io

```bash
az group list -o table
az acr list -o table
```


```bash
# Get the secrets
az acr list --query "[?contains(resourceGroup, 'mslearn-gh-pipelines')].loginServer" -o table 
az acr credential show --name contosocontainerregistry21267 --query "username" -o table
az acr credential show --name contosocontainerregistry21267 --query "passwords[0].value" -o table

# Show all container images (Expectation: container published in pipeline is in the list)
az acr repository list --name contosocontainerregistry21267 -o table


git tag -a v2.0.0 -m 'First tag'
git push --tags

az acr repository show-tags --repository contoso-website --name contosocontainerregistry21267 -o table


az aks list -o tsv --query "[?name=='contoso-video'].resourceGroup"

az aks show -g mslearn-gh-pipelines-6901 -n contoso-video -o tsv --query addonProfiles.httpApplicationRouting.config.HTTPApplicationRoutingZoneName
# e5a674ccc4214e29855a.eastus.aksapp.io

az ad sp create-for-rbac --role Contributor --scopes /subscriptions/8952fcd5-b332-4df6-a491-f5bc77cff186 --sdk-auth
# Option '--sdk-auth' has been deprecated and will be removed in a future release.
# Creating 'Contributor' role assignment under scope '/subscriptions/8952fcd5-b332-4df6-a491-f5bc77cff186'
# The output includes credentials that you must protect. Be sure that you do not include these credentials 
# in your code or check the credentials into your source control. For more information, see https://aka.ms/azadsp-cli
# {
#   "clientId": "a025f684-1fc4-416a-8429-1cd886922159",
#   "clientSecret": "glL8Q~cJtBl1-sbB99_6jinsvT9D-RGweiqP7dyA",
#   "subscriptionId": "8952fcd5-b332-4df6-a491-f5bc77cff186",
#   "tenantId": "f953dcfc-5534-491a-8ff8-43ad26d258e5",
#   "activeDirectoryEndpointUrl": "https://login.microsoftonline.com",
#   "resourceManagerEndpointUrl": "https://management.azure.com/",
#   "activeDirectoryGraphResourceId": "https://graph.windows.net/",
#   "sqlManagementEndpointUrl": "https://management.core.windows.net:8443/",
#   "galleryEndpointUrl": "https://gallery.azure.com/",
#   "managementEndpointUrl": "https://management.core.windows.net/"
# }

https://helm.sh/docs/intro/install/
https://stackoverflow.com/questions/65086856/wsl2-clock-is-out-of-sync-with-windows

```

