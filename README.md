# 🧪 test-vba

A GitHub Action that executes VBA unit tests against plain-text source files (`.bas`, `.cls`, `.frm`) without requiring Microsoft Excel to be installed, prints pass/fail test results, and uploads code coverage metrics to [Coveralls.io](https://coveralls.io).

Powered by [`vbaUnit`](https://github.com/Beakerboy/vbaUnit), [`Vba-Excel-Object-Library`](https://github.com/Beakerboy/Vba-Excel-Object-Library), and [`VbaStdLib`](https://github.com/Beakerboy/VbaStdLib).

---

## ✨ Features

* **Cross-Platform Execution:** Runs natively in Python on `ubuntu-latest`, `windows-latest`, or `macos-latest`—no Office COM installation required.
* **Built-In Standard & Excel Libraries:** Pre-loads `vba` (`VbaStdLib`) and `excel` (`Vba-Excel-Object-Library`) object models so your VBA code and tests run out of the box.
* **Automated Code Coverage:** Tracks line coverage during test runs and uploads reports directly to Coveralls.io.

---

## 📥 Inputs

| Input | Description | Required | Default |
| :--- | :--- | :---: | :--- |
| `source_path` | Path to the directory containing your VBA source files (`.bas`, `.cls`, `.frm`). | No | `./src` |
| `test_path` | Path to the directory containing your VBA unit test modules. | No | `./tests` |
| `github_token` | Coveralls repository token (or `secrets.GITHUB_TOKEN`) used to upload code coverage reports. | No | `***` |

---

## 🚀 Usage

### Basic Example

Add a workflow file (e.g., `.github/workflows/test.yml`) to run your VBA unit tests on every push and pull request:

```yaml
name: VBA Unit Tests

on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'

      - name: Run VBA unit tests
        uses: Vba-actions/test-vba@v1
        with:
          source_path: './src'
          test_path: './tests'
          github_token: \${{ secrets.GITHUB_TOKEN }}
```

### Custom Folder Layout

If your project stores source code at the repository root or uses a custom test folder name, override `source_path` and `test_path`:

```yaml
      - name: Run VBA unit tests
        uses: Vba-actions/test-vba@v1
        with:
          source_path: './source'
          test_path: './unit-tests'
          github_token: \${{ secrets.COVERALLS_REPO_TOKEN }}
```

---

## 🔧 How It Works

1. Installs `vbaUnit`, `Vba-Excel-Object-Library`, and `VbaStdLib` into the runner's Python environment.
2. Sets `SOURCEPATH`, `TESTPATH`, and `COVERALLS_REPO_TOKEN` from your workflow inputs.
3. Executes `python -m vba_unit --coverage --libraries vba excel`, printing passing and failing test functions to the workflow log and reporting coverage to Coveralls.

---

## 🤝 Contributing

Found a bug or want to suggest an improvement? Open an issue or submit a pull request in [Vba-actions/test-vba](https://github.com).
