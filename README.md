# hermes-catalog

ZDR-filtered model catalog manifest for Hermes Agent deployments that must
only use EU endpoints with zero data retention.

Every model in this manifest was tested live against
`https://eu.openrouter.ai/api/v1` (chat completions with the org token) and
passed the account's ZDR/guardrail policy. Models that are listed on the EU
endpoint but excluded at request time (e.g. `anthropic/claude-fable-5`,
whose only deployment violates ZDR) are omitted.

## Usage

In Hermes' `config.yaml` (HERMES_HOME):

```yaml
model_catalog:
  url: https://raw.githubusercontent.com/MarkArts/hermes-catalog/main/model-catalog.json
```

The model picker then only lists these models. Re-test when new models
appear on the EU endpoint.
