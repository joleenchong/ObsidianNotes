Configuration requests to the control plan node's API server are usually in yaml or json format.

3 parts of a config file:
- metadata - name of component, etc.
- specification - component configs specific to kind of component
- status - compares desired and actual status to determine if component needs fixing -> generated automatically

YAML config format:
- strict indentation
- stored with code
