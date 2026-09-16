SIEL — Landing Page v34.11

Performance pass (visual preserved):
- hero PNG converted to WebP and preloaded at high priority;
- Silvia's Hair and Clara previews converted to WebP;
- below-the-fold portfolio images use lazy loading / async decoding;
- Jucelio third-party screenshot is deferred until its card approaches the viewport;
- Google Fonts stylesheet no longer blocks the first render;
- hero headline/header stay paintable immediately (no opacity entrance delaying LCP);
- below-the-fold sections use content-visibility;
- unused legacy images removed from the build.
