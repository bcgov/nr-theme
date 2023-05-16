# **Use FSA theme for VUE3 project**

For vue3 application, due to the restriction of the [Carbon UI library](https://vue.carbondesignsystem.com/?path=/story/welcome--default), we will use [PrimeVue](https://primevue.org/) to integrate with this common theme repo.

### **Configuration:**

-   Install the FSA common theme package
    ```
    npm install @bcgov-nr/nr-fsa-theme
    ```
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
    import '@bcgov-nr/nr-fsa-theme/style-sheets/primevue-components-overrides.scss';

    const app = createApp(App);
    app.use(PrimeVue);
    ```

    Install the SASS loader

    ```
    npm install -D sass-loader sass
    ```