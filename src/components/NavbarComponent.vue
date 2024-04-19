<template>
  <nav :class="[`navbar-${theme} bg-${theme} navbar navbar-expand-lg`]">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Navbar</a>
      <button
        class="navbar-toggler"
        type="button"
        data-bs-toggle="collapse"
        data-bs-target="#navbarNav"
        aria-controls="navbarNav"
        aria-expanded="false"
        aria-label="Toggle navigation"
      >
        <span class="navbar-toggler-icon"></span>
      </button>
      <div
        class="collapse navbar-collapse"
        style="justify-content: space-between"
        id="navbarNav"
      >
        <ul class="navbar-nav">
          <li v-for="(page, id) in pages" class="nav-item" :key="id">
            <navbar-link
              :page="page"
              :isActive="activePage === id"
              @click.prevent="navLinkClick(id)"
            ></navbar-link>
          </li>
        </ul>
        <form class="d-flex">
          <button @click.prevent="changeTheme" class="btn btn-primary">
            {{ theme }} Mode
          </button>
        </form>
      </div>
    </div>
  </nav>
</template>

<script>
import NavbarLink from "./NavbarLink.vue";
export default {
  components: { NavbarLink },
  props: ["pages", "activePage", "navLinkClick"],
  data() {
    return {
      useDarkNavbar: true,
      theme: "dark",
    };
  },
  methods: {
    changeTheme() {
      this.theme = this.theme === "dark" ? "light" : "dark";
    },
  },
  computed: {
    navbarClasses() {
      return {
        "navbar-dark  bg-dark": this.useDarkNavbar,
        "navbar-light bg-light": !this.useDarkNavbar,
      };
    },
  },
};
</script>
