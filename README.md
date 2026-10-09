# factor CLI

Release binaries for `factor`, the command-line tool for
[Factor](https://getfactor.dev): run a script or a project on a rented GPU
with one command. Nothing is developed here: every release is built, tested
and signed by the release workflow of the (private) source repository and
published to this one.

## Install

**macOS** (Apple Silicon and Intel)

```bash
brew install --cask feweir/tap/factor
```

**Linux and macOS** (x86-64 and ARM64)

```bash
curl -fsSL https://getfactor.dev/install.sh | sh
```

`.deb` and `.rpm` packages are attached to every release.

**Windows** (x86-64 and ARM64)

```powershell
scoop bucket add factor https://github.com/feweir/scoop-bucket
scoop install factor
```

Or download an archive from [Releases](https://github.com/feweir/factory-cli/releases).

Then:

```bash
factor auth login
```

Documentation: [getfactor.dev/docs](https://getfactor.dev/docs).

## Verify a download

Every release is signed with [Sigstore](https://sigstore.dev). The signature
names the workflow that built it:

```bash
cosign verify-blob checksums.txt \
  --certificate checksums.txt.pem \
  --signature checksums.txt.sig \
  --certificate-identity-regexp 'https://github.com/feweir/factory/.github/workflows/release.yml@refs/tags/.*' \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com

sha256sum --check --ignore-missing checksums.txt
```
