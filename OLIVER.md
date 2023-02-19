
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

az aks show -g mslearn-gh-pipelines-6901 -n contoso-video -o tsv --query addonProfiles.httpApplicationRouting.config.HTTPApplicationRoutingZoneName

https://helm.sh/docs/intro/install/
https://stackoverflow.com/questions/65086856/wsl2-clock-is-out-of-sync-with-windows

```