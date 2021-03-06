# Deployments and Data-Clients

## Edge HTTP Routing

Edge HTTP routing is the first hit to your production HTTP
loadbalancer. Skipper can serve this well and reliably in production since 2016.

On the edge you want to dispatch incoming HTTP requests to your
backends, which could be a microservice architecture.

In this deployment mode you might have 100k HTTP routes, which are
used in production and modified by many parties.

To support this scenario we have the [etcd dataclient](../data-clients/etcd.md).

[Etcd](https://github.com/coreos/etcd) is a distributed database.

TODO: why we use ETCD for this purpose

## Kubernetes Ingress

[Kubernetes Ingress](http://kubernetes.io/docs/user-guide/ingress/) is the
component responsible to route traffic into your
[Kubernetes](http://kubernetes.io/) cluster.
As deployer you can define an ingress object and an ingress controller
will make sure incoming traffic gets routed to her backend service as
defined. Skipper supports this scenario with the
[Kubernetes dataclient](../data-clients/kubernetes.md) and is used in
production since end of 2016.

Skipper as ingress controller does not need to have any file
configuration or anything external which configures Skipper. Skipper
automatically finds Ingress objects and configures routes
automatically, without reloading. The only requirement is to target
all traffic you want to serve with Kubernetes to a loadbalancer pool
of Skippers. This is a clear advantage over other ingress controllers
like nginx, haproxy or envoy.

Read more about [Skipper's Kubernetes dataclient](../data-clients/kubernetes.md).

## Demos / Talks

In demos you may want to show arbitrary hello world applications.
You can easily describe html or json output on the command line with
the [route-string dataclient](../data-clients/route-string.md).

## Simple Routes File

The most static deployment that is known from apache, nginx or haproxy
is write your routes into a file and start your http server.
This is what the [Eskip file dataclient](../data-clients/eskip-file.md) is about.
