# Contributing

Contributions, suggestions, and issue reports are welcome!

## Development Setup

```bash
git clone https://github.com/<your-username>/quantum-resistant-crypto.git
cd quantum-resistant-crypto
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
pip install -e .
```

## Running Tests

```bash
pytest tests/ -v
```

## Code Style

- Keep modules focused (one algorithm family per file)
- Add a docstring to every public function/class explaining the cryptographic
  purpose, not just the code mechanics
- Add a corresponding test in `tests/` for any new wrapper or function

## Adding a New Algorithm Wrapper

1. Create a new file under the appropriate folder (`kem/`, `signatures/`, etc.)
2. Follow the existing wrapper pattern: `generate_keypair()`, plus
   `encapsulate`/`decapsulate` or `sign`/`verify`
3. Add a test in `tests/`
4. Add a usage example in `examples/` if it demonstrates a new concept
5. Update `docs/algorithms_overview.md`
