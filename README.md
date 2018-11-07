## Openfaas runtimes to deploy knative services

This repository contains knative buildtemplates with [OpenFaaS](https://github.com/openfaas) runtimes.

Most convenient way to work with knative objects and test this runtimes is [tm CLI](https://github.com/triggermesh/tm)

Once you have tm CLI installed, you can install openfaas runtimes and start deploying your code.

#### Golang example

Install golang openfaas runtime:

```
$ tm deploy buildtemplate --from-url https://raw.githubusercontent.com/triggermesh/openfaas-runtime/master/go/openfaas-go-runtime.yaml
Downloading build template definition
Creating "openfaas-go-runtime" build template
```

and now you can deploy any go code within one command, for example:

```
$ tm deploy service hello-go --from-source https://github.com/golang/example --build-template openfaas-go-runtime --build-argument DIRECTORY=hello --wait
Deployment started. Run "tm -n default describe service hello-go" to see the details
Waiting for ready state........
Service domain: hello-go.default.example.com
```

Depending on DNS and Ingress setup you should be able to access your function either from Internet or by editing `/etc/hosts` file:

```
$ curl hello-go.default.example.com
Hello, Go examples!
```

#### Python example

Install python 2.7 openfaas runtime:

```
$ tm deploy buildtemplate --from-url https://raw.githubusercontent.com/triggermesh/openfaas-runtime/master/python2.7/openfaas-python2.7-runtime.yaml
Downloading build template definition
Creating "openfaas-python27-runtime" build template
```

Deploy code:

```
$ tm deploy service hello-python --from-source https://github.com/geekcomputers/Python --build-template openfaas-python27-runtime --build-argument HANDLER=helloworld.py --wait
Deployment started. Run "tm -n default describe service hello-python" to see the details
Waiting for ready state........
Service domain: hello-python.default.example.com

$ curl hello-python.default.example.com
Hello World!
```

### Support

We would love your feedback on these Openfaas knative templates so don't hesitate to let us know what is wrong and how we could improve it, just file an [issue](https://github.com/triggermesh/openfaas-runtime/issues/new)

### Code of Conduct

These templates are by no means part of [CNCF](https://www.cncf.io/) but we abide by its [code of conduct](https://github.com/cncf/foundation/blob/master/code-of-conduct.md)
