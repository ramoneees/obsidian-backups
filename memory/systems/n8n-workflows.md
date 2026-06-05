# n8n Workflows — Integration Patterns

## MCP Calls via Python

### Pattern (Working)

```python
import subprocess

# Source env first
subprocess.run(['bash', '-c', 'source ~/.openclaw/.env && python3 /tmp/n8n-mcporter.py'],
               env={**os.environ, 'N8N_MCP_TOKEN': token})
```

### Key Points

1. Always `source ~/.openclaw/.env` first for N8N_MCP_TOKEN
2. Use Python subprocess with `--args` flag + JSON payload
3. mcporter call: `mcporter call <server> <tool> --args <json>`

## Env Source

`~/.openclaw/.env` contains:
- N8N_MCP_TOKEN
- Other n8n credentials

## Common Patterns

- Trigger: webhook → Python script → mcporter
- Result: mcporter call → n8n response → Hermes notification

## Related

- [[mcp-servers]] — MCP server config
- [[k8s-autonomous]] — K8s alert workflow using n8n