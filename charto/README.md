# Helm 2 Merge debugging

Repro attempt:
- Start with helm chart with .Values.resources.limits.cpu set, also
  include a default in the chart template.
- Install the chart, should use the limit from .Values.resources.limits.cpu
- Remove .Values.resources.limits.cpu (leave limits defined as empty map
  or helm will fail the rollout). This will use the default limit.
- Define .Values.resource.limits.cpu as either "0", 0 (number,
  unquoted), or as "" (the empty string, quoted). The default will be
  applied as the limit
