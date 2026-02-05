# DeMoD Nix Assistant: Nix Ecosystem Expert for Ollama agents.

This repository provides training data to fine-tune IBM's Granite3 MoE model as a specialized assistant for the Nix ecosystem (Nix package manager, NixOS, nixpkgs, and flakes). The dataset emphasizes production-grade patterns, security practices, and deep technical knowledge current as of February 2026.

## Dataset Contents

- `purenix_senior_alpaca.json`: 42 expert-level instruction-response pairs in Alpaca format
- Comprehensive coverage of:
  - Nix language semantics (lazy evaluation, recursion limits, string escaping)
  - Store protocol internals (NAR format, .narinfo, binary cache API)
  - Security boundaries (evaluation vs build sandboxing)
  - Cross-compilation mechanics
  - Module system merge strategies
  - Reproducibility limits and verification
  - Performance pitfalls and optimizations
  - Platform-specific behavior (Linux, macOS, Windows/WSL2)

All examples include explicit version context (Nix 2.26, NixOS 25.11 "Xantusia") and distinguish between stable/experimental features.

## Usage

For supervised fine-tuning with Granite3 MoE:

```bash
python train.py --dataset purunix_senior_alpaca.json --model granite3-moe-8b
```

The dataset follows Alpaca format:
```json
{
  "instruction": "[CONTEXT: ...] Task description",
  "input": "Optional user context",
  "output": "Version-aware response with caveats"
}
```

## Licensing

### Granite3 MoE
This dataset is designed for use with IBM's Granite3 MoE model, which is licensed under the IBM LICENSE AGREEMENT FOR GRANITE MODELS. Users must comply with IBM's terms when using this dataset for fine-tuning Granite3 models.

### Nix Content
All technical content about the Nix ecosystem is derived from official Nix documentation and source code, which are licensed under:

- **Nix documentation**: Creative Commons Attribution 4.0 International (CC-BY-4.0)
- **Nix source code**: MIT License

The training examples themselves are licensed under CC-BY-4.0 to match the Nix documentation they reference.

### Dataset License
The training dataset structure and organization is licensed under CC-BY-4.0. You may:
- Share — copy and redistribute the material in any medium or format
- Adapt — remix, transform, and build upon the material for any purpose, even commercially

Under the following terms:
- **Attribution** — You must give appropriate credit, provide a link to the license, and indicate if changes were made. You may do so in any reasonable manner, but not in any way that suggests the licensor endorses you or your use.

## Disclaimer

This dataset is not affiliated with or endorsed by the NixOS Foundation or IBM. It is provided for research and development purposes only. Users are responsible for compliance with all applicable licenses and terms of use.
