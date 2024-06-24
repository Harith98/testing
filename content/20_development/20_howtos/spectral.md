# Spectral

## Usage

```bash
echo 'extends: ["spectral:oas", "spectral:asyncapi"]' > .spectral.yaml

spectral lint myapifile.yaml

cd {api-folder}

spectral lint api.json --ruleset ../.spectral.yaml

spectral lint myapifile.yaml --ruleset ../.spectral.yaml --fail-severity=warn

spectral lint api.json --ruleset ../spectral-kebab-ruleset.yaml 
```

## Extending rulesets

spectral-kebab-ruleset.yaml

```yaml
extends: ["spectral:oas", "spectral:asyncapi"]

rules:
  paths-kebab-case:
    description: Paths should be kebab-case.
    message: "{{property}} should be kebab-case (lower-case and separated with hyphens)"
    severity: warn
    given: $.paths[*]~
    then:
      function: pattern
      functionOptions:
        match: "^(\/|[a-z0-9-.]+|{[a-zA-Z0-9_]+})+$"
```

## OpenAPI Tags

[Operation must have tags](operation-must-have-tags.png)

[OpenAPI tags](https://swagger.io/docs/specification/grouping-operations-with-tags/)  

## Links

[Homepage](https://stoplight.io/open-source/spectral)  
[Documentation](https://stoplight.io/open-source/spectral)  
[Rulesets](https://github.com/stoplightio/spectral-rulesets)  
[Create custom ruleset](https://meta.stoplight.io/docs/spectral/01baf06bdd05a-create-a-ruleset)  
[VS Code plugin](https://marketplace.visualstudio.com/items?itemName=stoplight.spectral)  
[Git Actions](https://github.com/stoplightio/spectral-action)  
