kubernetes 1 day 4
------------------

Topics

* statefulsets
* jobs
* cockroachdb
* deploy cockroachdb
* operators
* custom resources
* prometheus operator
* deploy prometheus operator and prometheus
* certified kubernetes administrator
* wrap up

statefulsets
------------

Like a Deployment, a StatefulSet manages Pods that are based on an identical container spec. Unlike a Deployment, a StatefulSet maintains a sticky identity for each of their Pods. These pods are created from the same spec, but are not interchangeable: each has a persistent identifier that it maintains across any rescheduling.

Links
* [StatefulSets](https://kubernetes.io/docs/concepts/workloads/controllers/statefulset/)

jobs
----

Job creates one or more Pods and ensures that a specified number of them successfully terminate. As pods successfully complete, the Job tracks the successful completions. When a specified number of successful completions is reached, the task (ie, Job) is complete. Deleting a Job will clean up the Pods it created.

Links
* [Jobs](https://kubernetes.io/docs/concepts/workloads/controllers/job/)

cockroachdb
-----------

CockroachDB is a distributed SQL database built on a transactional and strongly-consistent key-value store. It scales horizontally; survives disk, machine, rack, and even datacenter failures with minimal latency disruption and no manual intervention; supports strongly-consistent ACID transactions; and provides a familiar SQL API for structuring, manipulating, and querying data.

Links
* [Cockroachdb](https://www.cockroachlabs.com/)
* [FAQ](https://www.cockroachlabs.com/docs/v20.2/frequently-asked-questions)
* [Kubernetes Install Guide](https://www.cockroachlabs.com/docs/v20.2/orchestrate-cockroachdb-with-kubernetes-insecure#manual)

install cockroachdb
-------------------

make sure to create your own namespace

    oc new-project <my-name>

apply the statefulset

    oc apply -f cockroachdb-statefulset.yaml

check the pods and pvcs that the statefulset will create

    oc get pods
    oc get pvc

initialized the database with the init job

    oc apply -f cluster-init.yaml

navigate to the included route to see cockroachdb dashboard

operators
---------

Operators are software extensions to Kubernetes that make use of custom resources to manage applications and their components. Operators follow Kubernetes principles, notably the control loop.

Links
* [Operators](https://kubernetes.io/docs/concepts/extend-kubernetes/operator/)

custom resources
----------------

A resource is an endpoint in the Kubernetes API that stores a collection of API objects of a certain kind; for example, the built-in pods resource contains a collection of Pod objects.

A custom resource is an extension of the Kubernetes API that is not necessarily available in a default Kubernetes installation. It represents a customization of a particular Kubernetes installation. However, many core Kubernetes functions are now built using custom resources, making Kubernetes more modular.

Links
* [Custom Resources](https://kubernetes.io/docs/concepts/extend-kubernetes/api-extension/custom-resources/)

prometheus operator
-------------------

The Prometheus Operator provides Kubernetes native deployment and management of Prometheus and related monitoring components. The purpose of this project is to simplify and automate the configuration of a Prometheus based monitoring stack for Kubernetes clusters.

Links
* [Prometheus Operator](https://github.com/prometheus-operator/prometheus-operator)


deploy prometheus operator and prometheus
-----------------------------------------

start the operator

    oc apply -f prometheus-operator-deployment.yaml

run the prometheus crd

    oc apply -f prometheus.yaml

Navigate to the prometheus route to see prometheus running


certified kubernetes administrator
----------------------------------

The purpose of the Certified Kubernetes Administrator (CKA) program is to provide assurance that CKAs have the skills, knowledge, and competency to perform the responsibilities of Kubernetes administrators.

Links
* [CKA](https://www.cncf.io/certification/cka/)
* [Study Resources](https://ravikirans.com/cka-kubernetes-exam-study-guide/)

wrap up
-------

You have now had an opprutunity to explore all of the basis of kubernetes. Good luck and hopefully your new experiences and skills will come in handy.