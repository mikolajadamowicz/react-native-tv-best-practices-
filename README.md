# React Native TV Best Practices

An AI agent skill for building high-quality React Native TV apps across Apple TV, Android TV, Fire TV, Vega OS, and web-based platforms (Tizen, webOS).

This skill follows the same structure as [react-native-best-practices](https://github.com/callstackincubator/agent-skills/tree/main/skills/react-native-best-practices) from the [agent-skills](https://github.com/callstackincubator/agent-skills) repository, adapted specifically for TV development.

## What is this?

This is a **skill** — a structured knowledge base that AI coding agents (Claude Code, OpenAI custom GPTs, etc.) can use to provide expert-level guidance on React Native TV development. Instead of relying on general training data, the agent consults these reference files for specific, up-to-date guidance.

The content is derived from two comprehensive resources:
- **"Mastering the Big Screen: React Native for TV"** by Callstack & Amazon
- **"The Ultimate Guide to React Native TV Development 2026"** by Callstack & Amazon

## How to use it

### With Claude Code

Register the skill in your Claude Code configuration, then invoke it when working on TV apps. The agent will consult `SKILL.md` for problem routing and pull detailed guidance from the relevant reference files.

### With OpenAI

Use the `agents/openai.yaml` configuration to set up a custom GPT or assistant with this skill.

### Standalone

Browse the reference files directly — each one is a self-contained guide on a specific TV development topic, with code examples, best practices, and platform-specific notes.

## Structure

```
├── SKILL.md                        # Main skill — priority framework, problem routing
├── POWER.md                        # Quick reference — prioritized file index
├── agents/
│   └── openai.yaml                 # OpenAI agent integration config
└── references/                     # 27 detailed reference guides
    ├── Focus & Navigation
    │   ├── focus-management.md     # TVFocusGuideView, hasTVPreferredFocus, debugging
    │   ├── focus-performance.md    # Cascading renders, single focus frame pattern
    │   ├── nav-directional.md      # D-pad fundamentals, platform focus engines
    │   ├── nav-patterns.md         # Drawer, tabs, modals, back navigation
    │   └── nav-keyboard.md         # System/custom keyboards, voice input, QR auth
    ├── Design & UX
    │   ├── design-10foot.md        # 10-foot experience principles
    │   ├── design-layout.md        # Cards, swimlanes, heroes, safe zones, spacing
    │   ├── design-typography.md    # Font sizes (50-80% larger than mobile), typefaces
    │   └── design-color.md         # Contrast ratios, HDR, ambient light adaptation
    ├── Setup & Architecture
    │   ├── setup-getting-started.md # react-native-tvos, Expo TV, platform config
    │   ├── setup-architecture.md    # Monorepo structure, code sharing strategies
    │   └── setup-cross-platform.md  # Platform detection, file extensions, inconsistencies
    ├── Performance
    │   ├── perf-overview.md        # Golden rule, device tiers, KPIs, automation
    │   ├── perf-animations.md      # Native driver, Reanimated, platform quirks
    │   ├── perf-lists.md           # FlashList virtualization, FlatList optimization
    │   ├── perf-network.md         # Optimistic UI, prefetching, caching
    │   └── perf-memory.md          # Image optimization, cache control, profiling
    ├── Video Streaming
    │   ├── video-streaming.md      # ABR, HLS/DASH protocols, DRM
    │   ├── video-players.md        # react-native-video, Shaka Player, custom controls
    │   └── video-debugging.md      # FFmpeg, network analysis, performance monitoring
    ├── Testing
    │   ├── test-strategy.md        # Trophy approach, integration-first strategy
    │   ├── test-javascript.md      # RNTL, tvRemote helpers, platform event emulation
    │   └── test-e2e.md             # Appium, WebdriverIO, device farms
    ├── Accessibility
    │   ├── a11y-overview.md        # WCAG on TV, screen readers, platform differences
    │   ├── a11y-implementation.md  # Roles, labels, hints, dynamic content, modals
    │   └── a11y-checklist.md       # 10-section pre-launch accessibility checklist
    └── Release
        └── release-cicd.md         # Build fingerprinting, diff triggers, caching, app stores
```

## Topics covered

### Focus & Navigation
Focus management is the core technical challenge for TV apps. These guides cover how platform focus engines work (tvOS inferred model vs. Android TV Cartesian model vs. web-based spatial navigation), how to use `TVFocusGuideView` for complex layouts, how to trap focus in modals, and how to debug focus issues. Performance-specific guidance covers preventing cascading re-renders on focus changes and the single focus frame pattern.

### Design for the 10-Foot Experience
Everything changes when the user is 10 feet from the screen. Text must be 50-80% larger than mobile. Focus states must be visible from across the room. Navigation must be predictable with minimal button presses. These guides cover layout patterns (cards, swimlanes, heroes), typography scales, color/contrast guidelines for various display technologies (LCD, OLED, HDR), and safe zone handling for overscan.

### Setup & Architecture
Getting started with `react-native-tvos` and Expo TV, structuring a monorepo for multiple TV platforms, and sharing code between mobile and TV. Covers platform-specific file extensions, `Platform.isTV` detection, and bundler configuration for web-based TV targets.

### Performance
TV hardware is significantly weaker than modern phones — often 1-2 GB RAM shared with the video decoder. These guides cover the golden rule (optimize for the weakest device), device tier strategies, animation performance (native driver is mandatory), list virtualization (FlashList over ScrollView), network optimization (optimistic UI, prefetching), and memory management (image scaling, cache control).

### Video Streaming
The backbone of most TV apps. Covers Adaptive Bitrate Streaming, HLS/DASH protocols, DRM (Widevine, FairPlay, PlayReady), video player options (`react-native-video` for simple cases, Shaka Player for enterprise), custom controls, seek bar implementation, BIF thumbnail format, and debugging tools (FFmpeg, Charles Proxy, Proxyman).

### Testing
TV testing needs a different approach than mobile. The trophy strategy emphasizes integration tests using React Native Testing Library with custom `tvRemote` helpers that emit platform-specific hardware key events. E2E testing covers Appium with WebdriverIO for native platforms and browser automation for web-based TVs, plus device farm integration (AWS, BrowserStack, Sauce Labs).

### Accessibility
Accessibility on TV is unique — D-pad navigation, focus-driven UI, limited screen reader consistency across platforms. Covers WCAG compliance, implementing roles/labels/hints, accessible modals and dynamic content, audio descriptions, and a full 10-section pre-launch checklist.

### CI/CD & Release
TV CI/CD pipelines multiply in complexity across 6+ platforms. Covers build fingerprinting (skip native builds when only JS changed), diff-based triggers (only build affected platforms), caching strategies, performance monitoring in CI, and app store submission requirements.

## Key principles

1. **The Golden Rule** — Design for the weakest device in your audience, make it feel like the fastest one.

2. **Focus Is Navigation** — No touch on TV. Every interaction flows through focus. Let the platform focus engine lead; fix layouts before adding focus code.

3. **The 10-Foot Experience** — Users are 10 feet away. Text 50-80% larger. Generous spacing. Strong contrast. Every button press = immediate visual feedback.

4. **Measure → Optimize → Re-measure → Validate** — Always on real hardware. Keep a low-end streaming stick in your dev kit.

## Contributing

To add or update reference files:
1. Follow the existing naming convention (`category-topic.md`)
2. Include: Key Takeaways, code examples, platform quirks, and Related links
3. Update `POWER.md` and `SKILL.md` routing tables if adding new files

## License

Content derived from publicly available Callstack & Amazon publications on React Native TV development.
