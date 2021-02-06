# operator-jenkins-config

This is dependent on the [Red Hat Jenkins Operator](https://github.com/jenkinsci/jenkins-automation-operator/) 
being installed on an OpenShift 4.x cluster

# JCasC

Jenkins Configration as Code (JCasC) is used to configure Jenkins automatically to a desired state.  YAML, greoovy, and seed jobs are supported.
More information can be found [configuration-as-code-plugin](https://github.com/jenkinsci/configuration-as-code-plugin)

`oc create -f ./app-sre-jcasc.yaml`

## app-sre-jcasc.yaml - configmap

This is the custom AppSRE Jenkins customizations used by the JCasC plugin to install a custom configuration via a configmap.

`oc create -f ./app-sre-podtemplates.yaml`
## app-sre-podtemplates.yaml - configmap

This was required in our case to run a groovy script post
app-sre-jcasc.yaml configmap to load an additional app-interface
podtemplate via a configmap and point to the https://quay.io/repository/arilivigni/app-sre-jenkins-agent quay.io image that has buldah and jenkins slave
components installed.

# app-sre-jenkins.yaml - Jenkins Deployment

This is the main deployment and can be installed in the UI through the Jenkins operator using `oc`.

`oc create -f ./app-sre-jenkins.yaml`


