# Hanzo C# SDK → [hanzo-csharp/sdk](https://github.com/hanzo-csharp/sdk)

[![NuGet](https://img.shields.io/nuget/v/Hanzo?label=Hanzo)](https://www.nuget.org/packages/Hanzo)

The Hanzo C# SDK lives at **[github.com/hanzo-csharp/sdk](https://github.com/hanzo-csharp/sdk)**: every `/v1`
operation of `api.hanzo.ai` as a typed method, generated from the API document
each cloud release publishes. This repository is its old address and holds no
code. Issues and pull requests go to [hanzo-csharp/sdk](https://github.com/hanzo-csharp/sdk).

## Install

.NET 8 or newer, from nuget.org:

```bash
dotnet add package Hanzo
```

## Quickstart

```csharp
using Hanzo.AI;
using Hanzo.AI.Api;
using Hanzo.AI.Model;

var config = Gateway.Configuration();   // HANZO_API_KEY, HANZO_BASE_URL, HANZO_ORG_ID

foreach (var key in new AccountApi(config).GetAccountKeys().Keys)
{
    Console.WriteLine($"{key.Type} {key.Prefix}");
}

var reply = new AiApi(config).PostChatCompletions(new OpenaiChatCompletionRequest(
    model: "zen5",
    messages: new() { new OpenaiChatCompletionMessage(role: "user", content: "Say hello.") }));
Console.WriteLine(reply.Choices[0].Message.Content);
```

## Examples

Each a complete program in the SDK, compiled against it on every release:

| flow | what it does |
|---|---|
| [hello](https://github.com/hanzo-csharp/sdk/blob/main/examples/Hello.cs) | `GET /v1/account/keys`: prove the key works |
| [chat](https://github.com/hanzo-csharp/sdk/blob/main/examples/Chat.cs) | `POST /v1/chat/completions`: one completion |
| [money](https://github.com/hanzo-csharp/sdk/blob/main/examples/Money.cs) | `GET /v1/billing/balance`, `GET /v1/billing/usage` |
| [store](https://github.com/hanzo-csharp/sdk/blob/main/examples/Store.cs) | create a KV store, read it back, delete it |
| [agent](https://github.com/hanzo-csharp/sdk/blob/main/examples/Agent.cs) | create an agent, run it, poll the run to completion |
| [tools](https://github.com/hanzo-csharp/sdk/blob/main/examples/Tools.cs) | `GET /v1/tool`: the tool catalog the key reaches |
| [kai](https://github.com/hanzoai/kai/blob/main/examples/csharp/Program.cs) | `POST /v1/decisions`: a Kai decision, in the Kai cookbook |

## Other languages

[Java](https://github.com/hanzo-java/sdk) · [Python](https://github.com/hanzoai/python-sdk) ·
[TypeScript](https://github.com/hanzoai/js-sdk) · [Go](https://github.com/hanzo-go/sdk) ·
[Rust](https://github.com/hanzo-rs/sdk) · [C++](https://github.com/hanzo-cpp/sdk) ·
[all SDKs](https://github.com/hanzoai/sdk)
