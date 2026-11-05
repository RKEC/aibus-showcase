# Experiments in my home AI lab

I test changes and choose from the results. These samples are small, and I state the size of each one.

## Which version of the model?

I compared two versions of the same model on the same hardware.

| Version | Prompt speed (tokens/s) | Output speed (tokens/s) | Hidden coding tests |
|---|---|---|---|
| IQ4_XS | 841 | 36.8 | 2 of 2 |
| UD-Q4_K_XL | 546 | 39.2 | 2 of 2 |

I chose UD-Q4_K_XL, the more accurate version with faster output, and I accepted slower prompt reading.

## Can a local model finish coding tasks alone?

[agent-flow](https://github.com/RKEC/agent-flow) gives small tasks to a local model and tests each result. Plans with exact steps passed 7 of 7 tasks on the first try, and hidden tests passed. On the same task, a prose plan also passed but took 915 s instead of 710 s. These tasks were easy, so harder tasks are the next test.

## Why did the model run 8 times slower after a reboot?

Ollama started before the external GPU was ready, and it detects GPUs only at startup, so it stayed on the CPU. I made the service wait for the GPU. Output speed returned to 46.7 tokens/s.

## Can an AI assistant read my mail safely?

My assistant can read mail and write drafts, but it has no tool that sends mail. I wrote the tools myself, and remote images are blocked, because an image URL can leak data. The design assumes that a mail can contain a prompt injection, so an injection has no way to send anything out.

## Private document search

I run document search (RAG) on my own hardware with Open WebUI and a local embedding model. I have not yet measured its retrieval quality.
