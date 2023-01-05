# Overview

This document contains notes about how we contribute to and maintain **this fork** of the Namespace Node Affinity tool.  Included are a mix of details on how to work on this tool as well as how this fork differentiates from the upstream repository.

## Fork details

In general, this fork attempts to maintain everything as close to the upstream repository as possible, and to clearly separate any additions so they're easier to differentiate from actual upstream contents.  This is done to make pulling upstream's updates easier (the fewer complex merges that we need to wrangle, the better!).  This means that some content content that is not actually relevant to Canonical's fork is still kept here merely to make for easier maintenance.  For example, we likely will not use Minikube for testing, so [./scripts/Makefile](./scripts/Makefile) is not very relevant here and could be replaced with something more focused on local or Microk8s based.  Rather than editing the file directly, we'd prefer to add another Makefile (for example, `./scripts/Makefile_Canonical`) or, if we have many scripts to add, maybe a subfolder (`./scripts/_Canonical/*`) so it is easy to avoid merge conflicts.   

Although we strive to leave files as they were, a few major deviations are required:
* Canonical will handle webhook configuration/certs via a charm, so the `webhookconfig` tool (which is a small controller that handled these same functions) will not be used or maintained in this fork
* `.github`: As github will action these files, some workflows or other files here will be changed directly and likely should not follow upstream

## Developer Setup

TODO: Add notes here, including:
* how to run the test suite
* using [kubernetes webhook testers](https://github.com/ca-scribner/kubernetes-webhook-testers) to send webhook payloads during testing
