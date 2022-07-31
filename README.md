## How to run in GCP

- Step 1: you need to have an account GCP
- Step 2: enable gck, in the network, choose private. choose VPC default
- Step 3: create a cloud NAT in network service, choose VPC default
- Step 4: set up alias with file .bash_aliases with command source .bash_aliases
    ```
    #setup Aliases
    alias k='kubectl'
    alias ns='kubectl config set-context --current --namespace'
    alias kurrent='kubectl config view --minify -o "jsonpath={..namespace}" | xargs -I %s echo "Current Namespace: %s"'
    alias nodetop='k get nodes | grep Ready | cut -d" " -f1 | xargs kubectl describe node | grep -E "Name: |cpu |memory "' 
    ```
- Step 5: clone repo from git hub.
- Step 6: run command to start
    ```
    k apply -f 1.myapp-deploy.yaml
    k apply -f nginx-config-cm.yaml
    k apply -f service-demo.yaml
    k apply -f HPA-ecommerce.yaml
    ```