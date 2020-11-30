# Setup TeXLive Action

This action sets up TeXLive on GitHub Ubuntu instances.
By defaults, it installs a minimal environment (just the `texlive`, `cm-super`, `texlive-pictures`, and `texlive-latex-extra` Ubuntu packages).
However, you can customize your installation by listing the packages you need in a file of your choice, by default on `.github/texlive/requirements.txt`, by listing packages one per line.

The configuration is on an external file by choice: this allows you to reuse the same action configuration on multiple targets, allowing for code reuse and application of the "Don't Repeat Yourself" principle, e.g., by using [Autodelivery](https://github.com/marketplace/actions/autodelivery)

## Example usage

```yaml
jobs:
  Build-LaTeX:
    runs-on: ubuntu-latest
    steps:
      # Checkout the repository
      - name: Checkout
        uses: actions/checkout@v2
      - name: Install TeXLive
        # Actually pick a version, do not point on master, or the build won't be reproducible
        uses: DanySK/setup-texlive-action@master
        # You can omit the following if the default path is ok with you
        with:
          requirements-file: .github/texlive/requirements.txt
```
