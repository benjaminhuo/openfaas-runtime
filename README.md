## Openfaas runtimes to deploy knative services

This repository contains knative buildtemplates with [OpenFaaS](https://github.com/openfaas) runtimes.

Most convenient way to work with knative objects and test this runtimes is [tm CLI](https://github.com/triggermesh/tm)

Once you have tm CLI installed, you can deploy openfaas go runtime by executing:

```
tm deploy buildtemplate --from-url https://raw.githubusercontent.com/triggermesh/openfaas-runtime/master/go/openfaas-go-runtime.yaml
```

And then you can deploy any go code within one command, for example:

```
tm deploy service hello-go --from-source https://github.com/golang/example --build-template openfaas-go-runtime --build-argument DIRECTORY=hello
```  

In a minute you can check service status and domain:

```
tm describe service hello-go
```

Depending on DNS and Ingress setup you should be able to access your function either from Internet or by editing `/etc/hosts` file:

```
curl hello-go.default.example.com

Hello, Go examples!
```
 

### Support

We would love your feedback on these Openfaas knative templates so don't hesitate to let us know what is wrong and how we could improve it, just file an [issue](https://github.com/triggermesh/tm/issues/new)

### Code of Conduct

These templates are by no means part of [CNCF](https://www.cncf.io/) but we abide by its [code of conduct](https://github.com/cncf/foundation/blob/master/code-of-conduct.md)
