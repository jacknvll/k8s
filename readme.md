# Summary

This project is a learning repository as I follow a Udemy course with a syllabus on par with the "Certified Kubernetes Administrator" (CTA) certificate.

# Tool Alias
Sometimes writing ```kubectl``` all the time can be burdensome. You could also setup an 'alias' to shorten the command to something quicker to type.

For example: `alias k="kubectl"`

Now you only need to type ```k``` to execute the *kubectl* tool.

# Helpful Commands
Get list of resources: ```k get resource-type```

Only use this to create pods: 
``` k run nginx --image=nginx ```

Otherwise its: ```k create ...```

Open configuration with an editor:
``` vim config.yml```. Save changes with `:wq`

Apply changes made in a config file: `k apply -f config.yml`

Delete pod by name: `k delete pod redis123`

Shows the Node for each Pod: `k get pods -o wide`

See all properties & events of a resource: `k describe pod nginx`. This is helpful to identify "why" a Pod is not in a Running state.

# Deployments Inline & Configurations
You can create resources directly on the CLI terminal and let the tool generate the YAML configuration file for you. This can be a quicker solution than writing out a whole config file.
```
k create deployment httpd-frontend --image=httpd:2.4-alpine --replicas=33 -o yaml > httpd-deployment.yaml
```
Alternatively, you can create the configuration without deploying the resource/s, allowing further modification within the configuration file. Known as a ```dry-run```.
```
k create deployment httpd-frontend --image=httpd:2.4-alpine --replicas=33 --dry-run=client -o yaml > httpd-deployment.yaml
```