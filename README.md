# Setup

Requires `mkdocs` to be installed

Checkout this repo alongside `github.io` repo

```
mkdir site
git clone git@github.com:awalford16/awalford16.github.io.git ./site/awalford16.github.io
git clone git@github.com:awalford16/mkdocs-site.git ./site/mkdocs
```

Create development environment

```
cd mkdocs
python3 -m venv venv
. ./venv/bin/activate

pip install -r requirements.txt
```

Build and push to GH:

```
make build
```
