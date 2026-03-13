# LLM Server

The lab includes a dedicated AI analysis node running Ollama.

## Purpose

- receive structured scan results
- analyze host exposure
- generate triage-style output
- support AutoRecon AI in a local-first workflow

## Benefits

- private analysis
- no cloud dependency required
- reusable for future security automation workflows

## Example Model

- qwen2.5:7b

## Network Notes

The LLM server may be reached locally or through a private overlay such as Tailscale, depending on lab design.
