pipeline {
    agent any

    environment {
        AZURE_SUBSCRIPTION_ID='4917809c-4753-4722-81bf-a1b4429fd9ca'
        AZURE_TENANT_ID='819948b9-e473-435d-b429-6f100444732f'
        CONTAINER_REGISTRY='cptdockerregistry'
        RESOURCE_GROUP='Docker-Demo-RG'
        REPO="https://github.com/vijishankar/simple-docker-image.git"
        IMAGE_NAME="hello-world-image"
        TAG="cptdockerregistry.azurecr.io/hello-world-image:1.1"
    }

    stages {
        stage('Example') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'd56220d8-aa01-4bad-ae20-1ddd51e275a5', passwordVariable: 'z81gDx8hdH1CWb4RMR-6RY3t3.hhvoLaTQ', usernameVariable: 'd56220d8-aa01-4bad-ae20-1ddd51e275a5')]) {
                            sh 'az login --service-principal -u $AZURE_CLIENT_ID -p $AZURE_CLIENT_SECRET -t $AZURE_TENANT_ID'
                            sh 'az account set -s $AZURE_SUBSCRIPTION_ID'
                            sh 'az acr login --name $CONTAINER_REGISTRY --resource-group $RESOURCE_GROUP'
                            sh 'az acr build --image $REPO/$IMAGE_NAME:$TAG --registry $CONTAINER_REGISTRY --file Dockerfile . '
                        }
            }
        }
    }
}
