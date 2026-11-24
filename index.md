---
title: Silica Language and Compiler
layout: default
---

<div class="masthead"><img src="{{ '/silica_icon_small.png' | relative_url }}" alt="Silica" width="256" height="256"><span class="masthead-tagline">Coordinating, promoting, and overseeing the development of the Silica language</span></div>

The Silica Language and Compiler organization exists to coordinate, promote, and oversee the development of the Silica language, its compiler, and the tooling and extensions — reusable code — that grow around them.

Silica is a memory-safe, functional systems language. The compiler rejects unsafe or accidental behavior at compile time, with errors you can act on. Effects are explicit, actors pass messages, and memory is region-based with no garbage collector. It is designed for bare-metal systems development and also supports applications hosted by operating systems. The toolchain builds and reproduces itself on macOS (Apple Silicon), Linux on AArch64 and Linux on x86-64, and cross-compiles for the OS-free ESP32-S3.

The language itself is documented on the [Silica documentation site]({{ site.docs_url }}): why Silica, two books, the design principles, and how to build the compiler.

## Projects

Every public repository in the organization. The tabs at the top of the page link to the same repositories. Where the projects stand today, and what you can do with them, is on the [Project Status]({{ '/project-status/' | relative_url }}) page.

{% assign groups = "language|The language and its compiler,tools|Tooling and examples,extensions|Extensions,org|The organization" | split: "," %}
{% for g in groups %}
{% assign parts = g | split: "|" %}
{% assign members = site.repos | where: "group", parts[0] %}
{% if members.size > 0 %}
### {{ parts[1] }}

<div class="cards">
{%- for r in members %}
  <a class="card" href="{{ site.github_org }}/{{ r.name }}"><b>{{ r.title }}</b><span>{{ r.summary }}</span></a>
{%- endfor %}
</div>
{% endif %}
{% endfor %}

## Get started

Install the `silica` command. The first time it runs, it downloads the latest released compiler for your machine:

```bash
curl -fsSL https://github.com/Silica-Language-and-Compiler/silica-cli/releases/latest/download/install.sh | bash
```

Then clone [silica-examples]({{ site.github_org }}/silica-examples) and run one with `silica run hello-world`.

```silica
module main;

fn add(a: int64, b: int64) -> int64 {
    a + b
}

fn main() -> atom {
    case add(20, 1) * 2 of {
        42: int64 -> :ok;
        _: int64 -> :error
    }
}
```

To learn the language, start with [Learn to Program]({{ site.docs_url }}learn-programming/) if you have never written a program, or [Silica for Programmers]({{ site.docs_url }}learn-silica/) if you already write software.

## Get involved

Silica's security story and runtime architecture are being shaped in the open. The [Participate]({{ site.docs_url }}participate/) page organizes in-flight work, the [roadmap]({{ site.github_org }}/silica/blob/main/ROADMAP.md) is the authoritative checklist, and [CONTRIBUTING.md]({{ site.github_org }}/silica/blob/main/CONTRIBUTING.md) explains how to open issues and pull requests. New tooling and extensions are welcome as repositories in the organization.

<div class="motto"><img src="{{ '/silica_icon_emoji.png' | relative_url }}" alt=""><p>Motto: Secure by default at compile time — fail soft, never fail silent</p></div>
