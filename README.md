# Node.js 12 Packages

This repository hosts the `.deb` package for the final release of Node.js 12, `v12.22.12`. It is intended for use in legacy systems that still require Node.js 12, as it has reached its End of Life (EOL).

---

## Why This Repository?

Node.js 12 is no longer maintained, and its official repositories may become unavailable in the future. This repository ensures you have continued access to the Node.js 12.22.12 package for legacy projects.

---

## Compatibility Note

The `.deb` package in this repository has been modified to replace the `python-minimal` dependency with `python2-minimal`. This change ensures compatibility with Debian Bullseye and newer distributions. **Older versions of Debian (e.g., Buster) are not supported.**

---

## Usage

Follow these steps to download and install Node.js 12.22.12:

### 1. Download the Package

```bash
curl -O https://raw.githubusercontent.com/DeadlockDruid/node_12/nodejs_12.22.12.deb
```
````

### 2. Install the Package

```bash
sudo dpkg -i nodejs_12.22.12.deb
```

### 3. Fix Missing Dependencies (if required)

```bash
sudo apt-get install -f -y
```

---

## Repository Structure

This repository is structured to support the v12.22.12 package, with room for additional versions if necessary:

```
node_12/
├── nodejs_12.22.12.deb
└── README.md
```

---

## Notes

- **Security Disclaimer**: Node.js 12 is no longer maintained, so it will not receive security updates. Use this package only for legacy systems and migrate to a supported version (Node.js 16 or 18) as soon as possible.
- **Compatibility**: Ensure that your environment is running Debian Bullseye or newer before using this package. The dependency `python2-minimal` is required for installation.

---

## Additional Information

To learn more about Node.js lifecycle and EOL announcements, visit the official [Node.js Releases page](https://nodejs.org/en/about/releases/).

---

## Example Usage in Docker

If you are using this package in Docker, here’s an example Dockerfile snippet:

```dockerfile
FROM debian:bullseye

# Install Node.js 12.22.12
RUN apt-get update && apt-get install -y curl && \
    curl -O https://raw.githubusercontent.com/DeadlockDruid/node_12/nodejs_12.22.12.deb && \
    dpkg -i nodejs_12.22.12.deb && \
    apt-get install -f -y

# Verify Node.js Installation
RUN node -v
```
