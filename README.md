![Loupe](https://raw.githubusercontent.com/wincent/loupe/media/loupe-small.jpg)

## Intro<a name="loupe-intro" href="#user-content-loupe-intro"></a>

> "loupe (noun)<br />a small magnifying glass used by jewelers and watchmakers."

<p align="right"><a name="loupe-features" href="#user-content-loupe-features"><code>loupe-features</code></a></p>
Loupe enhances Vim's <strong>`search-commands`</strong> in four ways:

### 1. Makes the currently selected match easier to see<a name="loupe-1-makes-the-currently-selected-match-easier-to-see" href="#user-content-loupe-1-makes-the-currently-selected-match-easier-to-see"></a>

When searching using <strong>`/`</strong>, <strong>`?`</strong>, <strong>`star`</strong>, <strong>`#`</strong>, <strong>`n`</strong>, <strong>`N`</strong> or similar, it can be hard to see the "current" match from among all the matches that 'hlsearch' highlights. Loupe makes the currently selected match easier to see by:

- Applying a different <strong>`:highlight`</strong> group (by default, <strong>`hl-IncSearch`</strong>) to the match under the cursor.
- Keeping the matching line centered within the window when jumping between matches with <strong>`n`</strong> and <strong>`N`</strong>.

### 2. Applies sane pattern syntax by default<a name="loupe-2-applies-sane-pattern-syntax-by-default" href="#user-content-loupe-2-applies-sane-pattern-syntax-by-default"></a>

Loupe makes "very magic" (<strong>`/\v`</strong>) syntax apply by default when searching. This is true even if you initiate a search via a novel means, such as from a visual selection or with a complicated <strong>`:range`</strong> prefix.

This means that you can use a pattern syntax closer to the familiar regular expression syntax from languages such as Perl, Ruby, JavaScript (indeed, most other modern languages that support regular expressions).

### 3. Provides a shortcut to remove search highlighting<a name="loupe-3-provides-a-shortcut-to-remove-search-highlighting" href="#user-content-loupe-3-provides-a-shortcut-to-remove-search-highlighting"></a>

Loupe maps <leader>n to quickly remove all 'hlsearch' highlighting (although you can provide an alternative mapping of your choosing or suppress the feature entirely).

### 4. Sensible defaults for search-related features<a name="loupe-4-sensible-defaults-for-search-related-features" href="#user-content-loupe-4-sensible-defaults-for-search-related-features"></a>

Loupe provides reasonable defaults for most search-related Vim settings to provide a good "out of the box" experience. For more details, or to see how to override Loupe's settings, see <strong>[`loupe-overrides`](#user-content-loupe-overrides)</strong>.

## Installation<a name="loupe-installation" href="#user-content-loupe-installation"></a>

To install Loupe, use your plug-in management system of choice.

If you don't have a "plug-in management system of choice", I recommend Pathogen (https://github.com/tpope/vim-pathogen) due to its simplicity and robustness. Assuming that you have Pathogen installed and configured, and that you want to install Loupe into `~/.vim/bundle`, you can do so with:

```
git clone https://github.com/wincent/loupe.git ~/.vim/bundle/loupe
```

Alternatively, if you use a Git submodule for each Vim plug-in, you could do the following after `cd`-ing into the top-level of your Git superproject:

```
git submodule add https://github.com/wincent/loupe.git ~/vim/bundle/loupe
git submodule init
```

To generate help tags under Pathogen, you can do so from inside Vim with:

```
:call pathogen#helptags()
```

## Overrides<a name="loupe-overrides" href="#user-content-loupe-overrides"></a>

Loupe sets a number of search-related Vim settings to reasonable defaults in order to provide a good "out of the box" experience:

<p align="right"><a name="loupe-history-override" href="#user-content-loupe-history-override"><code>loupe-history-override</code></a></p>
'history'

Increased to 1000, to increase the number of previous searches remembered. Note that Loupe only applies this setting if the current value of 'history' is less than 1000.

<p align="right"><a name="loupe-hlsearch-override" href="#user-content-loupe-hlsearch-override"><code>loupe-hlsearch-override</code></a></p>
'hlsearch'

Turned on (when there is a previous search pattern, highlight all its matches).

<p align="right"><a name="loupe-incsearch-override" href="#user-content-loupe-incsearch-override"><code>loupe-incsearch-override</code></a></p>
'incsearch'

Turned on (while typing a search command, show where the pattern matches, as it was typed so far).

<p align="right"><a name="loupe-ignorecase-override" href="#user-content-loupe-ignorecase-override"><code>loupe-ignorecase-override</code></a></p>
'ignorecase'

Turned on (to ignore case in search patterns).

<p align="right"><a name="loupe-shortmess-override" href="#user-content-loupe-shortmess-override"><code>loupe-shortmess-override</code></a></p>
'shortmess'

Adds "s", which suppresses the display of "search hit BOTTOM, continuing at TOP" and "search hit TOP, continuing at BOTTOM" messages.

<p align="right"><a name="loupe-smartcase-override" href="#user-content-loupe-smartcase-override"><code>loupe-smartcase-override</code></a></p>
'smartcase'

Turned on (overrides 'ignorecase', making the search pattern case-sensitive whenever it containers uppercase characters).

To override any of these choices, you can place overrides in an <strong>`after-directory`</strong> (ie. `~/.vim/after/plugin/loupe.vim`). For example:

```
 " Override Loupe's 'history' setting from 1000 to 10000.
 set history=10000

 " Reset Loupe's 'incsearch' back to Vim default.
 set incsearch&vim

 " Remove unwanted 's' from 'shortmess'.
 set shortmess-=s
```

## Related<a name="loupe-related" href="#user-content-loupe-related"></a>

Just as Loupe aims to improve the within-file search experience, Ferret does the same for multi-file searching and replacing:

- https://github.com/wincent/ferret

## Website<a name="loupe-website" href="#user-content-loupe-website"></a>

The official Loupe source code repo is at:

- http://git.wincent.com/loupe.git

A mirror exists at:

- https://github.com/wincent/loupe

Official releases are listed at:

- http://www.vim.org/scripts/script.php?script_id=5215

## License<a name="loupe-license" href="#user-content-loupe-license"></a>

Copyright 2015-present Greg Hurrell. All rights reserved.

Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:

1. Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.

2. Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.

THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDERS OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.

## Development<a name="loupe-development" href="#user-content-loupe-development"></a>

### Contributing patches<a name="loupe-contributing-patches" href="#user-content-loupe-contributing-patches"></a>

Patches can be sent via mail to greg@hurrell.net, or as GitHub pull requests at: https://github.com/wincent/loupe/pulls

### Cutting a new release<a name="loupe-cutting-a-new-release" href="#user-content-loupe-cutting-a-new-release"></a>

At the moment the release process is manual:

- Perform final sanity checks and manual testing
- Update the <strong>[`loupe-history`](#user-content-loupe-history)</strong> section of the documentation
- Verify clean work tree:

```
git status
```

- Tag the release:

```
git tag -s -m "$VERSION release" $VERSION
```

- Publish the code:

```
git push origin master --follow-tags
git push github master --follow-tags
```

- Produce the release archive:

```
git archive -o loupe-$VERSION.zip HEAD -- .
```

- Upload to http://www.vim.org/scripts/script.php?script_id=5215

## Authors<a name="loupe-authors" href="#user-content-loupe-authors"></a>

Loupe is written and maintained by Greg Hurrell <greg@hurrell.net>.

The original idea for the <strong>`g:LoupeHighlightGroup`</strong> feature was taken from Damian Conway's Vim set-up:

- https://github.com/thoughtstream/Damian-Conway-s-Vim-Setup/blob/master/plugin/hlnext.vim

Which he discussed in his "More Instantly Better Vim" presentation at OSCON 2013:

- https://www.youtube.com/watch?v=aHm36-na4-4

## History<a name="loupe-history" href="#user-content-loupe-history"></a>

### 1.0 (28 December 2015)<a name="loupe-10-28-december-2015" href="#user-content-loupe-10-28-december-2015"></a>

- Renamed the <strong>`<Plug>LoupeClearHighlight`</strong> mapping to <strong>[`<Plug>(LoupeClearHighlight)`](#user-content-plugloupeclearhighlight)</strong>.

### 0.1 (5 July 2015)<a name="loupe-01-5-july-2015" href="#user-content-loupe-01-5-july-2015"></a>

- Initial release, extracted from my dotfiles (https://github.com/wincent/wincent).

## Mappings<a name="loupe-mappings" href="#user-content-loupe-mappings"></a>

### `<Plug>(LoupeClearHighlight)`<a name="loupe-plugloupeclearhighlight" href="#user-content-loupe-plugloupeclearhighlight"></a>

Loupe maps <leader>n to <strong>[`<Plug>(LoupeClearHighlight)`](#user-content-plugloupeclearhighlight)</strong>, which clears all visible highlights (like <strong>`:nohighlight`</strong> does). To use an alternative mapping instead, create a different one in your <strong>`.vimrc`</strong> instead using <strong>`:nmap`</strong>:

```
" Instead of <leader>n, use <leader>x.
nmap <leader>x <Plug>(LoupeClearHighlight)
```

Note that Loupe will not try to set up its <leader>n mapping if any of the following are true:

- A mapping for <leader>n already exists.
- An alternative mapping for <strong>[`<Plug>(LoupeClearHighlight)`](#user-content-plugloupeclearhighlight)</strong> has already been set up from a <strong>`.vimrc`</strong>.
- The mapping has been suppressed by setting <strong>`g:LoupeClearHighlightMap`</strong> to 1 in your <strong>`.vimrc`</strong>.

## Options<a name="loupe-options" href="#user-content-loupe-options"></a>

<p align="right"><a name="gloupehighlightgroup" href="#user-content-gloupehighlightgroup"><code>g:LoupeHighlightGroup</code></a></p>
### `g:LoupeHighlightGroup` (string, default: IncSearch)<a name="loupe-gloupehighlightgroup-string-default-incsearch" href="#user-content-loupe-gloupehighlightgroup-string-default-incsearch"></a>

Specifies the <strong>`:highlight`</strong> group used to emphasize the match currently under the cursor for the current search pattern. Defaults to "IncSearch" (ie. <strong>`hl-IncSearch`</strong>). For example:

```
let g:LoupeHighlightGroup='Error'
```

To prevent any special highlighting from being applied, set this option to "" (ie. the empty string).

<p align="right"><a name="gloupeloaded" href="#user-content-gloupeloaded"><code>g:LoupeLoaded</code></a></p>
### `g:LoupeLoaded` (any, default: none)<a name="loupe-gloupeloaded-any-default-none" href="#user-content-loupe-gloupeloaded-any-default-none"></a>

To prevent Loupe from being loaded, set <strong>`g:LoupeLoaded`</strong> to any value in your <strong>`.vimrc`</strong>. For example:

```
let g:LoupeLoaded=1
```

<p align="right"><a name="gloupeclearhighlightmap" href="#user-content-gloupeclearhighlightmap"><code>g:LoupeClearHighlightMap</code></a></p>
### `g:LoupeClearHighlightMap` (boolean, default: 1)<a name="loupe-gloupeclearhighlightmap-boolean-default-1" href="#user-content-loupe-gloupeclearhighlightmap-boolean-default-1"></a>

Controls whether to set up the <strong>[`<Plug>(LoupeClearHighlight)`](#user-content-plugloupeclearhighlight)</strong> mapping. To prevent any mapping from being configured, set to 0:

```
let g:LoupeClearHighlightMap=0
```

<p align="right"><a name="gloupeverymagic" href="#user-content-gloupeverymagic"><code>g:LoupeVeryMagic</code></a></p>
### `g:LoupeVeryMagic` (boolean, default: 1)<a name="loupe-gloupeverymagic-boolean-default-1" href="#user-content-loupe-gloupeverymagic-boolean-default-1"></a>

Controls whether "very magic" pattern syntax (<strong>`/\v`</strong>) is applied by default. To disable, set to 0:

```
let g:LoupeVeryMagic=0
```

<p align="right"><a name="gloupecenterresults" href="#user-content-gloupecenterresults"><code>g:LoupeCenterResults</code></a></p>
### `g:LoupeCenterResults` (boolean, default: 1)<a name="loupe-gloupecenterresults-boolean-default-1" href="#user-content-loupe-gloupecenterresults-boolean-default-1"></a>

Controls whether the match's line is vertically centered within the window when jumping (via <strong>`n`</strong>, <strong>`N`</strong> etc). To disable, set to 0:

```
let g:LoupeCenterResults=0
```
