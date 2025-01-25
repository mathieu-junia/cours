---
marp: true
theme: gaia
markdown.marp.enableHtml: true
paginate: true
footer: ISEN

---

<style>

section {
  background-color: #fefefe;
  color: #333;
}

img[alt~="center"] {
  display: block;
  margin: 0 auto;
}
blockquote {
  background: #ffedcc;
  border-left: 10px solid #d1bf9d;
  margin: 1.5em 10px;
  padding: 0.5em 10px;
}
blockquote:before{
  content: unset;
}
blockquote:after{
  content: unset;
}
</style>

<!-- _class: lead -->

# uv: Python Package Management

  "Everything should be made as simple as possible, but not simpler."

  – Albert Einstein

---

### What is uv ?

[uv](https://docs.astral.sh/uv/) is an **extremely fast Python package installer and resolver**, **written in Rust**, and designed as a drop-in replacement for `pip` and pip-tools workflows.

* **Speed and Efficiency**: uv is extremely fast.
* **Disk Space Efficiency**: uv uses a global cache to minimize redundancy, ensuring that identical packages are stored only once, regardless of how many projects require them.
* **Cross-Platform Compatibility**: Windows, macOS, Linux.
* **Virtual Environment Capabilities** `uv venv`, `uv venv myenv --python 3.12`.

---

## Installation

* macOS, Linux

```sh
curl -LsSf https://astral.sh/uv/install.sh | sh
```
or
```sh
wget -qO- https://astral.sh/uv/install.sh | sh
```
* Windows

```sh
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

---

## Creating project

* `uv init`
* `uv init --app`
* `uv init --lib`
* `uv init --app --python 3.12`

---

## Adding dependencies

`uv add`
`uv add --dev`
`uv add --optional`
`uv remove`

---

## Syncing already existing projects

`uv sync`

