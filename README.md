# Extension Skeleton

A production-ready Chrome extension skeleton with built-in LLM support. Based on [Nanobrowser](https://github.com/nanobrowser/nanobrowser) (Apache 2.0).

## Features

### Core (Always Available)
- **Sidepanel UI** - React chat interface with message list, history, bookmarks
- **Settings Page** - LLM provider configuration, model selection
- **11 LLM Providers** - OpenAI, Anthropic, Gemini, Ollama, Groq, Cerebras, etc.
- **Chrome Storage** - Type-safe storage abstraction
- **i18n** - Multi-language support (EN, PT-BR, ZH-TW)
- **Background Worker** - Service worker with port connections
- **Content Script** - Page injection base

### Optional Modules (Enable as Needed)
- **Web Automation** - Navigator, Planner, Validator agents
- **DOM Tools** - Page interaction, element extraction
- **Task Manager** - Task queue and execution
- **Speech-to-Text** - Voice input
- **Guardrails** - Safety filters

## Quick Start

### Prerequisites
- Node.js 22.x+
- pnpm 9.x+

### Install & Run

   ```bash
# Install dependencies
pnpm install

# Start development (watch mode)
pnpm dev

# Build for production
pnpm build

# Create extension zip
pnpm zip
```

### Load in Chrome

1. Open `chrome://extensions/`
2. Enable "Developer mode"
3. Click "Load unpacked"
4. Select the `dist/` folder

## Project Structure

```
extension-skeleton/
├── chrome-extension/          # Main extension (manifest, background)
│   ├── manifest.js            # Manifest V3 config
│   └── src/background/        # Service worker
├── pages/                     # UI pages
│   ├── side-panel/            # Sidepanel React app
│   ├── options/               # Settings page
│   └── content/               # Content scripts
├── packages/                  # Shared libraries
│   ├── storage/               # Chrome storage abstraction
│   ├── shared/                # Common utilities
│   ├── ui/                    # Shared components
│   └── i18n/                  # Internationalization
├── package.json
├── pnpm-workspace.yaml
└── turbo.json
```

## LLM Providers

| Provider | Type |
|----------|------|
| OpenAI | `openai` |
| Anthropic | `anthropic` |
| Google Gemini | `gemini` |
| DeepSeek | `deepseek` |
| Grok | `grok` |
| Ollama | `ollama` |
| Groq | `groq` |
| Cerebras | `cerebras` |
| OpenRouter | `openrouter` |
| Azure OpenAI | `azure_openai` |
| Custom OpenAI | `custom_openai` |

## Commands

| Command | Description |
|---------|-------------|
| `pnpm dev` | Start development mode |
| `pnpm build` | Build production version |
| `pnpm zip` | Create distribution zip |
| `pnpm type-check` | TypeScript checking |
| `pnpm lint` | Run ESLint |
| `pnpm clean` | Clean build artifacts |

## Customization

### Change Branding
- `chrome-extension/manifest.js` - name, description
- `packages/i18n/locales/*/messages.json` - strings
- `chrome-extension/public/` - icons

### Add Storage
```typescript
import { createStorage, StorageEnum } from '@extension/storage';

export const myStore = createStorage<MyType>('my-key', defaultValue, {
  storageEnum: StorageEnum.Local,
});
```

### Add Sidepanel View
```typescript
// pages/side-panel/src/components/MyView.tsx
export const MyView = () => <div>My view</div>;
```

### Add LLM Provider
```typescript
// packages/storage/lib/settings/types.ts
export enum ProviderTypeEnum {
  MyProvider = 'my_provider',
}
```

## License

Apache 2.0 - Based on [Nanobrowser](https://github.com/nanobrowser/nanobrowser)
