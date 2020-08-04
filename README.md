# pygments-promql

![Python package](https://github.com/pabluk/pygments-promql/workflows/Python%20package/badge.svg)

A PromQL lexer for Pygments.

This Python package provides a [Pygments](https://pygments.org/) lexer for the [Prometheus Query Language](https://prometheus.io/docs/prometheus/latest/querying/basics/). It allows Pygments and other tools ([Sphinx](https://sphinx-doc.org/), [Chroma](https://github.com/alecthomas/chroma), etc) to highlight PromQL queries.

![PromQL syntax highlighted](https://raw.githubusercontent.com/pabluk/pygments-promql/master/tests/example.png)

# Installation

## Using pip

To get the latest version from pypi.org:

```console
pip install pygments-promql
```

# Usage

## Command-line

*The following examples are using queries from [tests/example.promql](tests/example.promql)*

Showing colorized output in a terminal:

```console
pygmentize tests/example.promql
```

Or to generate a PNG file:

```console
pygmentize -f png -O "line_numbers=False,style=monokai" -o example.png tests/example.promql
```

## Python code

The following example:

```python
from pygments import highlight
from pygments.formatters import HtmlFormatter
from pygments_promql import PromQLLexer

query = 'http_requests_total{handler="/api/comments"}'
print(highlight(query, PromQLLexer(), HtmlFormatter()))
```

will generate this HTML output:

```html
<div class="highlight">
    <pre>
        <span></span>
	<span class="nv">http_requests_total</span>
	<span class="p">{</span>
	<span class="nl">handler</span>
	<span class="o">=</span>
	<span class="s">&quot;/api/comments&quot;</span>
	<span class="p">}</span>
	<span class="w"></span>
    </pre>
</div>
```

Use `HtmlFormatter(noclasses=True)` to include CSS inline styles on every `<span>` tag.


# Testing

If you want to test, play or contribute to this repo:

```console
git clone https://github.com/pabluk/pygments-promql.git
cd pygments-promql/
pip install -r requirements.txt
pip install -e .
pytest -v
```
