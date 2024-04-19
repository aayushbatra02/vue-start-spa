<template>
  <div>
    <navbar-component
      :active-page="activePage"
      :pages="pages"
      :nav-link-click="(id) => (activePage = id)"
    ></navbar-component>
    <page-viewer :page="pages[activePage]"></page-viewer>
  </div>
</template>

<script>
import NavbarComponent from "./components/NavbarComponent.vue";
import PageViewer from "./components/PageViewer.vue";

export default {
  components: {
    NavbarComponent,
    PageViewer,
  },
  data() {
    return {
      activePage: 0,
      pages: [
        {
          link: {
            text: "Home",
            url: "index.html",
          },
          pageTitle: "Home Page",
          content: "This is Home content",
        },
        {
          link: {
            text: "About",
            url: "about.html",
          },
          pageTitle: "About Page",
          content: "This is About content",
        },
        {
          link: {
            text: "Contact",
            url: "contact.html",
          },
          pageTitle: "Contact Page",
          content: "This is Contact content",
        },
      ],
    };
  },
};
</script>

<style>
</style>
