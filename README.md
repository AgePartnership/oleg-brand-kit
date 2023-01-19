# Oleg Brand Kit

This package contains Sass allowing for consistent distribution of Age Partnership branding, such as hex colour values.

This package is distributed through Yarn.

## Publishing Changes
We use [`npm version`](https://docs.npmjs.com/cli/v6/commands/npm-version) with some custom commit hooks in `package.json` to handle updating our package version, creating our Git release and tag, and pushing the changes to Github. There's no need to do a `git flow release`, to manually update the package version in package.json, or to manually merge your code into master and push your tags.

Here's the process for publishing your changes:
1. Merge your approved changes into develop and pull down develop locally.
2. Run `npm version [patch / minor / major]`, following normal [semantic versioning constraints](https://semver.org/).

## Install using npm

Before you can use npm, you need to [install Node](https://nodejs.org/en/download/).

Once you've done that, in the root of your project directory, run:

<pre>
    <code>
        npm install oleg-brand-kit
    </code>
</pre>

This will install the starter pack in the 'node_modules' directory located in the root of your project.

## Importing the Sass into your project

### Include the config variables!

If you want to include all the config variables from this repo, there's a handy single file you need to import into your main project Sass file:

`@import 'node_modules/oleg-brand-kit/config';`

### Include the utility classes!

If you want to include the utility classes from this repo, you can import the following into your main project Sass file:

`@import 'node_modules/oleg-brand-kit/utilities';`

This file contains classes which you can use to amend properties of an element, including font-weight, font-size and colour.

This file must be the last imported partial in your Sass file. Generally, classes added here hold the same CSS specificity value as classes used in module/component partials. In such cases, CSS will read the most 'recent' declaration. By importing the utilities partial after every other import, it ensures the utility classes work as intended.

For more information regarding CSS specificity, see: https://css-tricks.com/specifics-on-css-specificity/.

### Pick 'n' Mix

You can include files individually allowing you to customise what is available to your project. For example, to include just the colour variables, you would drop the following into your main project Sass file:

`@import 'node_modules/oleg-brand-kit/config.colour';`

## Stylelint - linting your code

Whenever you make a change to a .scss file you should run the scss linter to check it follows our standards and conventions. The scripts are listed in `package.json` under scripts.

To run stylelint itself (this will just show you any errors) run the following command:

`npm run stylelint`

To run stylelint and then get it to fix the errors:

`npm run stylelint-fix`


That's pretty much it. Now, go make a brew.

## Using Icons

A list of all icons can be found in `rebuild/icons/_icons.scss`.

*Note:* Image assets for icons are stored here: `rebuild/assets/images/icons`. The `icons` folder should be copied from this location into your project's public image directory where you can then access the asset files and use in your project as you would normally. Ideally this should be setup as a Gulp task.

If including icons via CSS, ensure the `$image-dir` is pointing to your project's public image directory.

### Including Icons
Icons can be included in a variety of methods;

* Asset File - `<img>`
* CSS - E.g. Pseudo elements
* HTML - Class on HTML elements

#### Asset File Method

SVGs assets can be used as normal. For example:

```
<img src="your_public_directory_path/assets/images/icons/hamburger--primary.svg" width="20" height="14" alt="Icon" />
```


#### CSS Method

In your CSS you can include icon styles through the use of `@extend`. 

Example in a class:

```
.example__icon {
    @extend .ap-icon;
    @extend .ap-icon--hamburger--primary;
    @extend .ap-icon--small;
}
```

Example in a pseudo class:

```
.example__icon {
    position:relative;

    &::before {
        @extend .ap-icon;
        @extend .ap-icon--hamburger--primary;
        @extend .ap-icon--small;
        content: '';
        display: block;
        left: 0;
        position: absolute;
    }
}
```

### Masking icons

If required, you can include `@extend .ap-icon--mask;` to return the icon as an image mask, allowing you to change the icon colour. This will only work on simple line style icons.

You must then specify a `background-color` within your CSS.

Example:

```
.example__icon {
    position:relative;

    &::before {
        @extend .ap-icon;
        @extend .ap-icon--hamburger--primary;
        @extend .ap-icon--small;
        @extend .ap-icon--mask;
        background-color: red;
        content: '';
        display: block;
        left: 0;
        position: absolute;
    }
}
```


#### HTML Method
Use icons in your components by including their class names e.g. `ap-icon--hamburger--primary`.

Example:

`<div class="ap-icon ap-icon--hamburger--primary ap-icon--small"></div>`

### Masking icons

If required, you can include `ap-icon--mask` to return the icon as an image mask, allowing you to change the icon colour. This will only work on simple line style icons.

You must then specify a `background-color` within your component.

Example:

`<div class="ap-icon ap-icon--hamburger--primary ap-icon--small ap-icon--mask example__icon"></div>`

Then in CSS, somthing similar to:

```
.example__icon {
    background-color: red;
}
```

### Icon sizes
By default the height and width are not provided, you must set this manually in your `<img>` tag or with an icon size helper class.

Sizes available to use:

* 'tiny': `16px`
* 'small': `24px`
* 'medium': `32px`
* 'ui': `40px`
* 'large': `88px`
* 'maxi': `152px`

Include these in your icon as `ap-icon--[size]`, e.g. `ap-icon--small`

#### CSS

```
.example__icon {
    @extend .ap-icon;
    @extend .ap-icon--hamburger--primary;
    @extend .ap-icon--small;
}
```

#### HTML

`<div class="ap-icon ap-icon--hamburger--primary ap-icon--small"></div>`