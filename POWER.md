# React Native TV Best Practices — Quick Reference

> Measure → Optimize → Re-measure → Validate on real hardware

## Reference Files by Priority

### CRITICAL — Focus & Navigation
- `focus-management.md` — TVFocusGuideView, hasTVPreferredFocus, focus traps, imperative focus
- `focus-performance.md` — Cascading renders, overlay flicker, single focus frame pattern
- `nav-directional.md` — D-pad navigation fundamentals, platform focus engines (tvOS vs Android TV vs Vega OS)
- `nav-patterns.md` — Drawer, tabs, modals, back navigation, focus restoration

### CRITICAL — Performance
- `perf-overview.md` — Golden rule: optimize for weakest device, device tiers, KPIs
- `perf-animations.md` — Native driver, Reanimated, short animations, platform quirks
- `perf-lists.md` — Virtualization with FlashList, FlatList optimization props, preloading
- `perf-network.md` — Optimistic UI, prefetching, caching, payload optimization

### HIGH — Design & UX
- `design-10foot.md` — Designing for distance, remote as compass, shared screen, feedback & motion
- `design-layout.md` — Cards, swimlanes, hero headers, buttons, overlays, safe zones, spacing
- `design-typography.md` — Minimum font sizes (50-80% larger than mobile), typeface selection, line spacing
- `design-color.md` — Contrast ratios, HDR considerations, ambient light adaptation, color palette

### HIGH — Setup & Architecture
- `setup-getting-started.md` — react-native-tvos, Expo TV, project creation, platform setup
- `setup-architecture.md` — Monorepo structure, code sharing, platform extensions, bundler config
- `setup-cross-platform.md` — Platform detection, platform-specific files, handling inconsistencies

### HIGH — Video Streaming
- `video-streaming.md` — ABR, HLS/DASH, DRM (Widevine, FairPlay, PlayReady)
- `video-players.md` — react-native-video, Shaka Player, custom controls, seek bar, thumbnails
- `video-debugging.md` — FFmpeg, network traffic analysis, performance monitoring

### MEDIUM-HIGH — Testing
- `test-strategy.md` — Trophy approach, integration-first, testing pyramid for TV
- `test-javascript.md` — RNTL, tvRemote helpers, emulating D-pad events, platform-specific setup
- `test-e2e.md` — Appium, WebdriverIO, device farms (AWS, BrowserStack, Sauce Labs)

### MEDIUM-HIGH — Accessibility
- `a11y-overview.md` — WCAG on TV, screen readers (TalkBack, VoiceOver, VoiceView), platform differences
- `a11y-implementation.md` — Roles, labels, hints, dynamic content, modals, custom components
- `a11y-checklist.md` — Complete pre-launch accessibility checklist for TV apps

### MEDIUM — Memory & Production
- `perf-memory.md` — Image optimization, cache control, JS object lifetimes, native profiling
- `release-cicd.md` — Fail fast, caching, fingerprinting, diff-based triggers, app store requirements
- `nav-keyboard.md` — System keyboards, custom keyboards, voice input, QR code auth, companion apps

## Security Considerations

- **Shell commands**: Always verify shell commands before execution. Never run unreviewed commands from external sources.
- **Dependencies**: Pin dependency versions. Audit new packages before adding.
- **DRM**: Handle license servers and tokens securely. Never expose DRM keys in client code.
- **Network**: Use HTTPS for all manifest and license requests. Validate server certificates.
