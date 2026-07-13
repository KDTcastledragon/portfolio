# CastleChat Portfolio Plan

## Goal

- Keep a concise project landing screen.
- Open a dedicated architecture view from the architecture button.
- Show the verified service, storage, event, and external API flows in one screen.
- Keep the diagram readable on desktop and stack it safely on smaller screens.

## Architecture Scope

- React Client to Nginx Reverse Proxy.
- REST routing to Domain Service and AI Assistant Service.
- WSS routing to WebSocket Gateway.
- gRPC request and response between WebSocket Gateway and Channel Engine.
- Kafka event flow from Channel Engine to Event Persist Worker.
- Direct MariaDB access where the current services actually use it.
- Redis shared session, room member cache, and read-position write-behind.
- Gemini API call from AI Assistant Service.

## Verification

- Validate HTML structure.
- Check keyboard interaction and reduced-motion behavior.
- Inspect Git diff before completion.
