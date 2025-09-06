<!-- Project Shields -->

[![Issues](https://img.shields.io/github/issues/bcgov/nr-theme)](/../../issues)
[![Pull Requests](https://img.shields.io/github/issues-pr/bcgov/nr-theme)](/../../pulls)
[![MIT License](https://img.shields.io/github/license/bcgov/nr-theme.svg)](/LICENSE)
[![Lifecycle](https://img.shields.io/badge/Lifecycle-Experimental-339999)](https://github.com/bcgov/repomountie/blob/master/doc/lifecycle-badges.md)

# **NR-Theme**

## Description

This is a common repository for maintaining the FDS (Forest Digital Service) design system code. The design system is built on top of the [Carbon Design System](https://carbondesignsystem.com) within Figma. Feel free to check our [Figma FDS Design System](<(https://www.figma.com/file/KDXuYanyOsBCM5vpPmNvGf/FSA-Design-System?node-id=58-2763&t=Xj2VFLJE3BlUdkds-0)>).

This repository provides the custom design tokens and custom stylesheets for [Carbon UI libary](https://carbondesignsystem.com/developing/frameworks/react/) and [Primevue UI library](https://primevue.org/installation/) to support the FDS Design System. A shared landing page styling can be found [here](/style-sheets/landing-page-components-overrides.scss).

## Installation and Usage

### Prerequisite

Your project needs to have Sass configured to load `.scss` files

### Usage (React + Carbon, 2025)
Please check the sample `main.tsx` file for a React application:
- In your project, create a new folder called `styles` under `src`
- Copy the `assets/font` folder to the `styles` folder
- Copy the `design-tokens` folder to the `styles` folder
- Copy the `style-sheets/overrides.scss` folder to the `styles` folder
- Import the `overrides.scss` file into your `main.tsx`
- Config the theme in `main.tsx` and use "SideNav" and "Content" component to apply the layout
```
import { StrictMode, useState } from "react";
import { createRoot } from "react-dom/client";
import App from "./App.tsx";
import "@carbon/styles/css/styles.css";
import "./styles/overrides.scss";

import { Theme } from "@carbon/react";
import {
  Header,
  HeaderName,
  SideNav,
  SideNavItems,
  SideNavLink,
  Content,
  Toggle,
} from "@carbon/react";
import { Home, Information } from "@carbon/icons-react";

const RootComponent = () => {
  const [theme, setTheme] = useState<"g10" | "g100">("g10");

  const handleToggle = (checked: boolean) => {
    setTheme(checked ? "g100" : "g10");
  };

  return (
    <StrictMode>
      <Theme theme={theme}>
        <Header aria-label="Carbon UI Shell Example">
          <HeaderName href="#" prefix="IBM">
            MyApp
          </HeaderName>

          <div style={{ marginLeft: "auto", marginRight: "1rem" }}>
            <Toggle
              id="theme-toggle"
              labelA="Light"
              labelB="Dark"
              toggled={theme === "g100"}
              onToggle={handleToggle}
            />
          </div>
        </Header>

        <SideNav isFixedNav expanded isChildOfHeader={false}>
          <SideNavItems>
            <SideNavLink href="#" renderIcon={Home}>
              Home
            </SideNavLink>

            <SideNavLink href="/about" renderIcon={Information} isActive>
              About
            </SideNavLink>
          </SideNavItems>
        </SideNav>

        <Content>
          <App />
        </Content>
      </Theme>
    </StrictMode>
  );
};

createRoot(document.getElementById("root")!).render(<RootComponent />);

```

### Use npm package (deprecated)

-   NPM
    -   use `npm i @bcgov-nr/nr-theme`
-   Yarn
    -   use `yarn add @bcgov-nr/nr-theme`

### Usage (React)

-   Create a `custom.scss` file in `./src`
-   Add `import './custom.scss';` to your `App.tsx` file
-   Configure your `custom.scss` file to your taste with this [example](/examples/React/example-custom.scss)
-   Add a global css prefix `bx` to your project
    -   in `./src/index.tsx`:
        -   `import { ClassPrefix } from '@carbon/react';`
    -   wrap your `<App />` with `ClassPrefix`:
        -   ```html
            <ClassPrefix prefix="bx">
                <App />
            </ClassPrefix>
            ```

### Usage (Vue3)

For vue3 application, due to the restriction of the [Carbon UI library](https://vue.carbondesignsystem.com/?path=/story/welcome--default), we will use [PrimeVue](https://primevue.org/) to integrate with this common theme repo.

**Configuration:**

-   Follow the [installation guide from PrimeVue official documentation](https://primevue.org/installation) to install PrimeVue

    ```
    npm install primevue primeicons
    ```

-   Add the following the main.ts file

    ```
    import { createApp } from 'vue';
    import PrimeVue from 'primevue/config';

    // use bootstrap4 as default style
    import 'primevue/resources/themes/bootstrap4-light-blue/theme.css';
    import 'primevue/resources/primevue.min.css';
    import 'primeicons/primeicons.css';

    // import the component override style sheet for primevue
    import '@bcgov-nr/nr-theme/style-sheets/primevue-components-overrides.scss';

    const app = createApp(App);
    app.use(PrimeVue);
    ```

    Install the SASS loader

    ```
    npm install -D sass-loader sass
    ```

### Usage (Application Landing Page)

The landing page stylesheet can apply to all applications regardless the UI libraries. Apply the custom class name to your landing page elements, and import the landing page stylesheet.

```
@import '@bcgov-nr/nr-theme/style-sheets/landing-page-components-overrides.scss';
```

![landing page image](./assets/images/landing-page-styling.jpg)
