# Awesome OpenAI-Compatible [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> Where OpenAI-compatible APIs differ: provider compatibility notes, self-hosted servers, translation layers, conformance tests and reliability data.

Many providers say their API is "OpenAI-compatible." In practice, parameters get ignored, rejected or renamed, reasoning output appears in different fields, and token usage is reported in different places. This list links each provider's own documentation of those differences, plus tools that test and measure them. Each entry describes what the linked page documents; it is not a ranking.

## Contents

- [Provider Compatibility Notes](#provider-compatibility-notes)
- [Self-Hosted Servers](#self-hosted-servers)
- [Translation Layers and SDKs](#translation-layers-and-sdks)
- [Conformance and Testing](#conformance-and-testing)
- [Trackers and Data](#trackers-and-data)

## Provider Compatibility Notes

- [Alibaba Cloud Model Studio](https://www.alibabacloud.com/help/en/model-studio/compatibility-of-openai-with-dashscope) - Region-specific compatible-mode base URLs, region-bound API keys, and a note that `tools` cannot be combined with `stream=True`.
- [Anthropic](https://platform.claude.com/docs/en/api/openai-sdk) - Field-by-field support table: `reasoning_effort`, `seed` and `logprobs` are ignored, `n` must be 1, `response_format` accepts only strict `json_schema`, and `usage` detail objects are always empty.
- [Cerebras](https://inference-docs.cerebras.ai/resources/openai) - Documents `n: 1` only, model-dependent `prediction` and `service_tier`, and models that reject `tools` together with `response_format`.
- [DeepSeek](https://api-docs.deepseek.com/guides/thinking_mode) - Thinking mode is toggled with a `thinking` object, ignores `temperature` and penalties, and requires `reasoning_content` to be passed back in later requests when tools are used.
- [Fireworks AI](https://docs.fireworks.ai/tools-sdks/openai-compatibility) - Lowers `max_tokens` instead of returning an error when the context is exceeded, and returns streaming usage in the last chunk.
- [Google Gemini](https://aistudio.google.com/docs/openai) - Maps `reasoning_effort` to thinking levels or budgets per model, exposes Gemini-only options through `extra_body`, and labels OpenAI library support as beta.
- [GreenNode MaaS](https://docs.greennode.ai/ai-stack/agent-base/ai-coding/connect-openai-compatible-to-maas) - Setup guide for OpenAI-compatible tools on GreenNode's pay-as-you-go and Token Plan endpoints, which use different hosts.
- [Groq](https://console.groq.com/docs/openai) - Lists fields that return a 400 error (`logprobs`, `logit_bias`, `top_logprobs`, `messages[].name`), requires `n` to be 1, and converts `temperature` 0 to `1e-8`.
- [Kimi](https://platform.kimi.ai/docs/guide/migrating-from-openai-to-kimi) - Migration notes covering a `temperature` range of 0 to 1, `n` limits at low temperature, `tool_choice` support per model, and the unsupported `functions` parameter.
- [Mistral AI](https://docs.mistral.ai/api/) - Chat completions reference with Mistral-specific fields such as `random_seed`, `safe_prompt` and `prompt_mode`.
- [Parallel](https://docs.parallel.ai/chat-api/sdk-compatibility) - Responses API limitations: text-only input, answers streamed as a single text delta, and no per-token usage reporting.
- [Perplexity](https://docs.perplexity.ai/guides/chat-completions-guide) - Compares the Agent API in Open Responses format with Sonar chat completions, including where search results and citations are returned.
- [Together AI](https://docs.together.ai/docs/inference/openai-compatibility) - Endpoint and parameter differences, including `reasoning_effort` on GPT-OSS models only and `cached_tokens` appearing in different `usage` locations by model.
- [xAI](https://docs.x.ai/docs/api-reference) - API reference that marks parameters as unsupported or ignored, such as penalties on the Responses API and `logprobs` on newer models.
- [Z.ai](https://docs.z.ai/guides/develop/openai/python) - Using GLM models with the OpenAI Python SDK, including the `thinking` switch in `extra_body` and `reasoning_content` in streamed deltas.

## Self-Hosted Servers

- [Ollama](https://docs.ollama.com/api/openai-compatibility) - Supported subset of the OpenAI API, per-endpoint unsupported fields, and a non-stateful Responses API.
- [SGLang](https://docs.sglang.io/basic_usage/openai_api_completions.html) - OpenAI-compatible chat and completions APIs, parameter validation, LoRA adapter selection, and reasoning parsers.
- [vLLM](https://docs.vllm.ai/en/latest/serving/online_serving/openai_compatible_server/) - OpenAI-compatible server endpoints and per-endpoint parameter notes.

## Translation Layers and SDKs

- [AI SDK OpenAI Compatible Provider](https://ai-sdk.dev/providers/openai-compatible-providers) - TypeScript provider for any OpenAI-compatible API, with settings such as `includeUsage` and custom metadata extraction.
- [LiteLLM Provider-Specific Parameters](https://docs.litellm.ai/docs/completion/provider_specific_params) - How parameters outside the OpenAI standard are passed to each provider through the SDK and proxy.
- [OpenRouter Parameters](https://openrouter.ai/docs/api/reference/parameters) - Request parameters accepted by a multi-provider router and how omitted parameters are left to provider defaults.

## Conformance and Testing

- [AI API Proxy Canary Prompts](https://github.com/howardpen9/awesome-ai-api-proxy#canary-prompts-detect-silent-downgrade) - Repeatable prompts to run against a relay and the model developer's API to detect a silently substituted model.
- [Am I OpenAI Compatible](https://github.com/heiervang-technologies/am-i-openai-compatible) - Probe for any HTTP server, with a matrix comparing vLLM, llama.cpp, Ollama, LM Studio and TabbyAPI against OpenAI.
- [Oceans LLM Provider API Compatibility](https://oceans-llm-docs.pages.dev/reference/provider-api-compatibility) - Per-provider compatibility flags in a translating gateway, such as whether streaming usage is requested.
- [OpenAI OpenAPI Specification](https://github.com/openai/openai-openapi) - Machine-readable specification of the OpenAI API, useful as the reference for conformance checks.

## Trackers and Data

- [Artificial Analysis Providers](https://artificialanalysis.ai/leaderboards/providers) - Compares API providers per model on output speed, latency and price.
- [Ezkielyna Model Status](https://api.ezkielyna.store/status/models.json) - JSON feed with per-model 24-hour success rate, 7- and 30-day uptime, time to first token and output speed, measured on one gateway's traffic.
- [LLM Gateway Uptime](https://llmgateway.io/models/glm-5.2/uptime) - Per-model pages with provider uptime, time to first token, throughput and error breakdowns over the last 24 hours.
- [LLM Prices](https://www.llm-prices.com/) - Calculator for API cost from input, cached input and output tokens, backed by an open pricing dataset.
- [Models.dev](https://models.dev/) - Open-source database of model context limits, prices and capability flags such as tool calling and structured output.

## Related Lists

- [Awesome AI Gateways](https://github.com/ai-gateways/awesome-ai-gateways) - Open source and commercial LLM, MCP and agent gateways.

## Contributing

Contributions are welcome. Read the [contribution guidelines](CONTRIBUTING.md) first. Every claim must be checkable on the linked page.

## Footnotes

Maintained by Ezkielyna, an independent AI API gateway (affiliation disclosed; we list competitors on equal terms).
