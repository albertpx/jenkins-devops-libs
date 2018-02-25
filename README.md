# Jenkins DevOps Shared Libraries

A collection of Jenkins Pipeline shared libraries for common DevOps software. Usage and dependencies for each can be found in the [documentation](docs).

Unsure how to use these in your declarative syntax `Jenkinsfile`? Check the declarative Jenkinsfile shared library  [documentation](https://jenkins.io/doc/book/pipeline/shared-libraries/#using-libraries).

Additionally, you can pare down the libraries available from this repo and then load those in yourself from your own git repo or otherwise.

## Retrieve and use with Disabled Sandbox

Basically, if you have the GitHub Branch Source plugin installed, then you can [load a specific version](https://jenkins.io/doc/book/pipeline/shared-libraries/#library-versions) like:

```groovy
@Library('github.com/mschuchard/jenkins-devops-libs@version')
```

If you do not have this plugin installed, or want more flexibility over the version used, then you can use or expand upon this class:

```groovy
library identifier: 'jenkins-devops-libs@master', retriever: modernSCM(
  [$class: 'GitSCMSource',
   remote: 'https://github.com/mschuchard/jenkins-devops-libs.git'])
```

## Use with Enabled Sandbox

Basically, you need to first [add the shared library](https://jenkins.io/doc/book/pipeline/shared-libraries/#global-shared-libraries) in the Jenkins global configuration. Then, you can either load the library's methods with:

```groovy
@Library('jenkins-devops-libs@version')_
```

or using the defaults with:

```groovy
library('jenkins-devops-libs')
```

## Supported
- FaaS
- Goss
- Packer
- Terraform

## TODO
- Puppet
- Serverspec
- FaaS: invoke, push, remove
- add dgoss run
- validate yaml/json methods and use in goss/packer/faas
- Else, replace all `sh` with API where possible and abstract common methods into utils.
