<h1> A Life Configuring Emacs </h1>

<p align="center"><img src="emacs-logo.png" width=150 height=150/></p>
<p align="center">
	<a href="<https://www.gnu.org/software/emacs/>">        
	<img src="<https://img.shields.io/badge/GNU%20Emacs-26.1-b48ead.svg?style=plastic"/>></a>
	<a href="<https://orgmode.org/>"><img src="<https://img.shields.io/badge/org--mode-9.2.3-489a9f.svg?style=plastic"/>></a>
</p>

<h3> My Literate Setup </h3>

I enjoy reading others' *literate* configuration files and incorporating what I learn
into my own. The result is a sufficiently well-documented and accessible read that yields
a stylish and functional system (•̀ᴗ•́)و

This `README.md` has been automatically generated from my configuration
and its contents below could also be read in blog format, with *colour*, or as colourful PDF,
[here](https://alhassy.github.io/init/). Enjoy :smile:


# Table of Contents

1.  [Why Emacs?](#org4570900)
2.  [Booting Up](#org1be082b)
    1.  [`~/.emacs` vs. `init.org`](#orgfd44901)
    2.  [`use-package` &#x2013;The start of `init.el`](#org18b7f69)
    3.  [`magit` &#x2013;Emacs' porcelain interface to git](#orgdc3f922)
    4.  [Fix spelling as you type &#x2013;and a thesaurus too!](#org9c5f75e)
    5.  [Using a Grammar & Style Checker](#org81f2284)
    6.  [Unicode Input via Agda Input](#orgf7319d6)
    7.  [Locally `toggle` a variable](#orgf1620f9)
    8.  [Syncing to the System's `$PATH`](#org2928585)
    9.  [Keeping My System Up to Date](#org3dcc0b2)
    10. [Who am I? ─Using Gnus for Gmail](#org88f583c)
    11. [Using Emacs in any text area on my OS](#org73c18fd)
3.  [Cosmetics](#org8f5124f)
    1.  [Startup message: Emacs & Org versions](#org190da80)
    2.  [Persistent Scratch Buffer](#org32fcef1)
    3.  [Spaceline: A sleek mode line](#org2df07f7)
    4.  [Flashing when something goes wrong](#org537cb25)
    5.  [My to-do list: The initial buffer when Emacs opens up](#orge44afbd)
    6.  [Showing date, time, and battery life](#org7fa3ad9)
    7.  [Hiding Scrollbar, tool bar, and menu](#orgd5376ab)
    8.  [Increase/decrease text size](#org0635cca)
    9.  [Delete Selection mode](#org8133a01)
    10. [Highlight & complete parenthesis pair when cursor is near ;-](#orgfa405b2)
    11. [Minibuffer should display line and column numbers](#org077e109)
    12. [Neotree: Directory Tree Listing](#org52da597)
    13. [Window resizing using the golden ratio](#org1cbffaf):Disabled:
4.  [Life within Org-mode](#orgdc2185a)
    1.  [High Speed Literate Programming](#orgfb596cd)
    2.  [Using org-mode as a Day Planner](#orgc0bb58a)
    3.  [Automating Pomodoro &#x2013;Dealing with dreadful tasks](#org4b71928)
    4.  [Journaling](#org76bf3d6)
    5.  [Workflow States](#WorkflowStates)
    6.  [Clocking Work Time](#org94d4b01)
    7.  [Reveal.JS &#x2013; The HTML Presentation Framework](#org0d2c513)
    8.  [Coloured LaTeX using Minted](#org40792f9)
    9.  [Executing code from `src` blocks](#org39aa9ed)
    10. [Hiding Emphasise Markers & Inlining Images](#org2032c71)
    11. [Jumping without hassle](#org3f0fd34)
    12. [Folding within a subtree](#orgfc73d2f)
    13. [Making then opening html's from org's](#org7136174)
    14. [Making then opening pdf's from org's](#org9f6128d)
    15. [Interpret the Haskell source blocks in a file](#orgec76567)
5.  [Expected IDE Support](#orga605017)
    1.  [Backups](#orgc1cb02f)
    2.  [Mouse Editing Support](#org5b0e63c)
    3.  [Having a workspace manager in Emacs](#org03afc0a)
    4.  [Jump between windows using Cmd+Arrow & between recent buffers with Meta-Tab](#org505556b)
    5.  [Completion Frameworks](#org4dc92d9)
    6.  [Snippets &#x2013; Template Expansion](#org034c782)
6.  [Helpful Functions & Shortcuts](#org2a61b82)
    1.  [Bind `recompile` to `C-c C-m` &#x2013; “m” for “m”ake](#orgf5ce1f3)
    2.  [Reload buffer with `f5`](#org541739c)
    3.  [Kill to start of line](#org0fa6e12)
    4.  [`file-as-list` and `file-as-string`](#org75d6e92)
    5.  [`kill-other-buffers`](#orgc9e6076)
    6.  [Switching from 2 horizontal windows to 2 vertical windows](#orga03f57f)
    7.  [`re-replace-in-file`](#org8cb85ed)
    8.  [Obtaining Values of `#+KEYWORD` Annotations](#orgea7baba)
    9.  [Quickly pop-up a terminal, run a command, close it](#org4400e0a)
    10. [`C-x k` kills current buffer](#org7e99e69)
    11. [Publishing articles to my personal blog](#org2726e05)
7.  [Summary of Utilities Provided](#orge3cff49)

<p align="center">
	<a href="https://www.gnu.org/software/emacs/">        
        <img src="https://img.shields.io/badge/GNU%20Emacs-26.1-b48ead.svg?style=plastic"/></a>
	<a href="https://orgmode.org/"><img src="https://img.shields.io/badge/org--mode-9.2.3-489a9f.svg?style=plastic"/></a>
</p>

<div class="org-center">
**Abstract**
</div>

Herein I document the configurations I utilise with [Emacs](https://gnu.org/s/emacs).

As a [literate program](https://www.offerzen.com/blog/literate-programming-empower-your-writing-with-emacs-org-mode) file with [Org-mode](http://orgmode.org/), I am ensured optimal navigation
through my ever growing configuration files, ease of usability and reference
for peers, and, most importantly, better maintainability for myself!

Dear reader, when encountering a foreign command `X` I encourage you to execute `(describe-symbol 'X)`, or press `C-h o` with the cursor on `X`.
An elementary Elisp Cheat Sheet can be found [here.](https://github.com/alhassy/ElispCheatSheet)


<a id="org4570900"></a>

# Why Emacs?

*Emacs is a flexible platform for developing end-user applications* &#x2013;unfortunately it is generally perceived as
merely a text editor. Some people use it specifically for one or two applications.

For example, [writers](https://www.youtube.com/watch?v=FtieBc3KptU) use it as an interface for Org-mode and others use it as an interface for version
control with Magit. [Org](https://orgmode.org/index.html#sec-4) is an organisation tool that can be used for typesetting which subsumes LaTeX, generating many different
formats &#x2013;html, latex, pdf, etc&#x2013; from a single source, keeping track of [schedules](https://orgmode.org/worg/org-tutorials/index.html#orgff7b885) & task management, blogging, habit tracking, personal information management tool, and [much more](http://orgmode.org/worg/org-contrib/).
Moreover, its syntax is so [natural](https://karl-voit.at/2017/09/23/orgmode-as-markup-only/) that most people use it without even knowing!
For me, Org allows me to do literate programming: I can program and document at the same time,
with no need to separate the two tasks and with the ability to generate multiple formats and files from a single file.

> If you are a professional writer…Emacs outshines all other editing software 
> in approximately the same way that the noonday sun does the stars. 
> It is not just bigger and brighter; it simply makes everything else vanish.
> —[Neal Stephenson](http://project.cyberpunk.ru/lib/in_the_beginning_was_the_command_line/), *In the beginning was the command line*

Of course Emacs comes with the basic features of a text editor, but it is much more;
for example, it comes with a powerful notion of ‘undo’: Basic text editors have a single stream of undo,
yet in Emacs, we have a tree &#x2013;when we undo and make new edits, we branch off in our editing stream
as if our text was being version controlled as we type! &#x2013;We can even switch between such branches!

    ;; Allow tree-semantics for undo operations.
    (package-install 'undo-tree)
    (global-undo-tree-mode)
    (diminish 'undo-tree-mode)
    
    ;; Execute (undo-tree-visualize) then navigate along the tree to witness
    ;; changes being made to your file live!
    
    ;; Each node in the undo tree should have a timestamp.
    (setq undo-tree-visualizer-timestamps t)
    
    ;; Show a diff window displaying changes between undo nodes.
    (setq undo-tree-visualizer-diff t)

*Emacs is an extensible editor: You can make it into the editor of your dreams!*
You can make it suited to your personal needs.
If there's a feature you would like, a behaviour your desire, you can simply code that into Emacs with
a bit of Lisp. As a programming language enthusiast, for me Emacs is my default Lisp interpreter
and a customisable IDE that I use for other programming languages 
&#x2013;such as C, Haskell, Agda, Racket, and Prolog.
Moreover, being a Lisp interpreter, we can alter the look and feel of Emacs live, without having
to restart it &#x2013;e.g., press `C-x C-e` after the final parenthesis of `(scroll-bar-mode 0)`
to run the code that removes the scroll-bar.

> *I use Emacs every day. I rarely notice it. But when I do, it usually brings me joy.*
> ─[Norman Walsh](https://so.nwalsh.com/2019/03/01/emacs)

I have used Emacs as an interface for developing cheat sheets, for making my blog, and as an application 
for ‘interactively learning C’. If anything Emacs is more like an OS than just a text editor
&#x2013;“living within Emacs” provides an abstraction over whatever operating system my machine has:
[It's so easy to take everything with me.](https://www.fugue.co/blog/2015-11-11-guide-to-emacs.html) Moreover, the desire to mould Emacs to my needs has made me
a better programmer: I am now a more literate programmer and, due to Elisp's documentation-oriented nature, I actually take the time
and effort to make meaningful documentation &#x2013;even when the project is private and will likely only be seen by me.

> *Seeing Emacs as an editor is like seeing a car as a seating-accommodation.* &#x2013; [Karl Voit](https://karl-voit.at/2015/10/23/Emacs-is-not-just-an-editor/)

Consider reading ⋯ 

-   [A CEO's Guide to Emacs](https://www.fugue.co/blog/2015-11-11-guide-to-emacs.html) &#x2013;A non-programmer introduction to Emacs (•̀ᴗ•́)و
-   [“When did you start using Emacs” discussion on Reddit](https://www.reddit.com/r/emacs/comments/6fytr5/when_did_you_start_using_emacs/)
-   The [Emacs Mini Manual](http://tuhdo.github.io/emacs-tutor.html#orgheadline63), or
-   [“How to Learn Emacs”](https://david.rothlis.net/emacs/howtolearn.html)
-   [The Org-mode Reference Manual](https://orgmode.org/index.html#sec-4) or [Worg: Community-Written Docs](https://orgmode.org/worg/) which includes a [meta-tutorial](https://orgmode.org/worg/org-tutorials/index.html).
-   [Video Series on Why Emacs Rocks](http://emacsrocks.com/)

Remember: Emacs is a flexible platform for developing end-user applications; e.g., this configuration file
is at its core an Emacs Lisp program that yields the editor of my dreams 
&#x2013;it encourages me to grow and to be creative, and I hope the same for all who use it;
moreover, it reflects my personality such as what I value and what I neglect in my workflow.

Finally, as will be shown below, you can literally use [Emacs anywhere](https://github.com/zachcurry/emacs-anywhere/#usage)
for textually input in your operating system &#x2013;no copy-paste required.


<a id="org1be082b"></a>

# Booting Up


<a id="orgfd44901"></a>

## `~/.emacs` vs. `init.org`

Why not keep Emac's configurations in the `~/.emacs` file?
This is because the Emacs system may explicitly add, or alter, code
in it.

For example, execute the following

1.  `M-x customize-variable RET line-number-mode RET`
2.  Then press: `toggle`, `state`, then `1`.
3.  Now take a look: `(find-file "~/.emacs")`

Notice how additions to the file have been created by \`custom'.

As such, I've chosen to write my Emacs' initialisation configurations
in a file named `~/.emacs.d/init.org`: I have a literate configuration which
is then loaded using org-mode's tangling feature.
Read more about Emacs' initialisation configurations [here.](http://www.gnu.org/software/emacs/manual/html_node/emacs/Init-File.html#Init-File)

Off topic, I love tiling window managers and had been using [xmonad](https://xmonad.org)
until recently when I obtained a mac machine and now use 
[Amethyst](https://ianyh.com/amethyst/) &#x2013; “Tiling window manager for macOS along the lines of xmonad.”

Let the Emacs' gui insert default configurations and customisation
into its own file, not touching or altering my initialisation file.
For example, I tend to have local variables to produce `README.md`'s
and other matters, so Emacs' Custom utility will remember to not prompt
me each time for the safety of such local variables.

    ;; (eshell-command "touch ~/.emacs.d/custom.el")
    
    (setq custom-file "~/.emacs.d/custom.el")
    (load custom-file)


<a id="org18b7f69"></a>

## `use-package` &#x2013;The start of `init.el`

There are a few ways to install packages
&#x2013;run `C-h C-e` for a short overview.
The easiest, for a beginner, is to use the command `package-list-packages`
then find the desired package, press `i` to mark it for installation, then
install all marked packages by pressing `x`.

Alternatively, one uses the declarative configuration tool [use-package](https://github.com/jwiegley/use-package/) 
&#x2013;a meta-package that manages other packages and the way they interact.

Background:
Recently I switched to mac &#x2013;first time trying the OS.
I had to do a few `package-install`'s and it was annoying.
I'm looking for the best way to package my Emacs installation 
&#x2013;including my installed packages and configuration&#x2013;
so that I can quickly install it anywhere, say if I go to another machine.
It seems `use-package` allows me to configure and auto install packages. 
On a new machine, when I clone my `.emacs.d` and start emacs,
on the first start it should automatically install and compile 
all of my packages through `use-package` when it detects they're missing.

First we need the basic `package` module which not only allows us to obtain `use-package` but
acts as its kernel.

    ;; Make all commands of the “package” module present.
    (require 'package)
    
    ;; Speef up start up by not loading any packages at startup.
    ;; (setq package-enable-at-startup nil)
    ;; Look at the *Messages* buffer before setting this to nil, then after.
    
    ;; Internet repositories for new packages.
    (setq package-archives '(("org"       . "https://orgmode.org/elpa/")
                             ("gnu"       . "https://elpa.gnu.org/packages/")
                             ("melpa"     . "https://melpa.org/packages/")
                             ("melpa-stable" . "https://stable.melpa.org/packages/")     
                             ;; Maintainer is AWOL.
                             ;; ("marmalade" . "https://marmalade-repo.org/packages/")
                             ))
    
    ;; Actually get “package” to work.
    (package-initialize) 

We can now:

-   `M-x list-packages` to see all melpa packages that can install
    -   Not in alphabetical order, so maybe search with `C-s`.
-   For example to download the haskell mode: `M-x package-install RET haskell-mode RET`.
    -   Or maybe to install `unicode-fonts` ;-)
-   Read more at <http://ergoemacs.org/emacs/emacs_package_system.html> or 
    at <https://github.com/milkypostman/melpa>

We now bootstrap `use-package`,

    ;; Unless it's already installed, update the packages archives,
    ;; then install the most recent version of “use-package”.
    (unless (package-installed-p 'use-package)
      (package-refresh-contents)
      (package-install 'use-package))
    
    (require 'use-package)

We can now invoke `(use-package XYZ :ensure t)`
which should check for the `XYZ` package and make sure it is accessible. 
If not, the `:ensure t` part tells `use-package` to download it 
&#x2013;using `package.el`&#x2013;
and place it somewhere accessible, in `~/.emacs.d/elpa/` by default.

By default we would like to download packages, since I do not plan on installing them manually
by download `.el` files and placing them in the correct places on my system.

    (setq use-package-always-ensure t)

Here's an example use of `use-package`.
Below I have my “show recent files pop-up” command set to `C-x C-r`;
but what if I forget? This mode shows me all key completions when I type `C-x`, for example.
Moreover, I will be shown other commands I did not know about! Neato :-)

    ;; Making it easier to discover Emacs key presses.
    (use-package which-key 
     :diminish which-key-mode
     :init (which-key-mode)
     :config (which-key-setup-side-window-bottom)
             (setq which-key-idle-delay 0.05)
    )

The `:diminish` keyword indicates that we do not want the mode's name to be
shown to us in the modeline &#x2013;the area near the bottom of Emacs.
It does so by using the `diminish` package, so let's install that.

    (use-package diminish)

Here are other packages that I want to be installed onto my machine.

    ;; (package-refresh-contents)     ;; Always stay up to date.
    
    ;; Nice looking theme ^_^
    
    ;; this gives me an error for some reason
    ;; (use-package spacemacs-theme)
    
    ;; “C-x” t to toggle between light and dark themes.
    
    (defun my/toggle-theme () "Toggle between dark and light themes."
      (interactive)
      ;; Load dark if light is top-most enabled theme, else load light.
      (load-theme 
      (if (equal (car custom-enabled-themes) 'spacemacs-light) 
          'spacemacs-dark
          'spacemacs-light
      ) t )
      
      ;; The dark theme's modeline separator is ugly.
      ;; Keep reading below regarding “powerline”.
      ;; (setq powerline-default-separator 'arrow)
      ;; (spaceline-spacemacs-theme)
    )
    
    (global-set-key "\C-x\ t" 'my/toggle-theme)
    
    ;; Initially begin with the light theme.
    (load-theme 'spacemacs-light t)

The [Doom Themes](https://github.com/hlissner/emacs-doom-themes/tree/screenshots) also look rather appealing.
A showcase of many themes can be found [here](https://emacsthemes.com/).

    ;; Efficient version control.
    (use-package magit
      :config (global-set-key (kbd "C-x g") 'magit-status)
    )
    
    (use-package htmlize)
    ;; Main use: Org produced htmls are coloured.
    ;; Can be used to export a file into a coloured html.
    
    (use-package biblio)     ;; Quick BibTeX references, sometimes.
    
    ;; Get org-headers to look pretty! E.g., * → ⊙, ** ↦ ◯, *** ↦ ★
    ;; https://github.com/emacsorphanage/org-bullets
    (use-package org-bullets)
    (add-hook 'org-mode-hook 'org-bullets-mode)
    
    (use-package haskell-mode)
    
    (use-package dash)    ;; “A modern list library for Emacs”
    (use-package s   )    ;; “The long lost Emacs string manipulation library”.

Note:

-   [dash](https://github.com/magnars/dash.el): “A modern list library for Emacs”
    -   E.g., `(--filter (> it 10) (list 8 9 10 11 12))`
-   [s](https://github.com/magnars/s.el): “The long lost Emacs string manipulation library”.
    -   E.g., `s-trim, s-replace, s-join`.

Finally, since I've symlinked my `.emacs`:

    ;; Don't ask for confirmation when opening symlinked files.
    (setq vc-follow-symlinks t)


<a id="orgdc3f922"></a>

## `magit` &#x2013;Emacs' porcelain interface to git

Why use `magit` as the interface to the git version control system?
In a magit buffer nearly everything can be acted upon:
Press `return,` or `space`, to see details and `tab` to see children items, usually.

Below is my personal quick guide to working with magit.
A quick magit tutorial can be found on [jr0cket's blog](http://jr0cket.co.uk/2012/12/driving-git-with-emacs-pure-magic-with.html.html)

-   **`magit-init`:** Put a project under version control. 
    The mini-buffer will prompt you for the top level folder version.
    A `.git` folder will be created there.

-   **`magit-status` , `C-x g`:** See status in another buffer. Press `?` to see options,
    including:
    
    -   **`q`:** Quit magit, or go to previous magit screen.
    -   **`s`:** Stage, i.e., add, a file to version control.
        Add all untracked files by selecting the *Untracked files* title.
    -   **`k`:** Kill, i.e., delete a file locally.
    -   **`K`:** This' `(magit-file-untrack)` which does `git rm --cached`.
    -   **`i`:** Add a file to the project `.gitignore` file. Nice stuff =)
    -   **`u`:** Unstage a specific staged change highlighted by cursor.
        `C-u s` stages everything &#x2013;tracked or not.
    -   **`c`:** Commit a change.
        -   A new buffer for the commit message appears, you write it then
            commit with `C-c C-c` or otherwise cancel with `C-c C-k`.
            These commands are mentioned to you in the minibuffer when you go to commit.
        -   You can provide a commit to *each* altered chunk of text! 
            This is super neat, you make a series of local such commits rather
            than one nebulous global commit for the file. The `magit` interface
            makes this far more accessible than a standard terminal approach!
        -   You can look at the unstaged changes, select a *region*, using `C-SPC` as usual, 
            and commit only that if you want!
        -   When looking over a commit, `M-p/n` to efficiently go to previous or next altered sections.
        -   Amend a commit by pressing `a` on `HEAD`.
    
    -   **`d`:** Show differences, another `d` or another option.
        -   This is magit! Each hunk can be acted upon; e.g., `s` or `c` or `k` ;-)
        -   [The staging area is akin to a pet store; commiting is taking the pet home.](https://softwareengineering.stackexchange.com/a/119807/185815)
    -   **`v`:** Revert a commit.
    -   **`x`:** Undo last commit. Tantamount to `git reset HEAD~` when cursor is on most recent
        commit; otherwise resets to whatever commit is under the cursor.
    -   **`l`:** Show the log, another `l` for current branch; other options will be displayed.
        -   Here `space` shows details in another buffer while cursor remains in current
            buffer and, moreover, continuing to press `space` scrolls through the other buffer!
            Neato.
    -   **`P`:** Push.
    -   **`F`:** Pull.
    -   **`:`:** Execute a raw git command; e.g., enter `whatchanged`.
    
    The status buffer may be refreshed using `g`, and all magit buffer by `G`.
    
    Press `tab` to see collapsed items, such as what text has been changed.

Notice that every time you press one of these commands, a ‘pop-up’ of related git options
appears! Thus not only is there no need to memorize many of them, but this approach makes
discovering other commands easier.

Use `M-x (magit-list-repositories) RET` to list local repositories:

Below are the git repos I'd like to clone.

    ;; Do not ask about this variable when cloning.
    (setq magit-clone-set-remote.pushDefault t)
    
    (defun maybe-clone (remote local)
      "Clone a ‘remote’ repository if the ‘local’ directory does not exist.
        Yields ‘nil’ when no cloning transpires, otherwise yields “cloned-repo”.
      "
      (unless (file-directory-p local) 
         (magit-clone remote local) 
         (add-to-list 'magit-repository-directories `(,local   . 0))
         'cloned-repo)
    )
    
    ;; Set variable without asking.
    (setq magit-clone-set-remote.pushDefault 't)
    
    ;; Public repos
    (maybe-clone "https://github.com/alhassy/emacs.d.git" "~/.emacs.d/")
    (maybe-clone "https://github.com/alhassy/alhassy.github.io" "~/alhassy.github.io")
    (maybe-clone "https://github.com/alhassy/CheatSheet" "~/CheatSheet")
    (maybe-clone "https://github.com/alhassy/ElispCheatSheet" "~/ElispCheatSheet")
    (maybe-clone "https://github.com/alhassy/MyUnicodeSymbols" "~/MyUnicodeSymbols")
    (maybe-clone "https://github.com/alhassy/interactive-way-to-c" "~/interactive-way-to-c")
    (maybe-clone "https://github.com/alhassy/next-700-module-systems-proposal.git" "~/thesis-proposal")
    (maybe-clone "https://github.com/JacquesCarette/MathScheme" "~/MathScheme")
    
    ;; Private repos
    ;;
    (maybe-clone "https://gitlab.cas.mcmaster.ca/alhassm/CAS781" "~/cas781") ;; cat adventures
    ;;
    ;; (maybe-clone "https://gitlab.cas.mcmaster.ca/carette/cs3fp3.git" "~/3fp3")
    ;; (maybe-clone "https://gitlab.cas.mcmaster.ca/RATH/RATH-Agda"     "~/RATH-Agda")
    (maybe-clone "https://gitlab.cas.mcmaster.ca/3ea3-winter2019/assignment-distribution.git" "~/3ea3/assignment-distribution")
    (maybe-clone "https://gitlab.cas.mcmaster.ca/3ea3-winter2019/notes.git" "~/3ea3/notes")
    (maybe-clone "https://gitlab.cas.mcmaster.ca/3ea3-winter2019/assignment-development.git" "~/3ea3/assignment-development")
    (maybe-clone "https://gitlab.cas.mcmaster.ca/3ea3-winter2019/kandeeps.git" "~/3ea3/sujan")
    (maybe-clone "https://gitlab.cas.mcmaster.ca/3ea3-winter2019/horsmane.git" "~/3ea3/emily")
    (maybe-clone "https://gitlab.cas.mcmaster.ca/3ea3-winter2019/anderj12.git" "~/3ea3/jacob")
    ;; (maybe-clone "https://gitlab.cas.mcmaster.ca/alhassm/3EA3.git" "~/3ea3/_2018")  
    ;; (maybe-clone "https://gitlab.cas.mcmaster.ca/2DM3/LectureNotes.git" "~/2dm3")
    
    ;; Likely want to put a hook when closing emacs, or at some given time,
    ;; to show me this buffer so that I can ‘push’ if I haven't already!
    ;
    ; (magit-list-repositories)

Let's always notify ourselves of a file that has [uncommited changes](https://tpapp.github.io/post/check-uncommitted/)
&#x2013;we might have had to step away from the computer and forgotten to commit.

    (require 'magit-git)
    
    (defun my/magit-check-file-and-popup ()
      "If the file is version controlled with git 
      and has uncommitted changes, open the magit status popup."
      (let ((file (buffer-file-name)))
        (when (and file (magit-anything-modified-p t file))
          (message "This file has uncommited changes!")
          (when nil ;; Became annyoying after some time.
          (split-window-below)
          (other-window 1)
          (magit-status)))))
    
    ;; I usually have local variables, so I want the message to show
    ;; after the locals have been loaded.
    (add-hook 'find-file-hook 
      '(lambda () 
          (add-hook 'hack-local-variables-hook 'my/magit-check-file-and-popup)
       ))

Let's try this out:

    (progn (eshell-command "echo change-here >> ~/dotfiles/.emacs")
           (find-file "~/dotfiles/.emacs")
    )

In doubt, execute `C-h e` to jump to the `*Messages*` buffer.


<a id="org9c5f75e"></a>

## Fix spelling as you type &#x2013;and a thesaurus too!

I would like to check spelling by default.

-   **`C-;`:** Cycle through corrections for word at point.
-   **`M-$`:** Check and correct spelling of the word at point
-   **`M-x ispell-change-dictionary RET TAB`:** To see what dictionaries are available.

    (use-package flyspell
      :hook (
    	   (prog-mode . flyspell-prog-mode)
    	   (text-mode . flyspell-mode))
    )

Flyspell needs a spell checking tool, which is not included in Emacs. 
We install `aspell` spell checker using, say, homebrew via `brew install aspell`.
Note that Emacs' `ispell` is the interface to such a command line spelling utility.

    (setq ispell-program-name "/usr/local/bin/aspell")
    (setq ispell-dictionary "en_GB") ;; set the default dictionary
    
    (diminish 'flyspell-mode) ;; Don't show it in the modeline.

Enabling fly-spell for text-mode enables it for org and latex modes since they
derive from text-mode.

Let us select a correct spelling merely by clicking on a word.

    (eval-after-load "flyspell"
      ' (progn
         (define-key flyspell-mouse-map [down-mouse-3] #'flyspell-correct-word)
         (define-key flyspell-mouse-map [mouse-3] #'undefined)))

Colour incorrect works; default is an underline.

    (global-font-lock-mode t)
    (custom-set-faces '(flyspell-incorrect ((t (:inverse-video t)))))

Finally, save to user dictionary without asking:

    (setq ispell-silently-savep t)

Nowadays, I very rarely write non-literate programs, but if I do
I'd like to check spelling only in comments/strings. E.g.,

    (add-hook          'c-mode-hook 'flyspell-prog-mode)
    (add-hook 'emacs-lisp-mode-hook 'flyspell-prog-mode)

Use the thesaurus Emacs frontend [Synosaurus](https://github.com/hpdeifel/synosaurus) to avoid unwarranted repetition.

    (use-package synosaurus 
      :diminish synosaurus-mode
      :init    (synosaurus-mode)
      :config  (setq synosaurus-choose-method 'popup) ;; 'ido is default.
               (global-set-key (kbd "M-#") 'synosaurus-choose-and-replace)
    )

The thesaurus is powered by the Wordnet `wn` tool, which can be invoked without an internet connection!

    ;; (shell-command "brew cask install xquartz &") ;; Dependency
    ;; (shell-command "brew install wordnet &")

Let's use Wordnet as a dictionary via the [wordnut](https://github.com/gromnitsky/wordnut) package.

    (use-package wordnut
     :bind ("M-!" . wordnut-lookup-current-word))
    
    ;; Use M-& for async shell commands. 

Use `M-↑,↓` to navigate dictionary results, and `wordnut-search` for a new search.

Use this game to help you learn to spell words that you're having trouble with;
see `~/Dropbox/spelling.txt`.

    (autoload 'typing-of-emacs "~/.emacs.d/typing.el" "The Typing Of Emacs, a game." t)

Practice touch typing using [speed-type](https://github.com/hagleitn/speed-type).

    (use-package speed-type)

Running `M-x speed-type-region` on a region of text, or `M-x speed-type-buffer` on a 
whole buffer, or just `M-x speed-type-text` will produce the selected region, buffer,
or random text for practice. The timer begins when the first key is pressed
and stats are shown when the last letter is entered.

Other typing resources include:

-   [Typing of Emacs](https://www.emacswiki.org/emacs/TypingOfEmacs) &#x2013;an Emacs alternative to speed type, possibly more engaging.
-   [Klavaro](https://alternativeto.net/software/klavaro/) &#x2013;a GUI based yet language-independent typing tutor.
    -   I'm enjoying this tool in getting started with Arabic typing.
    -   The plan is to move to using the online [Making Hijrah](https://makinghijrah.com/arabic-typing/) tutor which
        concludes the basic lesson plan with a few short narrations.
-   [Typing.io](https://typing.io/) is a tutor for coders: Lessons are based on open source code, such
    some XMonad written in Haskell or Linux written in  C.
-   [GNU Typist](https://www.gnu.org/software/gtypist/index.html#downloading) &#x2013;which is interactive in the terminal, so not ideal in Emacs&#x2013;,


<a id="org81f2284"></a>

## Using a Grammar & Style Checker

Let's install [a grammar and style checker](https://github.com/mhayashi1120/Emacs-langtool).
We get the offline tool from the bottom of the [LanguageTool](https://languagetool.org/) website, then relocate it
as follows.

    (use-package langtool
     :config
      (setq langtool-language-tool-jar
         "~/Applications/LanguageTool-4.5/languagetool-commandline.jar") 
    )

Now we can run `langtool-check` on the subsequent grammatically incorrect
text &#x2013;which is from the LanguageTool website&#x2013; which colours errors in red,
when we click on them we get the reason why; then we may invoke
`langtool-correct-buffer` to quickly use the suggestions to fix each correction,
and finally invoke `langtool-check-done` to stop any remaining red colouring.

    LanguageTool offers spell and grammar checking. Just paste your text here
    and click the 'Check Text' button. Click the colored phrases for details
    on potential errors. or use this text too see an few of of the problems
    that LanguageTool can detecd. What do you thinks of grammar checkers?
    Please not that they are not perfect. Style issues get a blue marker:
    It's 5 P.M. in the afternoon. The weather was nice on Thursday, 27 June 2017
    --uh oh, that's the wrong date ;-)

By looking around the source code, I can do all three stages smoothly (•̀ᴗ•́)و

    ;; Quickly check, correct, then clean up /region/ with M-^
    
    (add-hook 'langtool-error-exists-hook 
      (lambda ()
        (langtool-correct-buffer)
        (langtool-check-done)
      ))
      
    (global-set-key "\M-^" 'langtool-check)


<a id="orgf7319d6"></a>

## Unicode Input via Agda Input

[Agda](https://mazzo.li/posts/AgdaSort.html) is one of my favourite languages, it's like Haskell on steroids.
Let's set it up.

Executing `agda-mode setup` appends the following text to the `.emacs` file.
Let's put it here ourselves.

    (load-file (let ((coding-system-for-read 'utf-8))
                    (shell-command-to-string "/usr/local/bin/agda-mode locate")))

I almost always want the `agda-mode` input method.

    (require 'agda-input)
    (add-hook 'text-mode-hook (lambda () (set-input-method "Agda")))
    (add-hook 'org-mode-hook (lambda () (set-input-method "Agda")))

Below are my personal Agda input symbol translations;
e.g., `\set → 𝒮ℯ𝓉`. Note that we could give a symbol new Agda TeX binding
interactively: `M-x customize-variable agda-input-user-translations` then
`INS` then for key sequence type `set` then `INS` and for string paste `𝒮ℯ𝓉`.

    ;; category theory
    (add-to-list 'agda-input-user-translations '("set" "𝒮ℯ𝓉"))
    (add-to-list 'agda-input-user-translations '("alg" "𝒜𝓁ℊ"))
    (add-to-list 'agda-input-user-translations '("split" "▵"))
    (add-to-list 'agda-input-user-translations '("join" "▿"))
    (add-to-list 'agda-input-user-translations '("adj" "⊣"))
    (add-to-list 'agda-input-user-translations '(";;" "﹔"))
    (add-to-list 'agda-input-user-translations '(";;" "⨾"))
    (add-to-list 'agda-input-user-translations '(";;" "∘"))
    
    ;; lattices
    (add-to-list 'agda-input-user-translations '("meet" "⊓"))
    (add-to-list 'agda-input-user-translations '("join" "⊔"))
    
    ;; residuals
    (add-to-list 'agda-input-user-translations '("syq"  "╳"))
    (add-to-list 'agda-input-user-translations '("over" "╱"))
    (add-to-list 'agda-input-user-translations '("under" "╲"))
            ;; Maybe “\\” shortcut?
    
    ;; Z-quantification range notation, e.g., “∀ x ❙ R • P”
    (add-to-list 'agda-input-user-translations '("|" "❙"))
    (add-to-list 'agda-input-user-translations '("with" "❙"))
    
    ;; adjunction isomorphism pair
    (add-to-list 'agda-input-user-translations '("floor"  "⌊⌋"))
    (add-to-list 'agda-input-user-translations '("lower"  "⌊⌋"))
    (add-to-list 'agda-input-user-translations '("lad"    "⌊⌋"))
    (add-to-list 'agda-input-user-translations '("ceil"   "⌈⌉"))
    (add-to-list 'agda-input-user-translations '("raise"  "⌈⌉"))
    (add-to-list 'agda-input-user-translations '("rad"    "⌈⌉"))
    
    ;; silly stuff
    ;;
    ;; angry, cry, why-you-no
    (add-to-list 'agda-input-user-translations 
       '("whyme" "ლ(ಠ益ಠ)ლ" "ヽ༼ಢ_ಢ༽ﾉ☂" "щ(゜ロ゜щ)")) 
    ;; confused, disapprove, dead, shrug
    (add-to-list 'agda-input-user-translations 
       '("what" "「(°ヘ°)" "(ಠ_ಠ)" "(✖╭╮✖)" "¯\\_(ツ)_/¯"))
    ;; dance, csi
    (add-to-list 'agda-input-user-translations 
       '("cool" "┏(-_-)┓┏(-_-)┛┗(-_-﻿ )┓" "•_•)
    ( •_•)>⌐■-■
    (⌐■_■)
    "))
    ;; love, pleased, success, yesss
    (add-to-list 'agda-input-user-translations 
       '("smile" "♥‿♥" "(─‿‿─)" "(•̀ᴗ•́)و" "(งಠ_ಠ)ง"))

Finally let's effect such translations.

    ;; activate translations
    (agda-input-setup)

Note that the effect of [Emacs unicode input](http://ergoemacs.org/emacs/emacs_n_unicode.html) could be approximated using
`abbrev-mode`.


<a id="orgf1620f9"></a>

## Locally `toggle` a variable

**todo** body of toggle should be a progn?

It is dangerous to load a file with local variables;
instead we should load files without evaluating locals,
read the locals to ensure they are safe &#x2013;e.g., there's nothing
malicious like `eval: (delete-file your-important-file.txt)`&#x2013;
then revert the buffer to load the locals.

However, when preprocessing my own files I sometimes wish
to accept all locals without being queried and so have the following
combinator.

    (defmacro toggle (variable value code)
      "Locally set the value of ‘variable’ to be ‘value’ in the scope of ‘code’.
       In particular, the value of ‘variable’, if any, *is* affected
       to produce useful sideffects. It retains its orginal value outside this call.
    
       Example uses include terse replacements for one-off let-statements,
       or, more likely, of temporarily toggeling important values, such as 
       ‘kill-buffer-query-functions’ for killing a process buffer without confirmation.
    
       Another example: ‘(toggle enable-local-variables :all ⋯)’ to preprocess files
       without being queried about possibly dangerous local variables.
      "
      `(let ((_initial_value_ ,variable))
            (setq ,variable ,value)
            ,code
            (setq ,variable _initial_value_)
      )
    )

Since emacs-lisp interprets definitions sequentially, I define `toggle` here
since I employ it in the next section.


<a id="org2928585"></a>

## Syncing to the System's `$PATH`

For one reason or another, on OS X it seems that an Emacs instance
begun from the terminal may not inherit the terminal's environment
variables, thus making it difficult to use utilities like `pdflatex`
when Org-mode attempts to produce a PDF.

    (use-package exec-path-from-shell
      :init
        (when (memq window-system '(mac ns x))
         (exec-path-from-shell-initialize))
    )

See these [docs](https://github.com/purcell/exec-path-from-shell) for setting other environment variables.


<a id="org3dcc0b2"></a>

## Keeping My System Up to Date

    (defun my/stay-up-to-date ()
    
      "Ensure that OS and Emacs pacakges are up to date.
    
       Takes ~5 secons when everything is up to date.
      "
    
      (async-shell-command "brew update && brew upgrade")
      (other-window 1)
      (rename-buffer "Keeping-system-up-to-date")
        
      (package-refresh-contents)
      (insert "Emacs packages have been updated.")
    
      (other-window 1)
    )
    
    (add-hook 'after-init-hook 'my/stay-up-to-date)


<a id="org88f583c"></a>

## Who am I? ─Using Gnus for Gmail

Let's set the following personal
Emacs-wide variables ─to be used in other locations besides email.

    (setq user-full-name    "Musa Al-hassy"
          user-mail-address "alhassy@gmail.com")

By default, in Emacs, we may send mail: Write it in Emacs with `C-x m`,
then press `C-c C-c` to have it sent via your OS's default mailing system
&#x2013;mine appears to be Gmail via the browser. Or cancel sending mail with
`C-c C-k` &#x2013;the same commands for capturing, discussed below (•̀ᴗ•́)و

To send and read email in Emacs we use
[GNUS](https://en.wikipedia.org/wiki/Gnus) &#x2013;which, like many GNU itself, it a recursive acronym:
GNUS Network User Service.

1.  Execute, rather place in your init:
    
        (setq message-send-mail-function 'smtpmail-send-it)
    
    Revert to the default OS mailing method by setting this variable to
    `mailclient-send-it`.

2.  Follow only the [quickstart here](https://www.emacswiki.org/emacs/GnusGmail#toc1); namely, make a file named `~/.gnus` containing:
    
             ;; user-full-name and user-mail-address should be defined
             
        (setq gnus-select-method
              '(nnimap "gmail"
        	       (nnimap-address "imap.gmail.com")
        	       (nnimap-server-port "imaps")
        	       (nnimap-stream ssl)))
        
        (setq smtpmail-smtp-server "smtp.gmail.com"
              smtpmail-smtp-service 587
              gnus-ignored-newsgroups "^to\\.\\|^[0-9. ]+\\( \\|$\\)\\|^[\"]\"[#'()]")

3.  Enable “2 step authentication” for Gmail following [these](https://emacs.stackexchange.com/a/33309/10352) instructions.

4.  You will then obtain a secret password, the `x` marks below, which you insert in a file
    named `~/.authinfo` as follows &#x2013;using your email address.
    
        machine imap.gmail.com login alhassy@gmail.com password xxxxxxxxxxxxxxxx port imaps
        machine smtp.gmail.com login alhassy@gmail.com password xxxxxxxxxxxxxxxx port 587

5.  In Emacs, `M-x gnus` to see what's there.
    
    Or compose mail with `C-x m` then send it with `C-c C-c`.
    
    -   Press `C-h m` to learn more about message mode for mail composition;
        or read [the Message Manual](https://www.gnus.org/manual/message.pdf).

In gnus, by default items you've looked at disappear &#x2013;i.e., are archived.
They can still be viewed in, say, the online browser if you like.
In the `Group` view, `R` resets gnus, possibly retrieving mail or alterations
from other mail clients. `q` exits gnus in `Group` mode, `q` exits the particular
view to go back to summary mode. Only after pressing `q` from within a group
do changes take effect on articles &#x2013;such as moves, reads, deletes, etc.

-   **RET:** Open an article.

-   **B m:** Move an article, in its current state, to another group
    &#x2013;i.e., ‘label’ using Gmail parlance.
    
    Something to consider doing when finished with an article.
    
    To delete an article, simply move it to ‘trash’ &#x2013;of course this will delete it
    in other mail clients as well. There is no return from trash.
    
    Emails can always be achieved &#x2013;never delete, maybe?

-   **!:** mark an article as read, but to be kept around
    &#x2013;e.g., you have not replied to it, or it requires more reading at a later time.

-   **R:** Reply to email with sender's content there in place.
    -   `r` to reply to an email with sender's content in adjacent buffer.

-   **d:** mark an article as done, i.e., read it and it can be archived.

Learn more by reading [The Gnus Manual](https://www.gnus.org/manual.html); also available within Emacs by `C-h i m gnus` (•̀ᴗ•́)و

-   Or look at the [Gnus Reference Card](https://www.gnu.org/software/emacs/refcards/pdf/gnus-refcard.pdf).
-   Or, less comprehensively, this [outline](https://github.com/redguardtoo/mastering-emacs-in-one-year-guide/blob/master/gnus-guide-en.org#subscribe-groups).


<a id="org73c18fd"></a>

## Using Emacs in any text area on my OS

Using the [Emacs-Anywhere](https://github.com/zachcurry/emacs-anywhere/#usage) tool, I can press `Cmd Shift e` to have an Emacs frame
appear, produce text with Emacs editing capabilities, then `C-x 5 0` to have the
resulting text dumped into the text area I was working in.

This way I can use Emacs literally anywhere for textual input!

For my Mac OSX:

    (shell-command "curl -fsSL https://raw.github.com/zachcurry/emacs-anywhere/master/install | bash")
    
    (server-start)

The tools that use emacs-anywhere &#x2013;such as my web browser&#x2013; and emacs-anywhere
itself need to be given sufficient OS permissions:

    System Preferences → Security & Privacy → Accessibility

Then check the emacs-anywhere box from the following gui and provide a keyboard shortcut:

    System Preferences → Keyboard → Shortcuts → Services

(•̀ᴗ•́)و

I always want to be in Org-mode and input unicode:

    (add-hook 'ea-popup-hook
      (lambda (app-name window-title x y w h)
       (org-mode)
       (set-input-method "Agda")
      )  
    )  


<a id="org8f5124f"></a>

# Cosmetics

    ;; Make it very easy to see the line with the cursor.
    (global-hl-line-mode t)
    
    ;; Keep self motivated!
    (setq frame-title-format '("" "%b - Living The Dream (•̀ᴗ•́)و"))


<a id="org190da80"></a>

## Startup message: Emacs & Org versions

    ;; Silence the usual message: Get more info using the about page via C-h C-a.
    (setq inhibit-startup-message t)
    
    (defun display-startup-echo-area-message ()
      (message
          (concat "Welcome "      user-full-name
                  "! Emacs "      emacs-version
                  "; Org-mode "   org-version
                  "; System "    (system-name)
          )
      )     
    )

Now my startup message is,

    ;; Welcome Musa Al-hassy! Emacs 26.1; Org-mode 9.2.3; System alhassy-air.local

For some fun, run this cute method.

    (animate-birthday-present user-full-name)

Moreover, since I end up using org-mode most of the time, let's make that the default mode.

    (setq initial-major-mode 'org-mode)


<a id="org32fcef1"></a>

## Persistent Scratch Buffer

The `*scratch*` buffer is a nice playground for temporary data.

I use Org-mode often, so that's how I want things to appear.

    (setq initial-scratch-message (concat
      "#+Title: Persistent Scratch Buffer"
      "\n#\n # Welcome! This’ a place for trying things out. \n"))

We might accidentally close this buffer, so we could utilise the following.

    ;; A very simple function to recreate the scratch buffer:
    ;; ( http://emacswiki.org/emacs/RecreateScratchBuffer )
    (defun my/create-scratch-buffer nil
       "create a scratch buffer"
       (interactive)
       (switch-to-buffer (get-buffer-create "*scratch*"))
       (insert initial-scratch-message)
       (org-mode))   

However, by default its contents are not saved &#x2013;which may be an issue if we have
not relocated our playthings to their appropriate files. Whence let's save & restore
the scratch buffer by default.

    (use-package persistent-scratch
      :config  
      (persistent-scratch-setup-default))


<a id="org2df07f7"></a>

## Spaceline: A sleek mode line

I may not use the spacemacs [starter kit](https://www.emacswiki.org/emacs/StarterKits), since I do not like evil-mode and find spacemacs 
to “hide things” from me &#x2013;whereas Emacs “”encourages” me to learn more&#x2013;,
however it is a configuration and I enjoy reading Emacs configs in order to 
improve my own setup. From Spacemacs I've adopted Helm for list completion,
its sleek light & dark themes, and its modified powerline setup.

The ‘modeline’ is a part near the bottom of Emacs that gives information
about the current mode, as well as other matters &#x2013;such as time & date, for example.

    (use-package spaceline
      :config
      (require 'spaceline-config)
      (setq spaceline-buffer-encoding-abbrev-p nil)
      (setq spaceline-line-column-p nil)
      (setq spaceline-line-p nil)
      (setq powerline-default-separator 'arrow)
      :init
     (spaceline-helm-mode) ;; When using helm, mode line looks prettier.
     (spaceline-spacemacs-theme)
    )

Other separators I've considered include `'brace` instead of an arrow,
and `'contour, 'chamfer, 'wave, 'zigzag` which look like browser tabs
that are curved, boxed, wavy, or in the style of driftwood.


<a id="org537cb25"></a>

## Flashing when something goes wrong

Make top and bottom of screen flash when something unexpected happens thereby observing a warning message in the minibuffer. E.g., C-g, or calling an unbound key sequence, or misspelling a word.

    (setq visible-bell 1)
    ;; Enable flashing mode-line on errors
    ;; On MacOS, this shows a caution symbol ^_^


<a id="orge44afbd"></a>

## My to-do list: The initial buffer when Emacs opens up

    (find-file "~/Dropbox/todo.org")
    ;; (setq initial-buffer-choice "~/Dropbox/todo.org")
    
    (split-window-right)			  ;; C-x 3
    (other-window 1)			          ;; C-x 0
    (toggle enable-local-variables :all           ;; Load *all* locals.
        (toggle org-confirm-babel-evaluate nil    ;; Eval *all* blocks.
          (find-file "~/.emacs.d/init.org")))


<a id="org7fa3ad9"></a>

## Showing date, time, and battery life

    (setq display-time-day-and-date t)
    (display-time)
    
    ;; (display-battery-mode 1)
    ;; Nope; let's use a fancy indicator … 
    
    (use-package fancy-battery
      :diminish
      :config
        (setq fancy-battery-show-percentage t)
        (setq battery-update-interval 15)
        (fancy-battery-mode)
        (display-battery-mode)
    )

This will show remaining battery life, coloured green if charging
and coloured yellow otherwise. It is important to note that
this package is no longer maintained. It works on my machine.


<a id="orgd5376ab"></a>

## Hiding Scrollbar, tool bar, and menu

    (tool-bar-mode -1)
    (scroll-bar-mode -1)
    (menu-bar-mode -1)


<a id="org0635cca"></a>

## Increase/decrease text size

    (global-set-key (kbd "C-+") 'text-scale-increase)
    (global-set-key (kbd "C--") 'text-scale-decrease)
      ;; C-x C-0 restores the default font size
    
    (add-hook 'text-mode-hook
    	    '(lambda ()
    	       (visual-line-mode 1)))


<a id="org8133a01"></a>

## Delete Selection mode

Delete Selection mode lets you treat an Emacs region much like a typical text
selection outside of Emacs: You can replace the active region.
We can delete selected text just by hitting the backspace key.

    (delete-selection-mode 1)


<a id="orgfa405b2"></a>

## Highlight & complete parenthesis pair when cursor is near ;-

    ;; Highlight expression within matching parens when near one of them.
    (setq show-paren-delay 0)
    (setq blink-matching-paren nil)
    (setq show-paren-style 'expression)
    (show-paren-mode)
    
    ;; Colour parens, and other delimiters, depending on their depth.
    ;; Very useful for parens heavy languages like Lisp.
    (use-package rainbow-delimiters)
    
    (add-hook 'org-mode-hook
      '(lambda () (rainbow-delimiters-mode 1)))
    (add-hook 'prog-mode-hook
      '(lambda () (rainbow-delimiters-mode 1)))

For example,

    (blue (purple (forest (green (yellow (blue))))))

There is a powerful package called ‘smartparens’ for working with pair-able
characters, but I've found it to be too much for my uses. Instead I'll utilise
the lightweight package `electric`, which provided by Emacs out of the box.

    (electric-pair-mode 1)

It supports, by default, ACSI pairs `{}, [], ()` and Unicode `‘’, “”, ⟪⟫, ⟨⟩`.


<a id="org077e109"></a>

## Minibuffer should display line and column numbers

    (global-display-line-numbers-mode t)
    ; (line-number-mode t)
    (column-number-mode t)


<a id="org52da597"></a>

## Neotree: Directory Tree Listing

We open a nifty file manager upon startup.

    ;; neotree --sidebar for project file navigation
    (use-package neotree
      :config (global-set-key "\C-x\ d" 'neotree-toggle))
    
    ;; Only do this once: 
    (when nil
      (use-package all-the-icons)
      (all-the-icons-install-fonts 'install-without-asking))
    
    (setq neo-theme 'icons)
    (neotree-refresh)
    
    ;; Open it up upon startup.
    (neotree-toggle)

By default `C-x d` invokes `dired`, but I prefer `neotree` for file management.

Useful navigational commands include

-   `U` to go up a directory.
-   `C-c C-c` to change directory focus; `C-C c` to type the directory out.
-   `?` or `h` to get help and `q` to quit.

As always, to go to the neotree pane when it's the only other window,
execute `C-x o`.

I *rarely* make use of this feature; company mode & Helm together quickly provide
an automatic replacement for nearly all of my uses.


<a id="org1cbffaf"></a>

## Window resizing using the golden ratio     :Disabled:

Let's load the following package, which automatically resizes windows so that
the window containing the cursor is the largest, according to the golden ratio.
Consequently, the window we're working with is nice and large yet the other windows
are still readable.

    (use-package golden-ratio
      :diminish golden-ratio-mode
      :init (golden-ratio-mode 1))

After some time this got a bit annoying and I'm no longer  using this.


<a id="orgdc2185a"></a>

# Life within Org-mode

Let's obtain Org-mode along with the extras that allow us to ignore
heading names, but still utilise their contents &#x2013;e.g., such as a heading
named ‘preamble’ that contains org-mode setup for a file.

    (use-package org
      :ensure org-plus-contrib
      :config
      (require 'ox-extra)
      (ox-extras-activate '(ignore-headlines)))

This lets us use the `:ignore:` tag on headlines you'd like to have ignored, 
while not ignoring their content &#x2013;see [here](https://emacs.stackexchange.com/a/17677/10352).

-   Use the `:noexport:` tag to omit a headline *and* its contents.

Now, let's replace the content marker, “⋯”, with a nice
unicode arrow.

    (setq org-ellipsis " ⤵")

Also, fold all source blocks on startup.

    (setq org-hide-block-startup t)

I rarely use tables, but here is a useful [Org-Mode Table Editing Cheatsheet.](http://notesyoujustmightwanttosave.blogspot.com/)


<a id="orgfb596cd"></a>

## High Speed Literate Programming


### Manipulating Sections

Let's enable the [Org Speed Keys](http://notesyoujustmightwanttosave.blogspot.com/2011/12/org-speed-keys.html) so that when the cursor is at the beginning of 
a headline, we can perform fast manipulation & navigation using the standard Emacs movement
controls, such as 

-   `#` toggle `COMMENT`-ing for an org-header.
-   `s` toggles “narrowing” to a subtree; i.e., hide the rest of the document.
    
    If you narrow to a subtree then any export, `C-c C-e`, will only consider
    the narrowed detail.

-   `I/O` clock In/Out to the task defined by the current heading. 
    -   Keep track of your work times!
    -   `v` view agenda.
-   `u` for jumping upwards to the parent heading.
-   `c` for cycling structure below current heading, or `C` for cycling global structure.
-   `i` insert a new same-level heading below current heading.
-   `w` refile current heading; options list pops-up to select which heading to move it to. Neato!
-   `t` cycle through the available TODO states.
-   `^` sort children of current subtree; brings up a list of sorting options.
-   `n/p` for next/previous *visible* heading.
-   `f/b` for jumping forward/backward to the next/previous *same-level* heading.
-   `D/U` move a heading down/up.
-   `L/R` recursively promote (move leftwards) or demote (more rightwards) a heading.
-   `1,2,3` to mark a heading with priority, highest to lowest.

We can add our own speed keys by altering the `org-speed-commands-user` variable.

Moreover, `?` to see a complete list of keys available.

    (setq org-use-speed-commands t)


### Seamless Navigation Between Source Blocks

Finally, let's use the “super key” &#x2013;aka the command or windows key&#x2013;
to jump to the previous, next, or toggle editing org-mode source blocks.

    ;; Overriding keys for printing buffer, duplicating gui frame, and isearch-yank-kill.
    ;;
    (define-key org-mode-map (kbd "s-p") #'org-babel-previous-src-block)
    (define-key org-mode-map (kbd "s-n") #'org-babel-next-src-block)
    (define-key org-mode-map (kbd "s-e") #'org-edit-src-code)
    (define-key org-src-mode-map (kbd "s-e") #'org-edit-src-exit)

Interestingly, `s-l` is “goto line”.


### Modifying `<return>`

-   `C-RET, C-S-RET` make a new heading where the latter marks it as a `TODO`.
-   By default `M-RET` makes it easy to work with existing list items, headings, tables, etc
    by creating a new item, heading, etc.
-   Usually we want a newline then we indent, let's make that the default.
    
        (add-hook 'org-mode-hook '(lambda () 
          (local-set-key (kbd "<return>") 'org-return-indent))
          (local-set-key (kbd "C-M-<return>") 'electric-indent-just-newline))
    
    Notice that I've also added another kind of return, for when I want to
    break-out of the indentation approach and start working at the beginning of
    the line.

In summary,

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<thead>
<tr>
<th scope="col" class="org-left">key</th>
<th scope="col" class="org-left">method</th>
<th scope="col" class="org-left">behaviour</th>
</tr>
</thead>

<tbody>
<tr>
<td class="org-left">`<return>`</td>
<td class="org-left">`org-return-indent`</td>
<td class="org-left">Newline with indentation</td>
</tr>


<tr>
<td class="org-left">`M-<return>`</td>
<td class="org-left">`org-meta-return`</td>
<td class="org-left">Newline with new org item</td>
</tr>


<tr>
<td class="org-left">`C-M-<return>`</td>
<td class="org-left">`electric-indent-just-newline`</td>
<td class="org-left">Newline, cursor at start</td>
</tr>


<tr>
<td class="org-left">`C-<return>`</td>
<td class="org-left">`org-insert-heading-respect-content`</td>
<td class="org-left">New heading *after* current content</td>
</tr>


<tr>
<td class="org-left">`C-S-<return>`</td>
<td class="org-left">`org-insert-todo-heading-respect-content`</td>
<td class="org-left">Ditto, but with a `TODO` marker</td>
</tr>
</tbody>
</table>


### `C-a,e,k` and Yanking of sections

    ;; On an org-heading, C-a goes to after the star, heading markers.
    ;; To use speed keys, run C-a C-a to get to the star markers.
    ;;
    ;; C-e goes to the end of the heading, not including the tags.
    ;;
    (setq org-special-ctrl-a/e t)
    
    ;; C-k no longer removes tags, if activated in the middle of a heading's name.
    (setq org-special-ctrl-k t)
    
    ;; When you yank a subtree and paste it alongside a subtree of depth ‘d’,
    ;; then the yanked tree's depth is adjusted to become depth ‘d’ as well.
    ;; If you don't want this, then refile instead of copy pasting.
    (setq org-yank-adjusted-subtrees t)


<a id="orgc0bb58a"></a>

## Using org-mode as a Day Planner

⟪ This section is based on a dated, yet delightful, tutorial
  of the same title by [John Wiegley](http://newartisans.com/2007/08/using-org-mode-as-a-day-planner/). ⟫

We want a day-planner with the following use:

1.  “Mindlessly” & rapidly create new tasks.
2.  Schedule and archive tasks at the end, or start, of the work day.
3.  Glance at a week's tasks, shuffle if need be.
4.  Prioritise the day's tasks. Aim for ≤15 tasks.
5.  Progress towards `A` tasks completion by documenting work completed.
6.  Repeat! During the day, if anything comes up, capture it and intentionally
    forget about it.

[Capture](https://orgmode.org/org.html#Setting-up-capture) lets me quickly make notes & capture ideas, with associated reference material,
without any interruption to the current work flow. Without losing focus on what you're doing,
quickly jot down a note of something important that just came up.

E.g., I have a task, or something I wish to note down, rather than opening
some file, then making a heading, then writing it; instead, I press
`C-c c t` and a pop-up appears, I make my note, and it disappears with my
notes file(s) now being altered! Moreover, by default it provide a timestamp
and a link to the file location where I made the note &#x2013;helpful for tasks, tickets,
to be tackled later on.

    (setq org-default-notes-file "~/Dropbox/todo.org")
    (define-key global-map "\C-cc" 'org-capture)

By default we only get a ‘tasks’ form of capture, let's add some more.

    (cl-defun my/make/org-capture-template 
       (shortcut heading &optional (no-todo nil) (description heading) (category heading))
      "Quickly produce an org-capture-template.
    
      After adding the result of this function to ‘org-capture-templates’,
      we will be able perform a capture with “C-c c ‘shortcut’”
      which will have description ‘description’.
      It will be added to the tasks file under heading ‘heading’
      and be marked with category  ‘category’.
    
      ‘no-todo’ omits the ‘TODO’ tag from the resulting item; e.g.,
      when it's merely an interesting note that needn't be acted upon.
      ─Probably a bad idea─
    
      Defaults for ‘description’ and ‘category’ are set to the same as
      the ‘heading’. Default for ‘no-todo’ is ‘nil’.
      "
      `(,shortcut ,description entry
          (file+headline org-default-notes-file 
             ,(concat heading "\n#+CATEGORY: " category))
          , (concat "*" (unless no-todo " TODO") " %?\n:PROPERTIES:\n:CREATED: %U\n:END:\n\n")
          :empty-lines 1)
    )
    
    (setq org-capture-templates
      `(
         ,(my/make/org-capture-template "t" "Tasks, Getting Things Done")
         ,(my/make/org-capture-template "r" "Research")
         ,(my/make/org-capture-template "m" "Email")
         ,(my/make/org-capture-template "e" "Emacs (•̀ᴗ•́)و")
         ,(my/make/org-capture-template "b" "Blog")
         ,(my/make/org-capture-template "a" "Arbitrary Reading and Learning")
         ,(my/make/org-capture-template "p" "Personal Matters")
    ))

For now I capture everything into a single file.
One would ideally keep separate client, project, information in its own org file.
The `#+CATEGORY` appears alongside each task in the agenda view &#x2013;keep reading.

**Where am I currently capturing?**

-   During meetings, when a nifty idea pops into my mind, I quickly capture it.
    -   I've found taking my laptop to meetings makes me an active listener
        and I get much more out of my meetings since I'm taking notes.
-   Through out the day, as I browse the web, read, and work; random ideas pop-up, and I capture them indiscriminately.
-   I envision that for a phone call, I would open up a capture to make note of what the call entailed so I can review it later.
-   Anywhere you simply want to make a note, for the current heading, just press
    `C-c C-z`. The notes are just your remarks along with a timestamp; they are
    collected at the top of the tree, under the heading.
    
        ;; Ensure notes are stored at the top of a tree.
        (setq org-reverse-note-order nil)

Anyhow…

Step 1: When new tasks come up
Isn't it great that we can squirrel away info into some default location
then immediately return to what we were doing before &#x2013;with speed & minimal distraction! ♥‿♥
Indeed, if our system for task management were slow then we may not produce tasks and so forget them altogether! щ(゜ロ゜щ)

-   Entering tasks is a desirably impulsive act; 
    do not make any further scheduling considerations.
    
    The next step, the review stage occurring at the end or the start of
    the workday, is for processing.

> *The reason for this is that entering new tasks should be impulsive, not reasoned./* 
> *Your reasoning skills are required for the task at hand, not every new tidbit./* 
> *You may even find that during the few hours that transpire between creating a*
> *task and categorizing it, you’ve either already done it or discovered it doesn’t*
> *need to be done at all!* &#x2013; [John Wiegley](http://newartisans.com/2007/08/using-org-mode-as-a-day-planner/)

When my computer isn't handy, make a note on my phone then transfer it later.

**Step 2: Filing your tasks**
At a later time, a time of reflection, we go to our tasks list and actually schedule time to get them done
by `C-c C-s` then pick a date by entering a number in the form `+n` to mean that task is due `n` days from now.

-   Tasks with no due date are ones that “could happen anytime”, most likely no time at all.
-   At least schedule tasks reasonably far off in the future, then reassess when the time comes.
-   An uncompleted task is by default rescheduled to the current day, each day, along with how overdue it is.
    
    -   Aim to consciously reschedule such tasks!
    
    With time, it will become clear what is an unreasonable day
    verses what is an achievable day.

**Step 3: Quickly review the upcoming week**
The next day we begin our work, we press `C-c a a` to see the 
scheduled tasks for this week --`C-c C-s` to re-schedule the 
task under the cursor and `r` to refresh the agenda.

    (define-key global-map "\C-ca" 'org-agenda)

**Step 4: Getting ready for the day**
After having seen our tasks for the week, we press `d` to enter daily view
for the current day. Now we decide whether the items for today are 
`A`: of high urgency & important; `B`: of moderate urgency & importance; or
`C`: Pretty much optional, or very quick or fun to do.

-   `A` tasks should be both important *and* urgently done on the day they were scheduled.
    -   Such tasks should be relatively rare!
    -   If you have too many, you're anxious about priorities and rendering
        priorities useless.
-   `C` tasks can always be scheduled for another day without much worry.
    -   Act! If the thought of rescheduling causes you to worry, upgrade it to a
        `B` or `A`.
-   As such, most tasks will generally be priority `B`: 
    Tasks that need to be done, but the exact day isn't as critical as with an
    `A` task. These are the “bread and butter” tasks that make up your day to day
    life.

On a task item, press `,` then one of `A, B, C` to set its priority.
Then `r` to refresh.

**Step 5: Doing the work**
Since `A` tasks are the important and urgent ones, if you do all of the `A` tasks and
nothing else today, no one would suffer. It's a good day (─‿‿─).

There should be no scheduling nor prioritising at this stage.
You should not be touching your tasks file until your next review session:
Either at the end of the day or the start of the next.

-   Leverage priorities! E.g., When a full day has several `C` tasks, reschedule
    them for later in the week without a second thought.
    -   You've already provided consideration when assigning priorities.

**Step 6: Moving a task toward completion**
My workflow states are described in the section
[4.5](#WorkflowStates) and contain states: `TODO, STARTED, WAITING, ON_HOLD, CANCELLED, DONE`.

-   Tasks marked `WAITING` are ones for which we are awaiting some event, like someone
    to reply to our query. As such, these tasks can be rescheduled until I give up
    or the awaited event happens &#x2013;in which case I go to `STARTED` and document
    the reply to my query.
-   The task may be put off indefinitely with `ON_HOLD`, or I may choose never to do it
    with `CANCELLED`. Along with `DONE`, these three mark a task as completed
    and so it needn't appear in any agenda view.

I personally clock-in and clock-out of tasks &#x2013;keep reading&#x2013;,
where upon clocking-out I'm prompted for a note about what I've accomplished
so far.
Entering a comment about what I've done, even if it's very little,
feels like I'm getting something done. It's an explicit marker of progress.

In the past, I would make a “captain's log” at the end of the day, but that's
like commenting code after it's written, I didn't always feel like doing it and
it wasn't that important after the fact. The continuous approach of noting after
every clock-out is much more practical, for me at least.

**Step 7: Archiving Tasks**
During the review state,
when a task is completed, ‘archive’ it with `C-c C-x C-s`: This marks it as done, adds a time stamp,
and moves it to a local `*.org_archive` file. This was our ‘to do’ list becomes a ‘ta da’ list showcasing
all we have done (•̀ᴗ•́)و

Archiving keeps task lists clutter free, but unlike deletion it allows
us, possibly rarely, to look up details of a task or what tasks were completed
in a certain time frame &#x2013;which may be a motivational act, to see that you have
actually completed more than you thought, provided you make and archive tasks
regularly. We can use `(org-search-view)` to search an org file *and* the
archive file too, if we enable it so.

    ;; Include agenda archive files when searching for things
    (setq org-agenda-text-search-extra-files (quote (agenda-archives)))

    ;; Invoing the agenda command shows the agenda and enables
    ;; the org-agenda variables.
    (org-agenda "a" "a")

Let's install some helpful views for our agenda.

-   `C-c a c`: See completed tasks at the end of the day and archive them.
    
        ;; Pressing ‘c’ in the org-agenda view shows all completed tasks,
        ;; which should be archived.
        (add-to-list 'org-agenda-custom-commands 
          '("c" todo "DONE|ON_HOLD|CANCELLED" nil))
-   `C-c a u`: See unscheduled, undeadlined, and undated tasks in my todo files.
    Which should then be scheduled or archived.
    
        (add-to-list 'org-agenda-custom-commands 
          '("u" alltodo "" 
             ((org-agenda-skip-function
                (lambda ()
        	      (org-agenda-skip-entry-if 'scheduled 'deadline 'regexp  "\n]+>")))
        	      (org-agenda-overriding-header "Unscheduled TODO entries: "))))


<a id="org4b71928"></a>

## Automating [Pomodoro](https://en.wikipedia.org/wiki/Pomodoro_Technique) &#x2013;Dealing with dreadful tasks

Effort estimates are for an entire task.
Yet, sometimes it's hard to even get started on some tasks.

-   The code below ensures a 25 minute timer is started whenever clocking in happens.
    -   The timer is in the lower right of the modeline.

-   When the timer runs out, we get a notification.

-   We may have the momentum to continue on the dreadful task, or clock-out and take a break after
    documenting what was accomplished.

    ;; Tasks get a 25 minute count down timer 
    (setq org-timer-default-timer 25)
    
    ;; Use the timer we set when clocking in happens.
    (add-hook 'org-clock-in-hook
      (lambda () (org-timer-set-timer '(16))))
    
    ;; unless we clocked-out with less than a minute left,
    ;; show disappointment message.
    (add-hook 'org-clock-out-hook
      (lambda ()
      (unless (s-prefix? "0:00" (org-timer-value-string))
         (message-box "The basic 25 minutes on this dreadful task are not up; it's a shame to see you leave."))
         (org-timer-stop)
         ))

Note that this does not conflict with the total effort estimate for the task.


<a id="org76bf3d6"></a>

## Journaling

Thus far I've made it easy to quickly capture ideas and tasks,
not so much on the analysis phase:

-   What was accomplished today?
-   What are some notably bad habits? Good habits?
-   What are some future steps?

Rather than overloading the capture mechanism for such thoughts,
let's employ `org-journal` &#x2013;journal entries are stored in files such as 
`journal/20190407`, where the file name is simply the date, or only one
file per year as I've set it up below.
Each entry is the week day, along with the date,
then each child tree is an actual entry with a personal
title preceded by the time the entry was made.
Unlike capture and its agenda support, journal ensures entries are maintained in
chronological order with calendar support. 

Since org files are plain text files, an entry can
be written anywhere and later ported to the journal.

The separation of concerns is to emphasise the capture stage
as being quick and relatively mindless, whereas the Journaling
stage as being mindful.
Even though we may utilise capture to provide quick support for including
journal entries, I have set my journal to be on a yearly basis &#x2013;one file per year&#x2013;
since I want to be able to look at previous entries when making the current entry;
after all, it's hard to compare and contrast easily unless there's multiple entries
opened already.

As such, ideally at the end of the day, I can review what
has happened, and what has not, and why this is the case,
and what I intend to do about it, and what problems were encountered
and how they were solved &#x2013;in case the problem is encountered again in the future.
**Consequently, if I encounter previously confronted situations, problems,**
**all I have to do is reread my journal to get an idea of how to progress.**
Read more about [the importance of reviewing your day on a daily basis](https://www.google.com/search?q=on+the+importance+of+reviwing+your+day+daily&oq=on+the+importance+of+reviwing+your+day+daily&aqs=chrome..69i57.367j0j7&sourceid=chrome&ie=UTF-8).

Moreover, by journaling with Org on a daily basis, it can be
relatively easy to produce a report on what has been happening
recently, at work for example. For now, there is no need to
have multiple journals, for work and for personal life, as
such I will utilise the tag `:work:` for non-personal matters.

Anyhow, the setup:

    (use-package org-journal
      :bind (("C-c j" . org-journal-new-entry))
      :config
      (setq org-journal-dir "~/Dropbox/journal/")
      (setq org-journal-file-type 'yearly)
    )

Bindings available in `org-journal-mode`, when journaling:

-   `C-c C-j`: Insert a new entry into the current journal file.
    -   Note keys for `org-journal-new-entry` overwrite those for `org-goto`.
-   `C-c C-s`: Search the journal for a string.
    -   Note keys for `org-journal-search` overwrite those for `org-schedule`.

All journal entries are registered in the Emacs Calendar.
To see available journal entries do `M-x calendar`.
Bindings available in the calendar-mode:

-   `j`: View an entry in a new buffer.
-   `i j`: add a new entry into the day’s file
-   `f w/m/y/f/F`: Search in all entries of the current week, month, year, all of time,
    of in all entries in the future.


<a id="WorkflowStates"></a>

## Workflow States

Here are some of my common workflow states, &#x2013;the ‘!’ indicates a timestamp should be generated&#x2013;

    (setq org-todo-keywords
          (quote ((sequence "TODO(t)" "STARTED(s@/!)" "|" "DONE(d/!)")
                  (sequence "WAITING(w@/!)" "ON_HOLD(h@/!)" "|" "CANCELLED(c@/!)")
                 )
          )
    )

The `@` brings up a pop-up to make a local note about why the state changed.
**Super cool stuff!**
In particular, we transition from `TODO` to `STARTED` once 15 minutes, or a
reasonable amount, of work has transpired.
Since all but one state are marked for logging, we could use the 
`lognotestate` logging facility of org-mode, which prompts for a note 
every time a task’s state is changed.

Entering a comment about what I've done, even if it's very little,
feels like I'm getting something done. It's an explicit marker of progress
and motivates me to want to change my task's states more often until I see
it marked `DONE`.

Here's how they are coloured,

    (setq org-todo-keyword-faces
          (quote (("TODO" :foreground "red" :weight bold)
                  ("STARTED" :foreground "blue" :weight bold)
                  ("DONE" :foreground "forest green" :weight bold)
                  ("WAITING" :foreground "orange" :weight bold)
                  ("ON_HOLD" :foreground "magenta" :weight bold)
                  ("CANCELLED" :foreground "forest green" :weight bold))))

Now we press `C-c C-t` then the letter shortcut to actually make the state of an org heading.

    (setq org-use-fast-todo-selection t)

We can also change through states using Shift- left, or right.

Let's draw a state diagram to show what such a workflow looks like.

[PlantUML](http://plantuml.com/index) supports drawing diagrams in a tremendously simple format
&#x2013;it even supports Graphviz/DOT directly and many other formats.
Super simple setup instructions can be found [here](http://eschulte.github.io/babel-dev/DONE-integrate-plantuml-support.html); below are a bit more
involved instructions. Read the manual [here](http://plantuml.com/guide).

    ;; Install the tool
    ; (async-shell-command "brew cask install java") ;; Dependency
    ; (async-shell-command "brew install plantuml")
    
    ;; Tell emacs where it is.
    ;; E.g., (async-shell-command "find / -name plantuml.jar")
    (setq org-plantuml-jar-path
          (expand-file-name "/usr/local/./Cellar/plantuml/1.2019.3/libexec/plantuml.jar"))
    
    ;; Enable C-c C-c to generate diagrams from plantuml src blocks.
    (add-to-list 'org-babel-load-languages '(plantuml . t) )
    (require 'ob-plantuml)
    
    ; Use fundamental mode when editing plantuml blocks with C-c '
    (add-to-list 'org-src-lang-modes (quote ("plantuml" . fundamental)))

Let's use this! 

    skinparam defaultTextAlignment center  /' Text alignment '/
    
    skinparam titleBorderRoundCorner 15
    skinparam titleBorderThickness 2
    skinparam titleBorderColor red
    skinparam titleBackgroundColor Aqua-CadetBlue
    title My Personal Task States
    
    [*] -> Todo  /' This is my starting state '/
    Done -right-> [*]  /' This is an end state '/
    Cancelled -up-> [*]  /' This is an end state '/
    
    /'A task is “Todo”, then it's “started”, then finally it's “done”. '/
    Todo    -right-> Started
    Started -down->  Waiting
    Waiting -up->    Started
    Started -right-> Done
    
    /'Along the way, I may put pause the task for some reason then
      return to it. This may be since I'm “Blocked” since I need 
      something, or the task has been put on “hold” since it may not
      be important right now, and it may be “cancelled” eventually.  
    '/
    
    Todo    -down-> Waiting
    Waiting -up-> Todo
    Waiting -up-> Done
    
    Todo -down-> On_Hold
    On_Hold -> Todo
    
    On_Hold -down-> Cancelled
    Waiting -down-> Cancelled
    Todo    -down-> Cancelled
    
    /' The Org-mode shortcuts for these states are as follows. '/
    Todo      : t
    On_Hold   : h
    Started   : s
    Waiting   : w
    Cancelled : c
    Done      : d
    
    /' If a task is paused, we should document why this is the case. '/
    note right of Waiting: Note what is\nblocking us.
    note right of Cancelled: Note reason\nfor cancellation.
    note bottom of On_Hold: Note reason\nfor reduced priority.
    
    center footer  ♥‿♥ Org-mode is so cool (•̀ᴗ•́)و
    /' Note that we could omit the “center, left, right” if we wished, 
       or used a “header” instead.'/

<img src="../assets/img/workflow.png" alt="My Personal Task States">

Of note:

-   Multiline comments are with `/' comment here '/`, single quote starts a one-line comment.
-   Nodes don't need to be declared, and their names may contain spaces if they are enclosed in double-quotes.
-   One forms an arrow between two nodes by writing a line with `x ->[label here] y`
    or `y <- x`; or using `-->` and `<--` for dashed lines. The label is optional.
    
    To enforce a particular layout, use `-X->` where `X ∈ {up, down, right, left}`.

-   To declare that a node `x` has fields `d, f` we make two new lines having
    `x : f` and `x : d`.
-   One adds a note by a node `x` as follows: `note right of x: words then newline\nthen more words`.
    Likewise for notes on the `left, top, bottom`.
    -   Interesting sprites and many other things can be done with PlantUML. Read the docs.

This particular workflow is inspired by [Bernt Hansen](http://doc.norang.ca/org-mode.html)
&#x2013;while quickly searching through the PlantUML [manual](http://plantuml.com/guide):
The above is known as an “activity diagram” and it's covered in §4.


<a id="org94d4b01"></a>

## Clocking Work Time

Let's keep track of the time we spend working on tasks that we may have captured for ourselves the previous day.
Such statistics provides a good idea of how long it actually takes me to accomplish a certain task in the future
and it lets me know where my time has gone.

-   **Clock in:** on a heading with `I`, or in the subtree with `C-c C-x C-i`.
-   **Clock out:** of a heading with `O`, or in the subtree with `C-c C-x C-o`.
-   **Clock report:** See clocked times with `C-c C-x C-r`.

After clocking out, the start and end times, as well as the elapsed time, are added to a drawer
to the heading. We can punch in and out of tasks as many times as desired, say we took a break or
switched to another task, and they will all be recorded into the drawer.

    ;; Record a note on what was acciomplished when clocking out of an item.
    (setq org-log-note-clock-out t)

To get started, we could estimate how long a task will take and clock-in;
then clock-out and see how long it actually took.

Moreover, we can overlay due dates and priorities to tasks in a non-intrusive way that is
easy to edit by hand.

    ;; List of all the files where todo items can be found. Only one for now.
    (setq org-agenda-files '("~/Dropbox/todo.org"))
    
    ;; How many days ahead the default agenda view should look
    (setq org-agenda-ndays 7)
    
    ;; How many days early a deadline item will begin showing up in your agenda list.
    (setq org-deadline-warning-days 14)
    
    ;; In the agenda view, days that have no associated tasks will still have a line showing the date. 
    (setq org-agenda-show-all-dates t)
    
    (setq org-agenda-skip-deadline-if-done t)
    
    ;; Scheduled items marked as complete will not show up in your agenda view.
    (setq org-agenda-skip-scheduled-if-done t)
    
    ;; The agenda view – even in the 7-days-at-a-time view – will always begin on the current day. 
    ;; This is important, since while using org-mode as a day planner, you never want to think of 
    ;; days gone past. That’s something you do in other ways, such as when reviewing completed tasks.
    (setq org-agenda-start-on-weekday nil)

Sometimes, at the beginning at least, I would accidentally invoke the transposed
command `C-x C-c`, which saves all buffers and quits Emacs. So here's a helpful
way to ensure I don't quit Emacs accidentally.

    (setq confirm-kill-emacs 'yes-or-no-p)

    ;; Resume clocking task when emacs is restarted
    (org-clock-persistence-insinuate)
    
    ;; Show lot of clocking history
    (setq org-clock-history-length 23)
    
    ;; Resume clocking task on clock-in if the clock is open
    (setq org-clock-in-resume t)
    
    ;; Sometimes I change tasks I'm clocking quickly - this removes clocked tasks with 0:00 duration
    (setq org-clock-out-remove-zero-time-clocks t)
    
    ;; Clock out when moving task to a done state
    (setq org-clock-out-when-done t)
    
    ;; Save the running clock and all clock history when exiting Emacs, load it on startup
    (setq org-clock-persist t)
    
    ;; Do not prompt to resume an active clock
    ;; (setq org-clock-persist-query-resume nil)
    
    ;; Include current clocking task in clock reports
    (setq org-clock-report-include-clocking-task t)

**Finding tasks to clock in**
Use one of the following options, with the top-most being the first to be tried.

-   From anywhere, `C-u C-c C-x C-i` yields a pop-up for recently clocked in tasks.
-   Pick something off today's agenda scheduled items.
-   Pick a `Started` task from the agenda view, work on this unfinished task.
-   Pick something from the `TODO` tasks list in the agenda view.

-   `C-c C-x C-d` also provides a quick summary of clocked time for the current org file.

**Estimates versus actual time**
Before clocking into a task, add to the properties drawer `:Effort: 1:25` or `C-c C-x C-e`, for a task
that you estimate will take an hour an twenty-five minutes, for example. Now the modeline
will have will mention the time elapsed alongside the task name.

-   This is also useful when you simply want to put a time limit on a task that wont be
    completed anytime soon, say writing a thesis or a long article, but you still want
    to work on it for an hour a day and be warned when you exceed such a time constraint.
    
    When you've gone above your estimate time, the modeline shows it to be red.


<a id="org0d2c513"></a>

## [Reveal.JS](https://revealjs.com/?transition=zoom#/) &#x2013; The HTML Presentation Framework

Org-mode documents can be transformed into beautiful slide decks
with [org-reveal](https://github.com/yjwen/org-reveal/blob/master/Readme.org) with the following two simple lines.

    (use-package ox-reveal
     :config (setq org-reveal-root "http://cdn.jsdelivr.net/reveal.js/3.0.0/"))

For example, execute --`C-c C-c`&#x2013;  the following block to see an example slide-deck (─‿‿─)

    (shell-command "curl https://raw.githubusercontent.com/yjwen/org-reveal/master/Readme.org >> Trying_out_reveal.org")
    (with-temp-buffer (find-file "Trying_out_reveal.org")
     (org-reveal-export-to-html-and-browse)
    )

Org-mode exporting --`C-c C-e`&#x2013; now includes an option `R` for such reveal slide decks.


<a id="org40792f9"></a>

## Coloured LaTeX using Minted

Execute the following for bib ref as well as minted
Org-mode uses the Minted package for source code highlighting in PDF/LaTeX
&#x2013;which in turn requires the pygmentize system tool.

    (setq org-latex-listings 'minted
          org-latex-packages-alist '(("" "minted"))
          org-latex-pdf-process
          '("pdflatex -shell-escape -interaction nonstopmode -output-directory %o %f"
            "biber %b"
            "pdflatex -shell-escape -interaction nonstopmode -output-directory %o %f"
            "pdflatex -shell-escape -interaction nonstopmode -output-directory %o %f")
    )

For faster pdf generation, may consider invoking:

    (setq org-latex-pdf-process
          '("pdflatex -interaction nonstopmode -output-directory %o %f"))


<a id="org39aa9ed"></a>

## Executing code from `src` blocks

For example, to execute a shell command in emacs,
write a `src` with a shell command, then `C-c c-c` to see the results.
Emacs will generally query you to ensure you're sure about executing the
(possibly dangerous) code block; let's stop that:

    ; Seamless use of babel: No confirmation upon execution.
    ;; Downside: Could accidentally evaluate harmful code.
    (setq org-confirm-babel-evaluate nil)

A worked out example can be obtained as follows: `<g TAB` then `C-c C-C` to make a nice
simple graph &#x2013;the code for this is in the next section.

Some initial languages we want org-babel to support:

     (org-babel-do-load-languages
       'org-babel-load-languages
       '(
         (emacs-lisp . t)
         ;; (shell	 . t)
         (python . t)
         (haskell . t)
         (ruby	 . t)
         (ocaml	 . t)
         (dot	 . t)
         (latex	 . t)
         (org	 . t)
         (makefile	 . t)
         ))
    
    ;; Preserve my indentation for source code during export.
    (setq org-src-preserve-indentation t)
    
    ;; The export process hangs Emacs, let's avoid this.
    ;; MA: For one reason or another, this crashes more than I'd like.
    ;; (setq org-export-in-background t)

More languages can be added using `add-to-list`.


<a id="org2032c71"></a>

## Hiding Emphasise Markers & Inlining Images

    ;; org-mode math is now highlighted ;-)
    (setq org-highlight-latex-and-related '(latex))
    
    ;; Hide the *,=,/ markers
    (setq org-hide-emphasis-markers t)
    
    ;; (setq org-pretty-entities t) 
    ;; to have \alpha, \to and others display as utf8 http://orgmode.org/manual/Special-symbols.html

The following is now disabled &#x2013;it makes my system slower than I'd like.

    ;; Let's set inline images.
    (setq org-display-inline-images t)
    (setq org-redisplay-inline-images t)
    (setq org-startup-with-inline-images "inlineimages")
    
    ;; Automatically convert LaTeX fragments to inline images.
    (setq org-startup-with-latex-preview t)


<a id="org3f0fd34"></a>

## Jumping without hassle

    (defun my/org-goto-line (line)
      "Go to the indicated line, unfolding the parent Org header.
    
       Implementation: Go to the line, then look at the 1st previous
       org header, now we can unfold it whence we do so, then we go
       back to the line we want to be at.
      "
      (interactive)
      (goto-line line)
      (org-previous-visible-heading 1)
      (org-cycle)
      (goto-line line)
    )


<a id="orgfc73d2f"></a>

## Folding within a subtree

    (defun my/org-fold-current-subtree-anywhere-in-it ()
      "Hide the current heading, while being anywhere inside it."
      (interactive)
      (save-excursion
        (org-narrow-to-subtree)
        (org-shifttab)
        (widen))
    )
    
    (add-hook 'org-mode-hook '(lambda () 
      (local-set-key (kbd "C-c C-h") 'my/org-fold-current-subtree-anywhere-in-it)))


<a id="org7136174"></a>

## Making then opening html's from org's

    (cl-defun my/org-html-export-to-html (&optional (filename (buffer-name)))
      "Produce an HTML from the given ‘filename’, or otherwise current buffer,
       then open it in my default brower.
      "
     (interactive)
     (org-html-export-to-html)
     (let ((it (concat (file-name-sans-extension buffer-file-name) ".html")))
       (browse-url it)
       (message (concat it " has been opened in Chromium."))
       'success ;; otherwise we obtain a "compiler error".
     ) 
    )


<a id="org9f6128d"></a>

## Making then opening pdf's from org's

    (cl-defun my/org-latex-export-to-pdf (&optional (filename (buffer-name)))
      "Produce a PDF from the given ‘filename’, or otherwise current buffer,
       then open it in my default viewer.
      "
     (interactive)
     (org-latex-export-to-pdf)
     (let ((it (concat (file-name-sans-extension filename) ".pdf")))
       (eshell-command (concat "open " it  " & ")))
       (message (concat it " has been opened in your PDF viewer."))
       'success ;; otherwise we obtain a "compiler error".
    )


<a id="orgec76567"></a>

## Interpret the Haskell source blocks in a file

    (defvar *current-module* "NoModuleNameSpecified" 
      "The name of the module, file, that source blocks are 
       currently being tangled to.
    
       This technique is insipired by “Interactive Way to C”;
       see https://alhassy.github.io/InteractiveWayToC/.
      ")
    
    (defun current-module () 
      "Returns the current module under focus." 
      *current-module*)
    
    (defun set-module (name)
       "Set the name of the module currently under focus.
       
        Usage: When a module is declared, i.e., a new file has begun,
        then that source blocks header should be “:tangle (set-module ”name-here”)”.
        succeeding source blocks now inherit this name and so are tangled
        to the same module file. How? By placing the following line at the top
        of your Org file: “‘#+PROPERTY: header-args :tangle (current-module))’.
    
        This technique structures “Interactive Way to C”.
       "
       (setq *current-module* name)
    )
    
    (cl-defun my/org-run-haskell (&optional target (filename (buffer-name)))
      "Tangle Haskell source blocks of given ‘filename’, or otherwise current buffer,
       and load the resulting ‘target’ file into a ghci buffer.
    
       If no name is provided for the ‘target’ file that is generated from the
       tangeling process, it is assumed to be the buffer's name with a ‘hs’ extension.
    
       Note that this only loads the blocks tangled to ‘target’.
    
       For example, file ‘X.org’ may have haskell blocks that tangle to files
       ‘X.hs’, ‘Y.hs’ and ‘Z.hs’. If no target name is supplied, we tangle all blocks
       but only load ‘X.hs’ into the ghci buffer. A helpful technique to load the
       last, bottom most, defined haskell module, is to have the module declaration's
       source block be ‘:tangle (setq CODE “Y.hs”)’, for example; then the following
       code blocks will inherit this location provided our Org file has at the top
       ‘#+PROPERTY: header-args :tangle (current-module))’.
       Finally, our ‘compile-command’ suffices to be ‘(my/org-run-haskell CODE)’.
       ─
       This technique structures “Interactive Way to C”.
      "
       (let* ((it  (if target target (concat (file-name-sans-extension filename) ".hs")))
             (buf (concat "*GHCI* " it)))
    
         (toggle kill-buffer-query-functions nil (ignore-errors (kill-buffer buf)))
         (org-babel-tangle it "haskell")
         (async-shell-command (concat "ghci " it) buf) 
         (switch-to-buffer-other-window buf)
         (end-of-buffer)
       )
    )
    
    ;; Set this as the ‘compile-command’ in ‘Local Variables’, for example.


<a id="orga605017"></a>

# Expected IDE Support


<a id="orgc1cb02f"></a>

## Backups

By default, Emacs saves backup files &#x2013; those ending in ~ &#x2013; in the current directory, thereby cluttering it up. Let's place them in `~/.emacs.d/backups`, in case we need to look for a backup; moreover,
let's keep old versions since there's disk space to go around
&#x2013;what am I going to do with 500gigs when nearly all my ‘software’ is
textfiles interpreted within Emacs 😼

    ;; New location for backups.
    (setq backup-directory-alist '(("." . "~/.emacs.d/backups")))
    
    ;; Never silently delete old backups.
    (setq delete-old-versions -1)
    
    ;; Use version numbers for backup files.
    (setq version-control t)
    
    ;; Even version controlled files get to be backed up.
    (setq vc-make-backup-files t)

Why backups? Sometimes I may forget to submit a file, or edit, to my
version control system, and it'd be nice to be able to see a local
automatic backup. Whenever ‘I need space,’ then I simply empty
the backup directory, if ever.

Like package installations, my backups are not kept in any version control
system, like git; only locally.


<a id="org5b0e63c"></a>

## Mouse Editing Support

    ;; Text selected with the mouse is automatically copied to clipboard.
    (setq mouse-drag-copy-region t)


<a id="org03afc0a"></a>

## Having a workspace manager in Emacs

I've loved using XMonad as a window tiling manager.
I've enjoyed the ability to segregate my tasks
according to what ‘project’ I'm working on;
such as research, marking, Emacs play, etc.
With [perspective](https://github.com/nex3/perspective-el), I can do the same thing :-)

That is, I can have a million buffers, but only those
that belong to a workspace will be visible when I'm switching between buffers, for example.

    (use-package perspective)
    
    ;; Activate it.
    (persp-mode)
    
    ;; In the modeline, tell me which workspace I'm in.
    (persp-turn-on-modestring)

All commands are prefixed by `C-x x`; main commands:

-   **`s, n/→, p/←`:** ‘S’elect a workspace to go to or create it, or go to ‘n’ext one, or go to ‘p’revious one.
-   **`c`:** Query a perspective to kill.
-   **`r`:** Rename a perspective.
-   **`A`:** Add buffer to current perspective & remove it from all others.

As always, since we've installed `which-key`, it suffices to press
`C-x x` then look at the resulting menu 😃


<a id="org505556b"></a>

## Jump between windows using Cmd+Arrow & between recent buffers with Meta-Tab

    (use-package windmove
      :config
      ;; use command key on Mac
      (windmove-default-keybindings 'super)
      ;; wrap around at edges
      (setq windmove-wrap-around t))

The [docs](https://github.com/killdash9/buffer-flip.el) for the following have usage examples.

    (use-package buffer-flip
      :bind
       (:map buffer-flip-map
        ("M-<tab>" . buffer-flip-forward)
        ("M-S-<tab>" . buffer-flip-backward)
        ("C-g" . buffer-flip-abort))
      :config
        (setq buffer-flip-skip-patterns
            '("^\\*helm\\b"))
    )
    ;; key to begin cycling buffers.
    (global-set-key (kbd "M-<tab>") 'buffer-flip)


<a id="org4dc92d9"></a>

## Completion Frameworks

[Helm](http://tuhdo.github.io/helm-intro.html) provides possible completions and also shows recently executed commands when pressing `M-x`.

Extremely helpful for when switching between buffers, `C-x b`,
and discovering & learning about other commands!
E.g., press `M-x` to see recently executed commands and other possible commands!

Try and be grateful.

    (use-package helm 
     :diminish
     :init (helm-mode t)
     :bind
      ("C-x C-r" . helm-recentf)      ; search for recently edited  
    
      ;; Helm provides generic functions for completions to replace 
      ;; tab-completion in Emacs with no loss of functionality. 
      ("M-x" . 'helm-M-x)
      ;; ("C-x b". 'helm-buffers-list) ;; Avoid seeing all those *helm⋯* mini buffers!
      ("C-x b". 'helm-mini) ;; see buffers & recent files; more useful.
      ("C-x r b" .'helm-filtered-bookmarks)
      ("C-x C-f" . 'helm-find-files)
    
       ;; Show all meaningful Lisp symbols whose names match a given pattern.
       ;; Helpful for looking up commands.
       ("C-h a" . helm-apropos)
    
       ;; Look at what was cut recently & paste it in.
       ("M-y" . helm-show-kill-ring)
    )
    ;; (global-set-key (kbd "M-x") 'execute-extended-command) ;; Default “M-x”
    
    ;; Yet, let's keep tab-completetion anyhow.
    (define-key helm-map (kbd "TAB") #'helm-execute-persistent-action)
    (define-key helm-map (kbd "<tab>") #'helm-execute-persistent-action)
    ;; We can list ‘actions’ on the currently selected item by C-z.
    (define-key helm-map (kbd "C-z")  'helm-select-action)

When `helm-mode` is enabled, even help commands make use of it.
E.g., `C-h o` runs `describe-symbol` for the symbol at point,
and `C-h w` runs `where-is` to find the key binding of the symbol at point.
Both show a pop-up of other possible commands.

Incidentally, helm even provides an [interface](http://tuhdo.github.io/helm-intro.html#orgheadline24) for the top program via
`helm-top`. It also serves as an interface to popular search engines
and over 100 websites such as `google, stackoverflow`, and `arxive`.

    ;; (shell-command "brew install surfraw &")
    ;; 
    ;; Invoke helm-surfraw

If we want to perform a google search, with interactive suggestions,
then invoke `helm-google-suggest` &#x2013;which can be acted for other serves,
such as Wikipedia or Youtube by `C-z`. For more google specific options,
there is the `google-this` package.

Let's switch to a powerful searching mechanism &#x2013; [helm-swoop](https://github.com/ShingoFukuyama/helm-swoop).
It allows us to not only search the current buffer but also
the other buffers and to make live edits by pressing `C-c C-e`
when a search buffer exists. Incidentally, executing `C-s` on a word, region,
will search for that particular word, region; then apply changes by `C-x C-s`.

    (use-package helm-swoop
      :bind
      (
       ("C-s"     . 'helm-swoop)           ;; search current buffer
       ("C-M-s"   . 'helm-multi-swoop-all) ;; Search all buffer
       ;; Go back to last position where ‘helm-swoop’ was called
       ("C-S-s" . 'helm-swoop-back-to-last-point)
      )
     :config ;; Following from helm-swoop's github page.
       ;; Give up colour for speed.
      (setq helm-swoop-speed-or-color nil)
      ;; If this value is t, split window inside the current window
      (setq helm-swoop-split-with-multiple-windows nil)
      ;; If there is no symbol at the cursor, use the last used words instead.
      (setq helm-swoop-pre-input-function
          (lambda ()
            (let (($pre-input (thing-at-point 'symbol)))
              (if (eq (length $pre-input) 0)
                  helm-swoop-pattern ;; this variable keeps the last used words
                $pre-input))))
    )

Press `M-i` after a search has executed to enable it for all buffers.

We can also limit our search to org files, or buffers of the same mode,
or buffers belonging to the same project!

Note that on the Mac, I can still perform default Emacs search using
*Cmd+f*.

Finally, let's enable [“complete anything” mode](https://company-mode.github.io/)
&#x2013;it ought to start in half a second and only need two characters to get going,
which means word suggestions are provided and so I need only type partial words
then tab to get the full word!

    (use-package company
      :diminish
      :config
        (setq company-dabbrev-other-buffers t
              company-dabbrev-code-other-buffers t
            
              ;; Allow (lengthy) numbers to be eligible for completion.
              company-complete-number t
              
              ;; M-⟪num⟫ to select an option according to its number.
              company-show-numbers t
    
              ;; Only 2 letters required for completion to activate.
              company-minimum-prefix-length 2
            
              ;; Do not downcase completions by default.
              company-dabbrev-downcase nil
            
              ;; Even if I write something with the ‘wrong’ case,
              ;; provide the ‘correct’ casing.
              company-dabbrev-ignore-case t
    
              ;; Immediately activate completion.
              company-idle-delay 0
              )
    
        (global-company-mode 1)
    )
    ;; So fast that we don't need this.
    ;; (global-set-key (kbd "C-c h") 'company-complete)

Note that `M-/` goes through a sequence of completions.
Note that besides the arrow keys, we can also use `C-` or `M-` with `n, p` to
navigate the options. Note that [by default](https://github.com/company-mode/company-mode/issues/360) company mode does not support completion for
phrases containing hyphens &#x2013;this can be altered, if desired.

Besides boring word completion, let's add support for [emojis](https://github.com/dunn/company-emoji).

    (use-package company-emoji)
    (add-to-list 'company-backends 'company-emoji)

For example: 🥞 💻 🐵 ✉️😉 🐬 🌵.

➡️On a new line, write `:` then any letter to have a tool-tip appear.
All emoji names are lowercase. ◀

The libraries `emojify, emojify-logos` provides cool items like :haskell: :emacs: :org: :ruby: :python:.
Unfortunately they do not easily export to html with org-mode, so I'm not using
them.


<a id="org034c782"></a>

## Snippets &#x2013; Template Expansion

It is common that there is a sequence of text that we tend to repeat
often, possibly with a name or some other parameter altered.
Such a snippet could be written once then provided by a simple
Lisp insert command with the parameters being queried. Luckily, others
have written such pleasant utilities.

[Yasnippet](http://joaotavora.github.io/yasnippet/snippet-development.html) is a pleasant utility for template expansion with the alluring
feature to allow arbitrary Lisp code to be executed during expansion.
The declaration of templates is verbose, requiring a particular file
hierarchy, as such I utilise [Yankpad](https://github.com/Kungsgeten/yankpad) which allows me to employ
an Org-mode approach: Each template corresponds to an org heading of
the form `Key:Words:For:Expansion:Here: name of snippet here` and the
template body is then the body of the org heading.
Any of `Key, Words, For, Expansion, Here` will rewrite into the body
of the org tree. This is much more terse, and I even don't bother
with that; instead preferring to tangle my templates using yankpad
as a mere interface.

    ;; Yet another snippet extension program
    (use-package yasnippet
      :diminish yas-minor-mode
      :config
        (yas-global-mode 1)
        ;; respect the spacing in my snippet declarations
        (setq yas-indent-line 'fixed)
    )
    
    ;; Nice “interface” to said program
    (use-package yankpad
      ;; :if company-mode ;; load & initialise only if company-mode is defined
      :init
        ;; Location of templates
        (setq yankpad-file "~/.emacs.d/yankpad.org")
      :config
        ;; If you want to complete snippets using company-mode
        ;; (add-to-list 'company-backends #'company-yankpad)
        ;; If you want to expand snippets with hippie-expand
        (add-to-list 'hippie-expand-try-functions-list #'yankpad-expand)
        ;; Load the snippet templates -- useful after yankpad is altered 
        ;; (add-hook 'after-init-hook 'yankpad-reload)
        (setq yankpad-category "Category: Default")
    )
    
    ;; Elementary textual completion backend.
    (setq company-backends
       (add-to-list 'company-backends 'company-dabbrev))
    ;; 
    ;; Add yasnippet support for all company backends
    ;; https://emacs.stackexchange.com/a/10520/10352
    ;;
    (defvar company-mode/enable-yas t
      "There can only be one main completition backend, so let's
       enable yasnippet/yankpad as a secondary for all completion backends.")
    
    (defun company-mode/backend-with-yas (backend)
      (if (or (not company-mode/enable-yas)
              (and (listp backend) (member 'company-yankpad backend)))
          backend
        (append (if (consp backend) backend (list backend))
                '(:with company-yankpad))))
    
    (setq company-backends (mapcar #'company-mode/backend-with-yas company-backends))

With these settings, along with the `company` backend, I may type a keyword
then “tab” it into expansion.

Yankpad requires we have an org file that contains our templates,
so we tangle such a file `~/.emacs.d/yankpad.org`, and have all of our
templates be globally accessible.

    #+Description: This is file is generated from my init.org; do not edit. 
    
    * Default                                           :global:

Here's an example of a common template I perform by hand &#x2013;no more!
I have the expected habit of copying a URL from someplace then forming
a link to it by writing `[[URL] [description]]`, since the URL & syntax are already
known, let's expand those and place the cursor at the only unknown &#x2013;the description.

    ** my-org-insert-link: cleverly insert a link copied to clipboard
     [[${1:`(clipboard-yank)`}][$2]] $0

What's going on here?

1.  This template is expanded with the keyword `my-org-insert-link`, then “tab”.
2.  The cursor lands at position `$1`, which has default text being the result
    of evaluating `(clipboard-yank)`. 
    
    We may evaluate Lisp code anywhere by enclosing it in backticks.

3.  If we're satisfied with the current field, we simply tab to the next field.
    Otherwise, we simply write text &#x2013;which overwrites the default text.

4.  After enough tabbing we complete the template and the cursor lands
    at position `$0`.

⟪ Having default or mirrored text for `$2` would not allow me to see the URL
field, lest I wish to change it or at least confirm it's what I want.
Hence, the `$2` field has no default. ⟫

Let's overwrite the usual way to insert such links, via `C-c C-l`.

    (cl-defun org-insert-link ()
      "Makes an org link by inserting the URL copied to clipboard
      and prompting for the link description only.
    
      Type over the shown link to change it, or tab to move to the description
      field.
    
      This overrides Org-mode's built-in ‘org-insert-link’ utility.
      "
      (interactive)
      (insert "my-org-insert-link")
      (yankpad-expand)
    )

The [Yasnippe manual](http://joaotavora.github.io/yasnippet/snippet-development.html) is an accessible read, as is the 
 [Yankpad manual](https://github.com/Kungsgeten/yankpad), and showcases many other utilities; such as
having certain snippets being activated enabled only in particular
modes or on demand. Of note is that field `$n` can be accessed in 
code with the invocation `(yas-field-value n)`.

The rest of this section is other templates, not much for now,
concluding with actually loading this snippet mechanism globally.


### Org-mode Templates &#x2013;A reason I “generate” templates ;)

This produces a pop-up list of org-mode block types, if `src` is
selected, then a list of my commonly used languages pops-up.
Alternatively, ignore the pop-up menu and write any block or language name.

    ** begin: produce an org-mode block
    #+begin_${1:environment$(let* 
        ((block '("src" "example" "quote" "verse" "center" "latex" "html" "ascii"))
         (langs '("c" "emacs-lisp" "lisp" "latex" "python" "sh" "haskell" "plantuml" "prolog"))
         (type (yas-choose-value block)))
         (concat type (when (equal type "src") (concat " " (yas-choose-value langs)))))}
     $0
    #+end_${1:$(car (split-string yas-text))}

In this case, `yas-text` is equivalent to (`yas-field-value 1)`;
it generally refers to the value of the field being mirrored with `${n: ⋯yas-text⋯}`.

However, going through pop-ups takes precious time.
Let's introduce a template for my most utilised kind of language blocks.

    ** s-el: Elisp org-block
    #+begin_src emacs-lisp
    $0
    #+end_src

However, doing this for each language I want is a waste of time
and textual space. Why? The purpose of templates is to reduce repetition,
yet the above block would be repeated with only 3 parts ‘unknown’: 
The expansion keyword, the description, and the org-mode source block name.
Whence,

    (defun make-lang-template (key lang)
      "We make an org-mode source block snippet template.
      
      ‘key’ is the expansion word key for the language ‘lang’;
      the description for the snippet is also ‘lang’.
      "
      (s-join "\n" `(
        ,(concat "** " key ": " lang)
        ,(concat "#+begin_src " lang)
        "$0"
        "#+end_src"
        "\n"
      ))
    )

The template *text* is then generated by the following simple loop
&#x2013;whose source block is named `my-org-lang-templates`.

    (let (result) ;; ensure result is initially empty
       (dolist (x '( ("s_el" . "emacs-lisp")
                     ("s_org" . "org")
                     ("s_hs" . "haskell")
                     ("s_ag" . "agda2")
                     ("s_c" . "c")
                     ("s_lx" . "latex")
                   ) result)
          (setq result (concat result "\n" (make-lang-template (car x) (cdr x))))
       )   
    )

The *resulting text* of this block, generated below, is tangled to our yankpad
by utilising a [noweb](https://www.gnu.org/software/emacs/manual/html_node/org/Noweb-reference-syntax.html) source block invocation:

    #+begin_src org  :tangle "~/.emacs.d/yankpad.org" :noweb yes
    <<my-org-lang-templates()>>
    #+end_src

    
    ** s_el: emacs-lisp
    #+begin_src emacs-lisp
    $0
    #+end_src
    
    
    ** s_org: org
    #+begin_src org
    $0
    #+end_src
    
    
    ** s_hs: haskell
    #+begin_src haskell
    $0
    #+end_src
    
    
    ** s_ag: agda2
    #+begin_src agda2
    $0
    #+end_src
    
    
    ** s_c: c
    #+begin_src c
    $0
    #+end_src
    
    
    ** s_lx: latex
    #+begin_src latex
    $0
    #+end_src

Now `s-`, due to company mode, brings up a list of languages
that I can then simply scroll down through, then “enter” upon to
expand. Moreover, the prefix `s-` means that the key is mostly irrelevant,
since I needn't remember it because company-mode immediately lists possible completions.
Super neat stuff :-)

Ain't this reminiscent of meta-programming ;-)

⟪ Incidentally, I originally wrote an Elisp script to temporarily
open the yankpad, then append the desired text. However, such
an approach is brittle: I have to manually execute said script.

In contrast, using noweb invocations to tangle the results is
more flexible: Any time the tangling is performed, the yankpad
is kept up to date &#x2013;no personal intervention from myself.

Observe that noweb could be utilised in a similar fashion to 
[share key-value pairs across different source files](https://www.wisdomandwonder.com/article/10603/two-ways-to-share-static-key-pair-values-across-different-tangled-source-files-with-org-mode-literate-programming).
⟫


### Elisp Templates

    ** loop:  Elisp's for each loop
    (dolist (${1:var} ${2:list-form})
            ${3:body})
    
    ** defun: Lisp functions
    (cl-defun ${1:fun-name} (${2:arguments})
      "${3:documentation}"
      $0
    )
    
    ** cond: Elisp conditionals
    (cond (${1:scenario₁} ${2:response₁})
          (${3:scenario₂} ${4:response₂})
    )


### Equational Templates

    ** fun: Function declaration with type signature 
    
    ${1:fun-name} : ${2:arguments}
    $1 ${3:args} = ?$0
    
    ** eqn_begin: Start a ≡-Reasoning block in Agda
    
    begin
      ${1:left-hand-side}
    ≡⟨ ${3:reason-for-the-equality} ⟩
      ${2:right-hand-side}
    $0∎
    
    ** eqn_step: Insert a step in a ≡-Reasoning block in Agda
    ≡⟨ ${2:reason-for-the-equality} ⟩
      ${1:new-expression}
    $0


### Misc Templates

    ** remark: top-level literate comment
    
    {{{remark(${1:thoughts})}}} $0

Where my local use contains `#+MACRO: remark  @@latex: \fbox{\textbf{Comment: $1 }}@@`.


<a id="org2a61b82"></a>

# Helpful Functions & Shortcuts

Here is a collection of Emacs-lisp functions that I have come to use in other files.

Disclaimer: I wrote much of the following *before* I learned any lisp; everything below is probably terrible.

Let's save a few precious seconds,

    ;; change all prompts to y or n
    (fset 'yes-or-no-p 'y-or-n-p)


<a id="orgf5ce1f3"></a>

## Bind `recompile` to `C-c C-m` &#x2013; “m” for “m”ake

    (defvar my-keys-minor-mode-map
      (let ((map (make-sparse-keymap)))
        (define-key map (kbd "C-c C-m") 'recompile)
        map)
      "my-keys-minor-mode keymap.")
    
    (define-minor-mode my-keys-minor-mode
      "A minor mode so that my key settings override annoying major modes."
      :init-value t
      :lighter " my-keys")
    
    (my-keys-minor-mode)
    
    (diminish 'my-keys-minor-mode) ;; Don't show it in the modeline.


<a id="org541739c"></a>

## Reload buffer with `f5`

I do this so often it's not even funny.

    (global-set-key [f5] '(lambda () (interactive) (revert-buffer nil t nil)))

In Mac OS, one uses `Cmd-r` to reload a page and Emacs binds buffer reversion to `Cmd-u`
&#x2013;in Emacs, Mac's `Cmd` is referred to as the ‘super key’ and denoted `s`.

Moreover, since I use Org-mode to generate code blocks and occasionally
inspect them, it would be nice if they automatically reverted when they
were regenerated &#x2013;Emacs should also prompt me if I make any changes!

    ;; Auto update buffers that change on disk.
    ;; Will be prompted if there are changes that could be lost.
    (global-auto-revert-mode 1)


<a id="org0fa6e12"></a>

## Kill to start of line

Dual to `C-k`,

    ;; M-k kills to the left
    (global-set-key "\M-k" '(lambda () (interactive) (kill-line 0)) )


<a id="org75d6e92"></a>

## `file-as-list` and `file-as-string`

Disclaimer: I wrote the following *before* I learned any lisp; everything below is probably terrible.

    (defun file-as-list (filename)
      "Return the contents of FILENAME as a list of lines"
      (with-temp-buffer
        (insert-file-contents filename)
        (split-string (buffer-string))))
    
    (defun file-as-string (filename)
      "Return the contents of FILENAME as a list of lines"
      (with-temp-buffer
        (insert-file-contents filename)
        (buffer-string)))


<a id="orgc9e6076"></a>

## `kill-other-buffers`

    (defun kill-other-buffers ()
      "Kill all other buffers."
      (interactive)
      (mapc 'kill-buffer (delq (current-buffer) (buffer-list))))


<a id="orga03f57f"></a>

## Switching from 2 horizontal windows to 2 vertical windows

I often find myself switching from a horizontal view of two windows in Emacs to a
vertical view. This requires a variation of `C-x 1 RET C - x 3 RET C-x o X-x b RET`. 
Instead I now only need to type `C-|` to make this switch.

    (defun ensure-two-vertical-windows () 
      "I used this method often when programming in Coq."
     (interactive)
     (other-window 1)			;; C-x 0
     (let ((otherBuffer (buffer-name))) 
       (delete-window)			;; C-x 0
       (split-window-right)			;; C-x 3
       (other-window 1)			;; C-x 0
       (switch-to-buffer otherBuffer)	;; C-x b RET
     )
     (other-window 1)
    )
    (global-set-key (kbd "C-|") 'ensure-two-vertical-windows)


<a id="org8cb85ed"></a>

## `re-replace-in-file`

Disclaimer: I wrote the following *before* I learned any lisp; everything below is probably terrible.

    (defun re-replace-in-file (file regex whatDo) 
       "Find and replace a regular expression in-place in a file.
    
       Terrible function … before I took the time to learn any Elisp!
       "
    
        (find-file file)
        (goto-char 0)
        (let ((altered (replace-regexp-in-string regex whatDo (buffer-string))))
          (erase-buffer)
          (insert altered)
          (save-buffer)
          (kill-buffer)
       )
    )

Example usage:

    ;; Within mysite.html we rewrite: <h1.*h1>   ↦   <h1.*h1>\n NICE
    ;; I.e., we add a line break after the first heading and a new word, “NICE”.
    (re-replace-in-file "mysite.html"
                        "<h1.*h1>"
                        (lambda (x) (concat x "\n NICE")))


### `mapsto`: Simple rewriting for current buffer

    (defun mapsto (this that)
      "In the current buffer make the regular expression rewrite: this ↦ that."
      (let* ((current-location (point))
           ;; Do not alter the case of the <replacement text>.
           (altered (replace-regexp-in-string this (lambda (x) that) (buffer-string) 'no-fixed-case))
           )
          (erase-buffer)
          (insert altered)
          (save-buffer)
          (goto-char current-location)
      )
    )


<a id="orgea7baba"></a>

## Obtaining Values of `#+KEYWORD` Annotations

Org-mode settings are, for the most part, in the form `#+KEYWORD: VALUE`. Of notable interest
are the `TITLE` and `NAME` keywords. We use the following `org-keywords` function to obtain
the values of arbitrary `#+THIS : THAT` pairs, which may not necessarily be supported by native
Org-mode &#x2013;we do so for the case, for example, of the `CATEGORIES` and `IMAGE` tags associated with an article.

    ;; Src: http://kitchingroup.cheme.cmu.edu/blog/2013/05/05/Getting-keyword-options-in-org-files/
    (defun org-keywords ()
      "Parse the buffer and return a cons list of (property . value) from lines like: #+PROPERTY: value"
      (org-element-map (org-element-parse-buffer 'element) 'keyword
                       (lambda (keyword) (cons (org-element-property :key keyword)
                                               (org-element-property :value keyword)))))
    
    (defun org-keyword (KEYWORD)
      "Get the value of a KEYWORD in the form of #+KEYWORD: value"
      (cdr (assoc KEYWORD (org-keywords))))

Note that capitalisation in a ”#+KeyWord” is irrelevant.

See [here](https://orgmode.org/manual/Org-syntax.html) on how to see the abstract syntax tree of an org file
and how to manipulate it.


<a id="org4400e0a"></a>

## Quickly pop-up a terminal, run a command, close it

    (cl-defun toggle-terminal (&optional (name "*eshell-pop-up*"))
       "Pop up a terminal, do some work, then close it using the same command.
    
       The toggle behaviour is tied into the existence of the pop-up buffer.
       If the buffer exists, kill it; else create it.
       "
       (interactive)
       (cond 
         ;; when the terminal buffer is alive, kill it.
         ((get-buffer name)  (kill-buffer name) 
                             (ignore-errors (delete-window)))
         ;; otherwise, set value to refer to a new eshell buffer.
         (t                  (split-window-right)
                             (other-window 1)
                             (eshell)
                             (rename-buffer name))
       )
    )
    
    (global-set-key "\C-t" 'toggle-terminal)


<a id="org7e99e69"></a>

## `C-x k` kills current buffer

By default `C-x k` prompts to select which buffer
should be selected. I almost always want to kill
the current buffer, so let's not waste time making
such a tedious decision.

    ;; Kill current buffer; prompt only if
    ;; there are unsaved changes.
    (global-set-key (kbd "C-x k")
      '(lambda () (interactive) (kill-buffer (current-buffer))))


<a id="org2726e05"></a>

## Publishing articles to my personal blog

I try to [blog](https://alhassy.github.io/) occasionally, so here's a helpful function to quickly
publish the current article to my blog.

    (define-key global-map "\C-cb" 'my/publish-to-blog)
    
    (cl-defun my/publish-to-blog (&optional (draft nil) (local nil))
      "
      Using ‘AlBasmala’ setup to publish current article to my blog.
      Details of AlBasmala can be found here:
      https://alhassy.github.io/AlBasmala/
    
      Locally: ~/alhassy.github.io/content/AlBasmala.org
      
      A ‘draft’ will be produced in about ~7 seconds, but does not re-produce
      a PDF and the article has a draft marker near the top. Otherwise,
      it will generally take ~30 seconds due to PDF production, which is normal.
      The default is not a draft and it takes ~20 seconds for the live
      github.io page to update.
      
      The ‘local’ optiona indicates whether the resulting article should be
      viewed using the local server or the live webpage. Live page is default.
    
      When ‘draft’ and ‘local’ are both set, the resulting page may momentarily
      show a page-not-found error, simply refresh.
      "
    
      (load-file "~/alhassy.github.io/content/AlBasmala.el")
      (preview-article :draft draft)
      (unless draft (publish))
      (let ((server (if local "http://localhost:4000/" "https://alhassy.github.io/")))
        (async-shell-command (concat "open " server NAME "/") "*blog-post-in-browser*"))
    )


<a id="orge3cff49"></a>

# Summary of Utilities Provided

<table border="2" cellspacing="0" cellpadding="6" rules="groups" frame="hsides">


<colgroup>
<col  class="org-left" />

<col  class="org-left" />
</colgroup>
<tbody>
<tr>
<td class="org-left"><span class="underline">Command</span></td>
<td class="org-left"><span class="underline">Action</span></td>
</tr>


<tr>
<td class="org-left">`C-c C-m`</td>
<td class="org-left">recompile file</td>
</tr>


<tr>
<td class="org-left">`<f5>`</td>
<td class="org-left">revert buffer</td>
</tr>


<tr>
<td class="org-left">`M-x k`</td>
<td class="org-left">kill to start of line</td>
</tr>


<tr>
<td class="org-left">`C-∣`</td>
<td class="org-left">toggle 2 windows from horizontal to vertical view</td>
</tr>


<tr>
<td class="org-left">`(file-as-list   pathHere)`</td>
<td class="org-left">construe a file as a list of lines</td>
</tr>


<tr>
<td class="org-left">`(file-as-string pathHere)`</td>
<td class="org-left">construe a file as a string</td>
</tr>


<tr>
<td class="org-left">(`re-replace-in-file file regex whatDo)`</td>
<td class="org-left">perform an in-file regular expression rewrite</td>
</tr>


<tr>
<td class="org-left">`(mapsto this that)`</td>
<td class="org-left">regex rewrite in current buffer: this ↦ that</td>
</tr>


<tr>
<td class="org-left">`M-x create-scratch-buffer`</td>
<td class="org-left">&#x2013;self evident--</td>
</tr>


<tr>
<td class="org-left">`M-x kill-other-buffers`</td>
<td class="org-left">&#x2013;self evident--</td>
</tr>


<tr>
<td class="org-left">`M-$`</td>
<td class="org-left">check spelling of word at point</td>
</tr>


<tr>
<td class="org-left">`M-#`</td>
<td class="org-left">thesaurus look-up word at point</td>
</tr>


<tr>
<td class="org-left">`(toggle name val ⋯)`</td>
<td class="org-left">*Effectfully* set `name` to `val` only for scope `⋯`.</td>
</tr>


<tr>
<td class="org-left">`(my/org-run-haskell &optional file)`</td>
<td class="org-left">Interpret the Haskell org-blocks from a file into ghci.</td>
</tr>


<tr>
<td class="org-left">`C-+/-`</td>
<td class="org-left">increase/decrease text size</td>
</tr>


<tr>
<td class="org-left">`M-x my-org-html-export-to-html`</td>
<td class="org-left">make then open html from an org file</td>
</tr>


<tr>
<td class="org-left">`C-c C-c`</td>
<td class="org-left">execute code in an org `src` block</td>
</tr>


<tr>
<td class="org-left">`<E`</td>
<td class="org-left">produce an emacs-lisp `src` block</td>
</tr>


<tr>
<td class="org-left">`<g`</td>
<td class="org-left">produce a graph template `src` block</td>
</tr>


<tr>
<td class="org-left">`C-x t`</td>
<td class="org-left">open a new untitled org template file</td>
</tr>


<tr>
<td class="org-left">`(org-keywords)`</td>
<td class="org-left">get `#+Property: Value` pairs from an org file</td>
</tr>


<tr>
<td class="org-left">`(org-keyword property)`</td>
<td class="org-left">get the `value` of a given org `#+property`</td>
</tr>
</tbody>
</table>

Since I'm using `use-package`, I can invoke `M-x describe-personal-keybindings` to see what key bindings I've defined.
Since not all my bindings are via `use-package`, it does not yet cover all of my bindings.

We could run `C-h b` to see our bindings:

    (use-package helm-descbinds
      :defer t
      :bind (("C-h b" . helm-descbinds)))

Finally, we can observe which features are active in our current Emacs with,

    (message "Features: %s" features)

Some possibly interesting reads:

-   [How to Learn Emacs: A Hand-drawn One-pager for Beginners / A visual tutorial](https://sachachua.com/blog/wp-content/uploads/2013/05/How-to-Learn-Emacs-v2-Large.png)
-   [Emacs Mini-Manual, Part I of III](https://tuhdo.github.io/emacs-tutor.html)
-   [A list of people's nice emacs config files](https://github.com/caisah/emacs.dz)
-   [Awesome Emacs](https://github.com/emacs-tw/awesome-emacs): A community driven list of useful Emacs packages, libraries and others.
-   [Org and R Programming](https://github.com/erikriverson/org-mode-R-tutorial/blob/master/org-mode-R-tutorial.org) ;;  a tutorial on literate programming, e.g., evaluating code within `src` bloc.
-   [The GNU Emacs Reference Card](https://www.gnu.org/software/emacs/refcards/pdf/refcard.pdf)
-   [The Org-mode Reference Card](https://www.gnu.org/software/emacs/refcards/pdf/orgcard.pdf)
-   [An Elisp Reference Card](https://github.com/alhassy/ElispCheatSheet/blob/master/CheatSheet.pdf)

