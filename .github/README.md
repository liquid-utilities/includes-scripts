# Includes Scripts
[heading__top]:
  #includes-scripts
  "&#x2B06; Liquid tool for translating FrontMater into `script` HTML tags"


Liquid tool for translating FrontMater into `script` HTML tags


## [![Byte size of Includes Scripts][badge__main__includes_scripts__source_code]][includes_scripts__main__source_code] [![Open Issues][badge__issues__includes_scripts]][issues__includes_scripts] [![Open Pull Requests][badge__pull_requests__includes_scripts]][pull_requests__includes_scripts] [![Latest commits][badge__commits__includes_scripts__main]][commits__includes_scripts__main] [![License][badge__license]][branch__current__license]


---


- [:arrow_up: Top of Document][heading__top]
- [:building_construction: Requirements][heading__requirements]
- [:zap: Quick Start][heading__quick_start]
  - [:memo: Edit Your ReadMe File][heading__your_readme_file]
  - [:floppy_disk: Commit and Push][heading__commit_and_push]
  - [&#x1F9F0; Usage][heading__usage]
- [&#x1F5D2; Notes][heading__notes]
- [:chart_with_upwards_trend: Contributing][heading__contributing]
  - [:trident: Forking][heading__forking]
  - [:currency_exchange: Sponsor][heading__sponsor]
- [:card_index: Attribution][heading__attribution]
- [:balance_scale: Licensing][heading__license]


---



## Requirements
[heading__requirements]:
  #requirements
  "&#x1F3D7; Prerequisites and/or dependencies that this project needs to function properly"


This repository depends upon [Jekyll][jekyll_rb__home] which is supported by
[GitHub Pages][github_docs__github_pages__jekyll], further details about setup
can be found from [documentation][jekyll_rb__github_pages] published by the
Jekyll maintainers regarding GitHub Pages.


______


## Quick Start
[heading__quick_start]:
  #quick-start
  "&#9889; Perhaps as easy as one, 2.0,..."


This repository encourages the use of Git Submodules to track dependencies


**Bash Variables**


```bash
_module_name='includes-scripts'
_module_https_url="https://github.com/liquid-utilities/includes-scripts.git"
_module_base_dir='_includes/modules'
_module_path="${_module_base_dir}/${_module_name}"
```


**Bash Submodule Commands**


```bash
cd "<your-git-project-path>"

git checkout gh-pages
mkdir -vp "${_module_base_dir}"

git submodule add\
 -b main --name "${_module_name}"\
 "${_module_https_url}" "${_module_path}"
```


---


### Your ReadMe File
[heading__your_readme_file]:
  #your-readme-file
  "&#x1F4DD; Suggested additions for your ReadMe.md file so everyone has a good time with submodules"


Suggested additions for your _`ReadMe.md`_ file so everyone has a good time
with submodules


```markdown
Clone with the following to avoid incomplete downloads


    git clone --recurse-submodules <url-for-your-project>


Update/upgrade submodules via


    git submodule update --init --merge --recursive
```


---


### Your Layout File
[heading__your_layout_file]:
  #your-layout-file
  "&#x26F2; "


Add an include statement,
_`{% include modules/includes-scripts/includes-scripts.html %}`_,
within the chosen Layout file, for example if utilizing the
[`minima/jekyll`](https://github.com/jekyll/minima) theme modifications may be
similar to...


`_includes/head.html`


```liquid
{% comment %}
---
authors: [ Jekyll ]
version: 2.5.1
license: MIT
url: https://github.com/jekyll/minima/
---
{% endcomment %}
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <meta name="viewport" content="width=device-width, initial-scale=1">
  {%- seo -%}
  <link rel="stylesheet" href="{{ "/assets/css/style.css" | relative_url }}">
  {%- feed_meta -%}
  {%- include custom-head.html -%}
  {%- include modules/includes-scripts/includes-scripts.html -%}
</head>
```


---


### Commit and Push
[heading__commit_and_push]:
  #commit-and-push
  "&#x1F4BE; It may be just this easy..."


```bash
git add .gitmodules
git add "${_module_path}"


## Add any changed files too


git commit -F- <<'EOF'
:heavy_plus_sign: Adds `liquid-utilities/includes-scripts#1` submodule



**Additions**


- `.gitmodules`, tracks submodules AKA Git within Git _fanciness_

- `README.md`, updates installation and updating guidance

- `_modules_/includes-scripts`, Liquid tool for translating FrontMater into `script` HTML tags
EOF


git push origin gh-pages
```


**:tada: Excellent :tada:** your project is now ready to begin unitizing code from this repository!

---


### Usage
[heading__usage]:
  #usage
  "&#x1F9F0; How to utilize this repository"


**Example post**


```markdown
---
title: Post title
description: Something about some thing
scripts:
  - src: assets/js/lib/tools.js
    defer: true
  - src: assets/js/main.js
    defer: true
---

... Post content...
```


**Example output**


```html
<head>
  <meta charset="utf-8">
  <meta http-equiv="X-UA-Compatible" content="IE=edge">
  <!-- ... -->
  <script src="/project-name/assets/js/lib/tools.js" defer></script>
  <script src="/project-name/assets/js/main.js" defer></script>
</head>
```


______


## Notes
[heading__notes]:
  #notes
  "&#x1F5D2; Additional things to keep in mind when developing"


This repository may not be feature complete and/or fully functional, Pull
Requests that add features or fix bugs are certainly welcomed.

Currently the following key/value configurations may be defined per-page/post;

- `src` relative path or absolute URL to script

- `type` default `text/javascript` may be MIME type, `module`, `importmap`, or
  custom data-block
> [MDN -- `<script>` -- `type`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script/type)

- `integrity` list of hashes that client may utilize to verify script integrity
> [MDN -- Subresource Integrity](https://developer.mozilla.org/en-US/docs/Web/Security/Subresource_Integrity)

- `fetchpriority` default `auto` (in most clients), may be explicitly defined
  to `high`, `low`, or `auto` to hint to browser the relative priority to use
  when fetching an external script

- `charset` (deprecated) modern documents _should_ use UTF-8 by default

- `language` (deprecated) the `type` attribute _should_ be used instead

- `crossorigin` allows/restricts CORS data sharing, such `window.onerror`, for
  externally linked scripts. May be set to `anonymous` or `use-credentials`
> [MDN -- HTML attribute: `crossorigin`](https://developer.mozilla.org/en-US/docs/Web/HTML/Attributes/crossorigin)

- `referrerpolicy` defines headers to send when fetching script, may be
  `no-referrer`, `no-referrer-when-downgrade`, `origin`, `same-origin`,
  `strict-origin`, `strict-origin-when-cross-origin` (default), `unsafe-url`

- `async` useful when order of download/execution does not need to be
  deterministic, because it allows browser to download scripts in parallel
> [MDN -- `<script>` -- `async`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script#async)

- `defer` useful for downloading scripts in parallel, but executing after
  document has been parsed and before firing `DOMContentLoaded` event.  Similar
  to `async`, as far as download behavior, but execution order is determined by
  order defined within document.

**Example of all FrontMater definable attributes**

```yaml
scripts:
  - src: assets/js/main.js
    type: text/javascript

    blocking:
      - render

    integrity:
      - sha256-9b8090de7cb40209b9819469e2a90a1f3966cd6035ec5969de81c97dbb068d36
      - sha512-9397574ef73b0d2f46f210400c5120cc0bc61b3b9d2bcab6ef1906828b83a0722cd6d2e2f8b4c8c71e304845df29d154bbdc4ce813459487eb875766f6109d9a

    fetchpriority: high
    charset: UTF-8
    language: text/javascript
    crossorigin: anonymous
    referrerpolicy: no-referrer

    defer: true
    async: false
```


______


## Contributing
[heading__contributing]:
  #contributing
  "&#x1F4C8; Options for contributing to includes-scripts and liquid-utilities"


Options for contributing to includes-scripts and liquid-utilities


---


### Forking
[heading__forking]:
  #forking
  "&#x1F531; Tips for forking includes-scripts"


Start making a [Fork][includes_scripts__fork_it] of this repository to an account that you have write permissions for.


- Add remote for fork URL. The URL syntax is _`git@github.com:<NAME>/<REPO>.git`_...


```bash
cd ~/git/hub/liquid-utilities/includes-scripts

git remote add fork git@github.com:<NAME>/includes-scripts.git
```


- Commit your changes and push to your fork, eg. to fix an issue...


```bash
cd ~/git/hub/liquid-utilities/includes-scripts


git commit -F- <<'EOF'
:bug: Fixes #42 Issue


**Edits**


- `<SCRIPT-NAME>` script, fixes some bug reported in issue
EOF


git push fork main
```


> Note, the `-u` option may be used to set `fork` as the default remote, eg.
> _`git push -u fork main`_ however, this will also default the `fork` remote
> for pulling from too! Meaning that pulling updates from `origin` must be done
> explicitly, eg. _`git pull origin main`_


- Then on GitHub submit a Pull Request through the Web-UI, the URL syntax is
  _`https://github.com/<NAME>/<REPO>/pull/new/<BRANCH>`_


> Note; to decrease the chances of your Pull Request needing modifications
> before being accepted, please check the
> [dot-github](https://github.com/liquid-utilities/.github) repository for
> detailed contributing guidelines.


---


### Sponsor
  [heading__sponsor]:
  #sponsor
  "&#x1F4B1; Methods for financially supporting liquid-utilities that maintains includes-scripts"


Thanks for even considering it!


Via Liberapay you may
<sub>[![sponsor__shields_io__liberapay]][sponsor__link__liberapay]</sub> on a
repeating basis.


Regardless of if you're able to financially support projects such as
includes-scripts that liquid-utilities maintains, please consider sharing
projects that are useful with others, because one of the goals of maintaining
Open Source repositories is to provide value to the community.


______


## Attribution
[heading__attribution]:
  #attribution
  "&#x1F4C7; Resources that where helpful in building this project so far."


- [GitHub -- `github-utilities/make-readme`](https://github.com/github-utilities/make-readme)

- [MDN -- `<script>`: The Script element](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script)


______


## License
[heading__license]:
  #license
  "&#x2696; Legal side of Open Source"


```
Liquid tool for translating FrontMater into `script` HTML tags
Copyright (C) 2023 S0AndS0

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU Affero General Public License as published
by the Free Software Foundation, version 3 of the License.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License
along with this program.  If not, see <https://www.gnu.org/licenses/>.
```


For further details review full length version of
[AGPL-3.0][branch__current__license] License.



[branch__current__license]:
  /LICENSE
  "&#x2696; Full length version of AGPL-3.0 License"

[badge__license]:
  https://img.shields.io/github/license/liquid-utilities/includes-scripts

[badge__commits__includes_scripts__main]:
  https://img.shields.io/github/last-commit/liquid-utilities/includes-scripts/main.svg

[commits__includes_scripts__main]:
  https://github.com/liquid-utilities/includes-scripts/commits/main
  "&#x1F4DD; History of changes on this branch"


[includes_scripts__community]:
  https://github.com/liquid-utilities/includes-scripts/community
  "&#x1F331; Dedicated to functioning code"


[issues__includes_scripts]:
  https://github.com/liquid-utilities/includes-scripts/issues
  "&#x2622; Search for and _bump_ existing issues or open new issues for project maintainer to address."

[includes_scripts__fork_it]:
  https://github.com/liquid-utilities/includes-scripts/fork
  "&#x1F531; Fork it!"

[pull_requests__includes_scripts]:
  https://github.com/liquid-utilities/includes-scripts/pulls
  "&#x1F3D7; Pull Request friendly, though please check the Community guidelines"

[includes_scripts__main__source_code]:
  https://github.com/liquid-utilities/includes-scripts/
  "&#x2328; Project source!"

[badge__issues__includes_scripts]:
  https://img.shields.io/github/issues/liquid-utilities/includes-scripts.svg

[badge__pull_requests__includes_scripts]:
  https://img.shields.io/github/issues-pr/liquid-utilities/includes-scripts.svg

[badge__main__includes_scripts__source_code]:
  https://img.shields.io/github/repo-size/liquid-utilities/includes-scripts


[sponsor__shields_io__liberapay]:
  https://img.shields.io/static/v1?logo=liberapay&label=Sponsor&message=liquid-utilities

[sponsor__link__liberapay]:
  https://liberapay.com/liquid-utilities
  "&#x1F4B1; Sponsor developments and projects that liquid-utilities maintains via Liberapay"


[jekyll_rb__home]:
  https://jekyllrb.com/
  "Jekyll home page"

[jekyll_rb__github_pages]:
  https://jekyllrb.com/docs/github-pages/
  "Jekyll documentation for GitHub Pages setup"

[github_docs__github_pages__jekyll]:
  https://docs.github.com/en/github/working-with-github-pages/setting-up-a-github-pages-site-with-jekyll
  "GitHub Pages documentation on Jekyll setup"
