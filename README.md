# OpenAI API Connector

OpenAI API connector provides instant queries and mutations to request OpenAI API-compatible resources.

This connector is built using the [NDC Rest](https://github.com/hasura/ndc-rest) with [OpenAI's OpenAPI Specification](https://github.com/openai/openai-openapi).

## Environment Variables

| Name                      | Description                                   | Default Value             |
| ------------------------- | --------------------------------------------- | ------------------------- |
| OPENAI_SERVER_URL         | The base server URL of OpenAI API             | https://api.openai.com/v1 |
| OPENAI_API_KEY_AUTH_TOKEN | Bearer authentication token                   |                           |
| OPENAI_TIMEOUT            | Default request timeout in seconds            | 30                        |
| OPENAI_RETRY_TIMES        | Number of retry times                         | 0                         |
| OPENAI_RETRY_DELAY        | Delay time between each retry in milliseconds | 1000                      |
| OPENAI_RETRY_HTTP_STATUS  | Retry on HTTP status                          | 429, 500, 502, 503        |

## Development

### Local Development

Copy `.env.example` to `.env` and start Docker Compose:

```sh
docker-compose up -d --build
```

The connector serves the HTTP service at `http://localhost:8080`.

You also can use the mock API:

```ini
OPENAI_SERVER_URL=https://api.openai-mock.com/v1
OPENAI_API_KEY_AUTH_TOKEN=sk-0
```

Or you can use llama.cpp server. It supports some [OpenAI-compatible APIs](https://github.com/ggerganov/llama.cpp/blob/master/examples/server/README.md#post-v1chatcompletions-openai-compatible-chat-completions-api):

```ini
OPENAI_SERVER_URL=http://llama-server:5050/v1
```

### Update dependencies

```sh
NDC_REST_VERSION=<version> make update-deps
```

### Update schema

Update the latest commit in [schema/openai.yaml](schema/openai.yaml) and run:

```sh
make build-schema
```
