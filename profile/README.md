# Elixir Volt ⚡

Elixir-native frontend toolchain. No Node.js, no npm, no esbuild — just Rust NIFs on the BEAM.

## Packages

| Package | Description | Hex |
|---------|-------------|-----|
| [volt](https://github.com/elixir-volt/volt) | Dev server, HMR, Tailwind CSS, production builds | [![Hex](https://img.shields.io/hexpm/v/volt.svg)](https://hex.pm/packages/volt) |
| [oxc](https://github.com/elixir-volt/oxc_ex) | JS/TS parse, transform, bundle, minify | [![Hex](https://img.shields.io/hexpm/v/oxc.svg)](https://hex.pm/packages/oxc) |
| [vize](https://github.com/elixir-volt/vize_ex) | Vue SFC compilation, Vapor IR, LightningCSS | [![Hex](https://img.shields.io/hexpm/v/vize.svg)](https://hex.pm/packages/vize) |
| [oxide_ex](https://github.com/elixir-volt/oxide_ex) | Tailwind CSS content scanning (Rust NIF) | [![Hex](https://img.shields.io/hexpm/v/oxide_ex.svg)](https://hex.pm/packages/oxide_ex) |
| [quickbeam](https://github.com/elixir-volt/quickbeam) | QuickJS runtime for the BEAM | [![Hex](https://img.shields.io/hexpm/v/quickbeam.svg)](https://hex.pm/packages/quickbeam) |
| [phoenix_vapor](https://github.com/elixir-volt/phoenix_vapor) | Vue templates as native LiveView renders | [![Hex](https://img.shields.io/hexpm/v/phoenix_vapor.svg)](https://hex.pm/packages/phoenix_vapor) |
| [npm](https://github.com/elixir-volt/npm_ex) | npm package manager for Elixir | [![Hex](https://img.shields.io/hexpm/v/npm.svg)](https://hex.pm/packages/npm) |

## How it fits together

```
Phoenix app
├── volt            — asset pipeline (dev server + builder)
│   ├── oxc         — JS/TS compilation (Rust NIF)
│   ├── vize        — Vue SFCs + CSS (Rust NIF)
│   ├── oxide_ex    — Tailwind scanning (Rust NIF)
│   └── quickbeam   — Tailwind compiler (QuickJS)
└── phoenix_vapor   — Vue templates → %Rendered{} (SSR)
    ├── vize        — Vapor IR compilation
    └── quickbeam   — JS expression evaluation
```
