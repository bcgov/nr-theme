<!-- Project Shields -->

[![Issues](https://img.shields.io/github/issues/bcgov/nr-fsa-theme)](/../../issues)
[![Pull Requests](https://img.shields.io/github/issues-pr/bcgov/nr-fsa-theme)](/../../pulls)
[![MIT License](https://img.shields.io/github/license/bcgov/nr-fsa-theme.svg)](/LICENSE)
[![Lifecycle](https://img.shields.io/badge/Lifecycle-Experimental-339999)](https://github.com/bcgov/repomountie/blob/master/doc/lifecycle-badges.md)

# **NR-FSA-Theme**

## Description
This is a common repo for maintaining the FSA design system code. The design system is built on top of the [Carbon Design System](https://carbondesignsystem.com). Link to [Figma FSA Design System](https://www.figma.com/file/KDXuYanyOsBCM5vpPmNvGf/FSA-Design-System?node-id=58-2763&t=Xj2VFLJE3BlUdkds-0)

Landing page styling can be found in [Landing Page](/style-sheets/landing-page-components-overrides.scss)

## Installation and Usage

### Prerequisite
Your project need to have Sass configured to load `.scss` files

### Installation
- NPM
    - use `npm i @bcgov-nr/nr-fsa-theme`
- Yarn
    - use `yarn add @bcgov-nr/nr-fsa-theme`

### Usage (React)
- Create a `custom.scss` file in `./src`
- Add `import './custom.scss';` to your `App.tsx` file
- Configure your `custom.scss` file to your taste with this [example](/examples/React/example-custom.scss)
- Add a global css prefix `bx` to your project
    - in `./src/index.tsx`:
        - `import { ClassPrefix } from '@carbon/react';`
    - wrap your `<App />` with `ClassPrefix`:
        - ```html
          <ClassPrefix prefix="bx">
            <App />
          </ClassPrefix>
          ```
