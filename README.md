# Oleg Brand Kit

This package contains Sass allowing for consistent distribution of Age Partnership branding, such as hex colour values.

This package is distributed through Yarn.

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

This file must be the last imported partial in your Sass file. Generally, classes added here hold the same CSS specificity value as classes used in module/component partials. In such cases, CSS will read the most 'recent' declaration. By importing the utilities partial after every other import, it ensures the utility classes are set as intended.

For more information regarding CSS specificity, see: https://css-tricks.com/specifics-on-css-specificity/.

### Pick 'n' Mix

You can include files individually allowing you to customise what is available to your project. For example, to include just the colour variables, you would drop the following into your main project Sass file:

`@import 'node_modules/oleg-brand-kit/config.colour';`

That's pretty much it. Now, go make a brew.
