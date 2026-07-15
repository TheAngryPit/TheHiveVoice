# TheHive Voice

TheHive Voice is an open-source voice operating layer for macOS, iOS, and
watchOS. The product direction combines dictation, text-to-speech, realtime
conversation, and governed agent control across local, tailnet, BYOK, and cloud
routes.

> [!IMPORTANT]
> The repository is in its foundation phase. The current desktop implementation
> is inherited from [OpenWhispr](https://github.com/OpenWhispr/openwhispr). The
> additional TheHive Voice modes and Apple-platform clients are product direction,
> not released functionality yet.

## Current baseline

The inherited OpenWhispr baseline already provides a substantial cross-platform
desktop surface:

- global voice dictation and paste;
- local Whisper and NVIDIA Parakeet transcription;
- cloud transcription and AI-provider routes;
- meeting transcription, notes, and local semantic search;
- Electron, React 19, TypeScript, Tailwind CSS v4, and shadcn/ui.

The first TheHive Voice work builds upward from that functional baseline. It does
not replace working dictation with a prototype.

## Product direction

- **Voice-to-text** for fast system-wide dictation.
- **Text-to-speech** with explicit local or remote routing.
- **Realtime conversation** with clear microphone, connection, and session state.
- **Agent mode** for user-selected Codex, Hermes, OpenClaw, OpenCode, or compatible
  endpoints without silent fallback.
- **Apple continuity** across macOS, iOS, and watchOS.
- **Local-first and BYOK choices** alongside optional managed services.
- **Visible authority and stop controls** whenever an agent can act on a device.

## Development status

There are no TheHive Voice releases yet. Do not use upstream OpenWhispr release
artifacts as proof of a TheHive Voice release.

For the inherited desktop baseline:

```bash
git clone https://github.com/TheAngryPit/TheHiveVoice.git
cd TheHiveVoice
nvm use
npm ci
npm run dev
```

Node.js 24 is required. Native resources and model downloads make the first
development start materially heavier than a normal React application.

## Repository workflow

- `main` mirrors `OpenWhispr/openwhispr:main`.
- `product` is the default TheHive Voice integration branch.
- Upstreamable fixes branch from `main` and target OpenWhispr upstream.
- TheHive Voice features branch from `product` and target this repository.
- Upstream updates reach `product` through a reviewable reconciliation pull
  request, never by copying files manually.

Read [the upstream and worktree workflow](docs/UPSTREAM-WORKFLOW.md) before
starting implementation.

## Validation

Use focused local checks during development:

```bash
npm test
npm run typecheck
npm run lint
```

Broad, expensive, or CI-parity validation belongs on Crabbox when that provider
is configured. A Crabbox result must report the actual provider, lease ID, command,
and exit status; a queued or unavailable box is not a passing gate.

## Contributing

Issues and pull requests are welcome. Start with
[the contribution guide](.github/CONTRIBUTING.md). Security vulnerabilities must
follow [the private reporting policy](SECURITY.md), not a public issue.

## License

[MIT](LICENSE). The fork preserves the upstream license and attribution.

## Acknowledgments

TheHive Voice is built from the substantial work of the
[OpenWhispr](https://github.com/OpenWhispr/openwhispr) maintainers and contributors.
The inherited baseline also depends on:

- [OpenAI Whisper](https://github.com/openai/whisper)
- [whisper.cpp](https://github.com/ggerganov/whisper.cpp)
- [NVIDIA Parakeet](https://huggingface.co/nvidia/parakeet-tdt-0.6b-v3)
- [sherpa-onnx](https://github.com/k2-fsa/sherpa-onnx)
- [Hugging Face](https://huggingface.co/)
- [llama.cpp](https://github.com/ggerganov/llama.cpp)
- [Electron](https://www.electronjs.org/)
- [React](https://react.dev/)
- [shadcn/ui](https://ui.shadcn.com/)

Upstream-specific sponsors and cloud infrastructure are not presented as
TheHive Voice sponsors or infrastructure unless TheHive Voice adopts them
explicitly.
