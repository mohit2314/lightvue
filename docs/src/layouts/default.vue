<template>
  <div id="app">
    <app-header @toggle-drawer="toggleDrawer()" />
    <div class="sidemenu__backdrop" v-if="showDrawer" @click="toggleDrawer()"></div>
    <app-navigation-drawer :show-drawer="showDrawer" @toggle-drawer="toggleDrawer()" />
    <div class="page-wrap">
      <div class="page-content">
        <nuxt-child />
      </div>
      <app-footer />
    </div>
    <LvToast position="top" />
    <LvToast position="center" />
    <LvToast position="bottom" />
    <LvNotification />
    <LvNotification position="top-left" />
    <LvNotification position="bottom-left" />
    <LvNotification position="bottom-right" />
  </div>
</template>

<script>
import 'light-icons/dist/light-icon.css';
import AppHeader from '@/components/AppHeader.vue';
import AppNavigationDrawer from '@/components/AppNavigationDrawer.vue';
import AppFooter from '@/components/AppFooter.vue';

export default {
  scrollToTop: true,
  components: {
    AppHeader,
    AppNavigationDrawer,
    AppFooter,
  },
  data() {
    return {
      showDrawer: false,
    };
  },
  methods: {
    toggleDrawer() {
      this.showDrawer = !this.showDrawer;
    },
  },
};
</script>

<style lang="scss">
@import './overwrite.scss';
@import './examples.scss';
* {
  padding: 0px;
  margin: 0px;
  box-sizing: border-box;
  -webkit-tap-highlight-color: rgba(255, 255, 255, 0);
}

a {
  text-decoration: none;
}

body,
#app {
  background-color: #f5f8fa;
  color: #566d79;
  font-family: Roboto, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

/* Media Queries */
@media only screen and (max-width: 600px) {
  .bg-gray div {
    padding: 0.5rem 1rem;
    border-radius: 4px;
  }
}
.page-wrap {
  position: absolute;
  right: 0px;
  top: 60px;
  width: calc(100% - 250px);
  .page-content {
    padding: 30px 30px 0px;
  }
}

.feature-intro p {
  opacity: 0.8;
  line-height: 20px;
  margin: 8px 0px;
}
.sidemenu__backdrop {
  z-index: 998;
  background-color: rgba(28, 39, 45, 0.55);
  height: 100vh;
  width: 100vw;
  position: fixed;
  top: 0px;
  left: 0px;
  display: none;
  opacity: 0;
  transition: all 0.2s ease-in-out;
}

@media (max-width: 769px) {
  .page-wrap {
    left: 0px;
    width: 100%;
  }
  .sidemenu__backdrop {
    opacity: 1;
    display: initial;
  }
}
</style>
