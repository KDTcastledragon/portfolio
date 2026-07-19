# CastleChat Portfolio Plan

## 2026-07-14 Goal

- Reframe the site as a multi-project portfolio rather than a CastleChat-only landing page.
- Keep the fixed header and CastleChat project box in the original dark-green theme.
- Keep every area outside the header and project box pure white.
- Change only the requested project-box placement and dimensions.
- Preserve the existing CastleChat headline scale and the architecture and stack dialogs.
- Add the requested right-side project menu without inventing unfinished project content.

## Existing Architecture Scope

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

## 2026-07-18 Architecture Revision

- Add On-Premise and Cloud architecture views inside the existing architecture dialog.
- Show native Nginx on Windows for On-Premise and containerized Nginx on AWS Kubernetes for Cloud.
- Reorganize the technology stack around application, communication, asynchronous processing, data, and deployment.
- Promote the existing skill summary to a concise Core Engineering section.
- Keep downloadable desktop builds outside the portfolio repository and link GitHub Release assets.

## 2026-07-19 Architecture Visual Cleanup

- Simplify the On-Premise board by removing legends, connector labels, and explanatory footnotes.
- Use the CastleChat light-green palette for both architecture views.
- Redraw connector directions and rebalance node spacing without changing the represented services.

## 2026-07-19 Cloud Architecture Simplification

- Rebuild only the Cloud panel around AWS Cloud, ECR, DEV VPC, EKS, Gemini, MariaDB, and S3.
- Remove the crossed-out intermediary components and their layout space.
