# Contributing to {{My Theme}}

If you are a developer for UCF and want to contribute to this theme, we'd love to hear from you.  This document outlines the best ways to submit new ideas or inform us of bugs.

Please take a moment to review this document before submitting new issues or pull requests in order to make the contribution process easy and effective for everyone involved.


## Using the issue tracker

The [issue tracker](https://github.com/UCF/{{My-Theme}}/issues) in Github is the preferred channel for [bug reports](#bug-reports), [features requests](#feature-requests) and [submitting pull requests](#pull-requests).

Please do not use the issue tracker for personal support requests.  The [#help-themes Slack channel](https://ucf-wp.slack.com/messages/help-themes/) in the ucf-wp Slack group is the best place to get help with your project.  {{Consider referencing a theme-specific channel instead, if one is available.}}


## Bug reports

A bug is a demonstrable problem that is caused by the code in the repository. Concise and thorough bug reports will help us fix reported problems more quickly and effectively.

### Before submitting a bug report
Please follow the instructions below **before** submitting a new bug report:

1. **Use the GitHub issue search** &mdash; check if the issue has already been reported.

2. **Check if the issue has been fixed** &mdash; if you're not running the latest version of the theme, please check your code against the repo's `master` branch first (`master` will always contain the latest, stable project code). If you are running the latest version, make sure the problem isn't already resolved in an upcoming [milestone](https://github.com/UCF/{{My-Theme}}/milestones).

### Submit a bug report
Assuming you've followed all of these steps and still have a valid bug report to submit, you can submit a new bug report by [creating a new issue in Github](https://github.com/UCF/{{My-Theme}}/issues/new).

Add a descriptive, understandable title and details about the bug in the description field. Please try to be as detailed as possible in your report. What steps will reproduce the issue? What browser(s) and OS experience the problem? Do other browsers show the bug differently? What would you expect to be the outcome? All these details will help us fix any potential bugs more quickly.

Example:

> Short and descriptive example bug report title
>
> A summary of the issue and the browser/OS environment in which it occurs. If
> suitable, include the steps required to reproduce the bug.
>
> 1. This is the first step
> 2. This is the second step
> 3. Further steps, etc.
>
> `<url>` - a link to the reduced test case
>
> Any other information you want to share that is relevant to the issue being
> reported. This might include the lines of code that you have identified as
> causing the bug, and potential solutions (and your opinions on their
> merits).


## Feature requests

We welcome new feature requests, but before submitting a new request, think carefully about whether said feature aligns with the [goals of the project](https://github.com/UCF/{{My-Theme}}/wiki/#Project-goals) and with [UCF's brand](https://www.ucf.edu/brand/). We strongly encourage the discussion of new feature ideas in the ucf-wp Slack group.

Please provide as much detail and context as possible to justify the inclusion of your idea in the theme. We reserve the right to deny feature requests when they don't align with the project's goals, or if said feature is already accomplishable with existing utilities/components.

You can submit a new feature request by [creating a new issue in Github](https://github.com/UCF/{{My-Theme}}/issues/new).


## Pull requests

**Please ask first** before embarking on any significant pull request (e.g. implementing features, refactoring code); otherwise you risk spending a lot of time working on something that the theme's maintainers might not want to merge into the project. Generally speaking, pull requests should be related to existing issues that have been acknowledged by a UCF Marketing developer.

All pull requests should remain focused in scope and avoid containing unrelated commits.

Please adhere to the [coding guidelines](#code-guidelines) used throughout the project (indentation, accurate comments, etc.). Code that does not adhere to these standards will not be merged into the project.

### How to submit a pull request

Adhering to the following process is the best way to submit a pull request:

1. [Fork](https://help.github.com/articles/fork-a-repo/) the project.
2. Clone your fork, and configure the remotes:

   ```bash
   # Clone your fork of the repo into the current directory
   git clone https://github.com/<your-username>/{{My-Theme}}.git
   # Navigate to the newly cloned directory
   cd {{My-Theme}}
   # Assign the original repo to a remote called "upstream"
   git remote add upstream https://github.com/UCF/{{My-Theme}}.git
   ```

3. If you cloned a while ago, get the latest changes from upstream:

   ```bash
   git checkout master
   git pull upstream master
   ```

4. Create a new topic branch to contain your feature, change, or fix.

    New branches **must** be branched off of the most recent existing `rc-*` branch (typically there will only be one open at a time), or off of `master` directly, if no `rc-*` branch exists.

    **Never create _any_ new branch from the `develop` branch**--`develop` exists solely for project maintainers' usage and is considered a "dirty" branch. **Branches created from `develop` will not be merged into the project.**

   ```bash
   git checkout -b <topic-branch-name>
   ```

5. Commit your changes in logical chunks. Please provide helpful, readable commit messages (avoid nondescriptive messages such as "bugfix" or "minor change").

    If you're making changes to scss or js files, make sure you're minifying **and committing** those minified file changes.  scss and js file processing should be performed using gulp commands provided in the repo (see [gulpfile.js](https://github.com/UCF/{{My-Theme}}/blob/master/gulpfile.js))

6. Locally merge the upstream `rc-*` or `master` branch (whichever you branched off of initially) into your topic branch:

   ```bash
   git merge --no-ff upstream master
   ```

7. Push your topic branch up to your fork:

   ```bash
   git push origin <topic-branch-name>
   ```

8. [Open a Pull Request](https://help.github.com/articles/about-pull-requests/)
    with a clear title and description against the branch your topic branch was initially branched off of.


## Code guidelines

### HTML

[Adhere to the mdo Code Guide.](http://codeguide.co/#html)

- Use tags and elements appropriate for an HTML5 doctype (e.g., self-closing tags).
- Use CDNs and HTTPS when referencing third-party JS.
- Use [WAI-ARIA](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA) attributes when appropriate to promote accessibility.

### CSS/Sass

Adhere to the [mdo Code Guide](http://codeguide.co/#css) for basic CSS formatting guidelines, except for what's noted below.

Use [CSS-Tricks' Sass Style Guide](https://css-tricks.com/sass-style-guide/) for Sass-specific features (e.g. order of extends, mixin inclusions, etc in a ruleset).

- Declaration order: declarations should be in alphabetical order.
- Selectors: all selectors in a ruleset should be on their own line.
- All generated color pallettes and font sizes/weights should comply with [WCAG 2.0 AA contrast guidelines](https://www.w3.org/TR/WCAG20/#visual-audio-contrast) in their default state.  Components and utilities with hover/focus/active states should try to comply with these contrast requirements whenever possible.
- Except in rare cases, don't remove default `:focus` styles (via e.g. `outline: none;`) without providing alternative styles. See [this A11Y Project post](http://a11yproject.com/posts/never-remove-css-outlines/) for more details.

### JS

[Adhere to the jQuery Coding Standards and Best Practices](http://lab.abhinayrathore.com/jquery-standards/).

- 2 spaces (no tabs)
- Don't use [jQuery event alias convenience methods](https://github.com/jquery/jquery/blob/master/src/event/alias.js) (such as `$().focus()`). Instead, use [`$().trigger(eventType, ...)`](https://api.jquery.com/trigger/) or [`$().on(eventType, ...)`](https://api.jquery.com/on/), depending on whether you're firing an event or listening for an event. (For example, `$().trigger('focus')` or `$().on('focus', function (event) { /* handle focus event */ })`) We do this to be compatible with custom builds of jQuery where the event aliases module has been excluded.