# 🐍 Easy & Flexible Python Version Management with pyenv

## 🚀 Overview

This guide helps you install and manage **multiple Python versions** on Linux (Ubuntu, Debian, etc.) using [pyenv](https://github.com/pyenv/pyenv).
With `pyenv`, you can switch Python versions per project or globally without breaking system Python — perfect for developers, data scientists, and hobbyists.

---

## 🧰 Prerequisites

Before installing Python versions via `pyenv`, make sure your system has all required build tools and libraries:

```bash
sudo apt update
sudo apt install -y \
  build-essential \
  curl \
  libssl-dev \
  zlib1g-dev \
  libbz2-dev \
  libreadline-dev \
  libsqlite3-dev \
  libffi-dev \
  liblzma-dev \
  tk-dev \
  uuid-dev \
  libncurses5-dev \
  libgdbm-dev \
  libnss3-dev
```

---

## ⚙️ Step 1. Install pyenv

Run the following command to install `pyenv`:

```bash
curl https://pyenv.run | bash
```

This will automatically download and configure `pyenv` into your `~/.pyenv` directory.

---

## 🧩 Step 2. Configure your shell

Append these lines to your `~/.bashrc` (or `~/.bash_profile` if using macOS):

```bash
cat << 'EOF' >> ~/.bashrc

# Pyenv configuration
export PYENV_ROOT="$HOME/.pyenv"
[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin:$PATH"
eval "$(pyenv init - bash)"
EOF
```

Then reload your shell:

```bash
source ~/.bashrc
```

Verify the installation:

```bash
pyenv --version
```

---

## 🐍 Step 3. Install a Python version

Now you can install any available Python version (for example, 3.14.0):

```bash
pyenv install 3.14.0
```

List all available versions:

```bash
pyenv install --list
```

---

## 🌍 Step 4. Set global or local Python versions

### Set the global (default) version:

```bash
pyenv global 3.14.0
```

### Set a version only for a specific project:

```bash
cd my-project/
pyenv local 3.12.3
```

Now this project will automatically use Python 3.12.3.

---

## 🧠 Step 5. Verify your setup

Check which Python version is active:

```bash
python --version
which python
```

You should see your `pyenv`-managed Python path, e.g.:

```
/home/username/.pyenv/shims/python
```

---

## 🧼 Optional: Update pyenv

To keep pyenv and plugin lists up to date:

```bash
cd ~/.pyenv && git pull
```

---

## 💡 Pro Tips

* Use [`pyenv-virtualenv`](https://github.com/pyenv/pyenv-virtualenv) to create isolated environments per project.
* Add this alias to your `.bashrc` for quick rehashing:

  ```bash
  alias pyrefresh="pyenv rehash && pyenv versions"
  ```
* Use `pyenv doctor` (via `pyenv-doctor` plugin) to check for missing dependencies.

---

## 🧽 Example Usage

```bash
pyenv install 3.11.9
pyenv install 3.12.7
pyenv global 3.12.7
python --version
# Python 3.12.7

cd ~/projects/legacy-app
pyenv local 3.11.9
python --version
# Python 3.11.9
```

---

## ✅ Summary

| Action                  | Command                          |
| ----------------------- | -------------------------------- |
| Install pyenv           | `curl https://pyenv.run \| bash` |
| Add to `.bashrc`        | (see config above)               |
| Install Python version  | `pyenv install 3.14.0`           |
| Set global version      | `pyenv global 3.14.0`            |
| Set per-project version | `pyenv local 3.12.3`             |


