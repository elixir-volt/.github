# Elixir Volt ⚡

Frontend tooling for Phoenix that runs inside the BEAM. Build JavaScript, TypeScript, Vue, Tailwind CSS, npm packages, and Iconify SVGs from Elixir — without managing Node.js toolchain processes in your app.

```bash
mix igniter.install volt
mix phx.server
```

Volt is the center of the stack: a Vite-level asset pipeline with dev server, HMR, Tailwind, production builds, and framework support powered by Rust NIFs and embedded JavaScript runtimes.

## Start here

| Project | What it does | Hex |
| --- | --- | --- |
| [volt](https://github.com/elixir-volt/volt) | Elixir-native frontend build tool: dev server, HMR, Tailwind CSS, JS/TS, Vue/Svelte/React/Solid, production builds | [![Hex](https://img.shields.io/hexpm/v/volt.svg)](https://hex.pm/packages/volt) |

## Phoenix UI packages

| Project | What it does | Hex |
| --- | --- | --- |
| [phoenix_iconify](https://github.com/elixir-volt/phoenix_iconify) | Compile-time discovered Iconify SVG components for Phoenix and LiveView: `<.icon name="lucide:settings" />` | [![Hex](https://img.shields.io/hexpm/v/phoenix_iconify.svg)](https://hex.pm/packages/phoenix_iconify) |
| [iconify](https://github.com/elixir-volt/iconify) | Core IconifyJSON parser, fetcher, alias resolver, transformer, and SVG renderer for Elixir | [![Hex](https://img.shields.io/hexpm/v/iconify.svg)](https://hex.pm/packages/iconify) |
| [phoenix_vapor](https://github.com/elixir-volt/phoenix_vapor) | Vue templates compiled to native `%Phoenix.LiveView.Rendered{}` structs | [![Hex](https://img.shields.io/hexpm/v/phoenix_vapor.svg)](https://hex.pm/packages/phoenix_vapor) |

## Toolchain packages

| Project | What it does | Hex |
| --- | --- | --- |
| [oxc](https://github.com/elixir-volt/oxc_ex) | JS/TS parsing, transforming, bundling, formatting, linting, and minification through OXC | [![Hex](https://img.shields.io/hexpm/v/oxc.svg)](https://hex.pm/packages/oxc) |
| [vize](https://github.com/elixir-volt/vize_ex) | Vue SFC compilation, Vapor IR, and CSS tooling through Vize | [![Hex](https://img.shields.io/hexpm/v/vize.svg)](https://hex.pm/packages/vize) |
| [oxide_ex](https://github.com/elixir-volt/oxide_ex) | Tailwind CSS content scanning and candidate extraction through Tailwind Oxide | [![Hex](https://img.shields.io/hexpm/v/oxide_ex.svg)](https://hex.pm/packages/oxide_ex) |
| [quickbeam](https://github.com/elixir-volt/quickbeam) | QuickJS runtime for the BEAM with Web APIs backed by OTP | [![Hex](https://img.shields.io/hexpm/v/quickbeam.svg)](https://hex.pm/packages/quickbeam) |
| [npm](https://github.com/elixir-volt/npm_ex) | npm package resolution and installation from Elixir | [![Hex](https://img.shields.io/hexpm/v/npm.svg)](https://hex.pm/packages/npm) |
| [npm_semver](https://github.com/elixir-volt/npm_semver) | npm-compatible semantic version ranges for Elixir | [![Hex](https://img.shields.io/hexpm/v/npm_semver.svg)](https://hex.pm/packages/npm_semver) |

## How it fits together

```text
Phoenix app
├── volt                  — asset pipeline, dev server, HMR, production builds
│   ├── oxc               — JS/TS compilation and linting
│   ├── vize              — Vue SFCs and CSS tooling
│   ├── oxide_ex          — Tailwind content scanning
│   ├── quickbeam         — embedded JS runtime for tools
│   └── npm               — package resolution and install
├── phoenix_iconify       — server-rendered Iconify SVG components
│   └── iconify           — IconifyJSON parsing and SVG rendering
└── phoenix_vapor         — Vue templates → %Phoenix.LiveView.Rendered{}
    ├── vize              — Vapor IR compilation
    └── quickbeam         — JS expression evaluation
```

## Why this exists

Phoenix apps should not need a pile of external watchers, binaries, and JavaScript toolchain glue to get modern frontend ergonomics. Elixir Volt packages keep the toolchain close to the app, supervised by the BEAM, configurable with Elixir, and easy to compose with Phoenix.
