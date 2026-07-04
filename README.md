# Quantum-Resistant Cryptography (Post-Quantum Cryptography) Demo

A Python project demonstrating **NIST-standardized post-quantum cryptographic
algorithms** — built as an internship / academic project to show why classical
public-key cryptography (RSA, ECC) is vulnerable to quantum computers, and how
post-quantum algorithms defend against that threat.

## Why This Matters

Shor's algorithm, run on a sufficiently powerful quantum computer, can break
RSA and ECC by efficiently solving integer factorization and discrete
logarithm problems. This project implements and benchmarks the algorithms
NIST has standardized as replacements:

| Algorithm | Standard | Type | Hard Problem |
|---|---|---|---|
| **ML-KEM** (Kyber) | FIPS 203 | Key Encapsulation | Lattice (Module-LWE) |
| **ML-DSA** (Dilithium) | FIPS 204 | Digital Signature | Lattice (Module-LWE) |
| **SLH-DSA** (SPHINCS+) | FIPS 205 | Digital Signature | Hash-based |

## Features

- ✅ Quantum-resistant key exchange (ML-KEM / Kyber)
- ✅ Quantum-resistant digital signatures (ML-DSA / Dilithium, SLH-DSA / SPHINCS+)
- ✅ Classical RSA/ECC baseline implementations for comparison
- ✅ Hybrid classical + post-quantum key exchange (mirrors real-world deployments
  like Chrome, Signal's PQXDH, and Apple's PQ3)
- ✅ Benchmark suite comparing key sizes and timing across all algorithms
- ✅ Full test suite + GitHub Actions CI

## Project Structure

```
quantum-resistant-crypto/
├── .github/workflows/ci.yml     # GitHub Actions CI pipeline
├── src/pqcrypto_demo/
│   ├── kem/                     # ML-KEM (Kyber) wrapper
│   ├── signatures/               # ML-DSA (Dilithium), SLH-DSA (SPHINCS+)
│   ├── classical/                # RSA / ECC baseline for comparison
│   ├── hybrid/                   # Classical + PQC hybrid key exchange
│   ├── benchmark/                # Performance & size benchmarking
│   └── utils/                    # Shared helper functions
├── examples/                     # Runnable demo scripts
├── tests/                        # pytest test suite
├── docs/                         # Extended documentation
├── notebooks/                    # Jupyter notebook for analysis/plots
└── data/                         # Benchmark output (CSV)
```

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/<your-username>/quantum-resistant-crypto.git
cd quantum-resistant-crypto
```

### 2. Install system dependencies for `liboqs`

**Ubuntu / Debian:**
```bash
sudo apt-get update
sudo apt-get install -y cmake gcc ninja-build libssl-dev
```

**macOS:**
```bash
brew install cmake ninja openssl
```

> See [`docs/setup_liboqs.md`](docs/setup_liboqs.md) for full details and
> troubleshooting.

### 3. Install Python dependencies

```bash
python -m venv venv
source venv/bin/activate      # Windows: venv\Scripts\activate
pip install -r requirements.txt
pip install -e .
```

## Usage

**Run the key exchange demo:**
```bash
python examples/demo_key_exchange.py
```

**Run the signature demo:**
```bash
python examples/demo_sign_verify.py
```

**Run the full classical vs. post-quantum benchmark:**
```bash
python examples/compare_classical_vs_pqc.py
```

Results are saved to `data/benchmark_results.csv`.

## Running Tests

```bash
pytest tests/ -v
```

## Algorithms Implemented

See [`docs/algorithms_overview.md`](docs/algorithms_overview.md) for details
on how each algorithm works, and [`docs/architecture.md`](docs/architecture.md)
for the module design rationale.

## References

- NIST FIPS 203 — Module-Lattice-Based Key-Encapsulation Mechanism Standard (ML-KEM)
- NIST FIPS 204 — Module-Lattice-Based Digital Signature Standard (ML-DSA)
- NIST FIPS 205 — Stateless Hash-Based Digital Signature Standard (SLH-DSA)
- Open Quantum Safe Project — https://openquantumsafe.org/

## License

MIT License — see [LICENSE](LICENSE).
