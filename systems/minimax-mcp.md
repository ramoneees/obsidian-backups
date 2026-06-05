# MiniMax MCP Server

## Overview

Custom MCP server for MiniMax AI API. Configured via mcporter as server named `minimax`.

## Capabilities

| Model | Type | Notes |
|-------|------|-------|
| speech-2.8-hd | TTS | Emotion removed for compatibility |
| speech-2.8 | TTS | Emotion removed for compatibility |
| music-2.6 | Music generation | - |
| hailuo-2.3 | Video | - |
| hailuo-2.3-fast | Video (fast) | - |
| image-01 | Image generation | - |

## Patches Applied

**Location**: `~/.cache/uv/archive-v0/PoZBM1_TzbvBZTItBcw93/`

**const.py**:
- Added `speech-2.8-hd` to model list
- Added `music-2.6` to model list

**server.py**:
- Removed emotion parameter for speech-2.8 models

## Output Path

Generated files saved to: `~/minimax-output`

## Token Plan

Quotas depend on Starter/Plus/Max plan. Check plan for specific limits.

## Related

- [[mcp-servers]] — General MCP config
- [[../projects/minimax-tts-workflow]] — TTS workflow project