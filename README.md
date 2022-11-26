# vscode-sphinx-seed

## Setup vscode

1. install vscode extension of `ms-vscode-remote.remote-containers`
    [https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers]

2. Ctrl+Shift+P -> `Reopen in Container`

## Crete sphinx project

Run command following:

```shell
sphinx-quickstart --no-batchfile --sep
```

The following directories will be created:

```shell
.
├── Makefile
├── build
└── source
    ├── _static
    ├── _templates
    ├── conf.py
    └── index.rst
```

See also details command line help: `sphinx-quickstart --help`

## Setup sphinx for use graph tools

As you can see in the Dockerfile it contains some diagram extensions. To enable them add the following to your conf.py:
If unset, the figure is visible in preview, but not when generating documentation.

### Use PlantUML

Add the following configuration to `conf.py`

```python
extensions += ['sphinxcontrib.plantuml']
plantuml = ['java', '-jar', '/usr/local/bin/plantuml.jar']
```

### Use blockdiags

Add the following configuration to `conf.py`

```python
extensions += [
    'sphinxcontrib.blockdiag',
    'sphinxcontrib.seqdiag',
    'sphinxcontrib.actdiag',
    'sphinxcontrib.nwdiag',
    'sphinxcontrib.rackdiag',
    'sphinxcontrib.packetdiag',
]
blockdiag_html_image_format = 'SVG'
seqdiag_html_image_format = 'SVG'
actdiag_html_image_format = 'SVG'
nwdiag_html_image_format = 'SVG'
rackiag_html_image_format = 'SVG'
packetdiag_html_image_format = 'SVG'
```

## Build document

### Create PDF

```shell
make latexpdf
```

### Create HTML

```shell
make html
```

## Trouble shooting

If you don't see the diagram, you may be able to fix it by checking
your esbonio settings and restart vscode.

```json
{
    "esbonio.sphinx.buildDir" : "${workspaceFolder}/build/html",
    "esbonio.sphinx.confDir"  : "${workspaceFolder}/source",
    "esbonio.sphinx.srcDir"   : "${workspaceFolder}/source"
}
```

see also: [https://docs.restructuredtext.net/articles/configuration]

## See also

- https://sphinx-users.jp/index.html
- https://www.sphinx-doc.org/ja/master/
