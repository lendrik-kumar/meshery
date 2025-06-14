---
layout: default
title: Meshery Adapter for Traefik Mesh
name: Meshery Adapter for Traefik Mesh
component: Traefik Mesh
earliest_version: v1.0
port: 10006/gRPC
project_status: stable
lab: traefik-meshery-adapter
github_link: https://github.com/meshery/meshery-traefik-mesh
image: /assets/img/service-meshes/traefik-mesh.svg
white_image: /assets/img/service-meshes/traefik-mesh.svg
permalink: extensibility/adapters/traefik-mesh
redirect_from: service-meshes/adapters/traefik-mesh
language: en
---

{% assign sorted_tests_group = site.compatibility | group_by: "meshery-component" %}
{% for group in sorted_tests_group %}
      {% if group.name == "meshery-traefik-mesh" %}
        {% assign items = group.items | sort: "meshery-component-version" | reverse %}
        {% for item in items %}
          {% if item.meshery-component-version != "edge" %}
            {% if item.overall-status == "passing" %}
              {% assign adapter_version_dynamic = item.meshery-component-version %}
              {% break %}
            {% elsif item.overall-status == "failing" %}
              {% continue %}
            {% endif %}
          {% endif %}
        {% endfor %} 
      {% endif %}
{% endfor %}

{% include compatibility/adapter-status.html %}



## Lifecycle management

The {{page.name}} can install **{{page.earliest_version}}** of {{page.component}}. A number of sample applications can be installed using the {{page.name}}.

Want to contribute? Check our [progress]({{page.github_link}}).

### Sample Applications

The {{ page.name }} includes some sample applications operations. Meshery can be used to deploy any of these sample applications.

- [Bookinfo]({{site.baseurl}}/guides/infrastructure-management/sample-apps)
  - Follow this [tutorial workshop](https://github.com/layer5io/istio-service-mesh-workshop/blob/master/lab-2/README.md) to set up and deploy the BookInfo sample app on Istio using Meshery.
- [Httpbin]({{site.baseurl}}/guides/infrastructure-management/sample-apps)
  - Httpbin is a simple HTTP request and response service.

## Suggested Topics

- Examine [Meshery's architecture]({{ site.baseurl }}/architecture) and how adapters fit in as a component.
- Learn more about [Meshery Adapters]({{ site.baseurl }}/architecture/adapters).
