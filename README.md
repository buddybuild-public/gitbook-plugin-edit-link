GitBook Plugin: Edit Link
=========================

This GitBook Plugin adds an "Edit This Page" link to every page's
toolbar. The link targets that page's source file on Github, or Gitlab,
or any repo.

## Screenshot

![gitbook-plugin-edit-link](https://cloud.githubusercontent.com/assets/4115/5695161/f5b79002-99b8-11e4-821a-d2af6c729348.png)

## Usage

### Step #1 - Update the `book.json` file

1. In your GitBook's `book.json` file, add `edit-link` to `plugins` list.

2. In `pluginsConfig`, set the `base` value, which is the base path to your
   GitHub, or GitLab, or other code repo. The trailing slash is NOT required.

3. By default, the link label is "Edit This Page". You can change it by
   configuring `label`.

#### Sample `book.json` file for gitbook version 2.0.1 and above

```
{
  "gitbook": "2.0.1",
  "plugins": [
    "edit-link@https://github.com/buddybuild-public/gitbook-plugin-edit-link.git"
  ],
  "pluginsConfig": {
    "edit-link": {
      "base": "https://github.com/USER/REPO/edit/BRANCH/path/to/book",
      "label": "Edit This Page"
    }
  }
}
```

#### Sample `book.json` file for gitbook version 2.0.1+ and multilingual labels

```
{
  "gitbook": "2.0.1",
  "plugins": [
    "edit-link@https://github.com/buddybuild-public/gitbook-plugin-edit-link.git"
  ],
  "pluginsConfig": {
    "edit-link": {
      "base": "https://github.com/USER/REPO/edit/BRANCH/path/to/book",
      "label": {
        "en": "Edit This Page",
        "de": "Seite bearbeiten"
      }
    }
  }
}
```

#### Sample `book.json` file for older gitbook versions <= 1.5.0

```
{
  "gitbook": "1.5.0",
  "plugins": ["edit-link@1.1.0"],
  "pluginsConfig": {
    "edit-link": {
      "base": "https://github.com/USER/REPO/edit/BRANCH/path/to/book",
      "label": "Edit This Page"
    }
  }
}
```

**Note**: The above snippet can be used as complete `book.json` file, if
your book doesn't have one yet.

**Github/Gitlab**: In the `base` string `...REPO/edit/BRANCH...`, you
may replace `edit` with `tree` if you want source file to open in
read-mode, rather than edit-mode directly on GitHub/GitLab.

#### Configuration Summary

The following configuration items are available (these need to appear in
the `pluginsConfig` => `edit-link` section, as demonstrated above):

- `base`:     Specifies the base URL within your book's repo.
- `icon`:     The classname(s) for the button's icon. Defaults to
              `fa fa-edit` (a [FontAwesome](http://fontawesome.io/icons/)
              icon).
- `label`:    The label for the button. Defaults to `Edit This Page`.
- `aria`:     The ARIA label for the button.
- `position`: The position of the button in the toolbar, `left` or
              `right`. Defaults to `left`.

### Step #2 - GitBook commands

1. Run `gitbook install`. It automatically installs the `edit-link`
   GitBook plugin for your book. This is needed only once.

2. Build your book (`gitbook build`) or serve (`gitbook serve`) as usual.


## Troubleshooting

1. If you are not seeing the "Edit this page" link, check if your
   `book.json` is valid. You can use this online tool -
   [http://json.parser.online.fr/beta/](http://json.parser.online.fr/beta/)

2. Check if you are using default GitBook theme; this plugin assumes
   that you are. It is NOT recommended to modify GitBook themes
   directly.


## Changelog

**2.1.1 - 10 August 2017**

- Added option to specify a custom CSS class, `cssclass`.
- Renamed `title` to `aria` in `package.json`.

**2.1 - 09 August 2017**

- Added defense agaist undefined GitBook language, per
  [@matsu-chara](https://github.com/matsu-chara/gitbook-plugin-edit-link/commit/5ebbd9f0b813df974c881753c56b81d529476699).
- Added option to specify the `icon`, per
  [@amakrishnamundru](https://github.com/ramakrishnamundru/gitbook-plugin-edit-link/commit/46c29089afc70db65aba6c07c7302a1c341f3560).
- Added option to specify the `aria` label.
- Added option to specify the `position` in the toolbar.
- Updated `README.md`:
  - Removed deprecated "Known Issue" and "How this work?" sections.
  - Fixed grammar.
  - Added "Configuration Overview".

**1.3 - 28 April 2015**

- Gitbook 2.0.1 compatibility added by [@todvora](https://github.com/rtCamp/gitbook-plugin-edit-link/pull/4). Please see known-issues for more details.

**1.2 - 03 April 2015**

- Multiligual gitbook support added by [@aniav](https://github.com/aniav) ([#2](https://github.com/rtCamp/gitbook-plugin-edit-link/pull/2))

**1.1.3 - 11 Jan 2015**

- Initial release
