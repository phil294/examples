<template>
  <div id="app">
    <NoSSR> <vue-progress-bar /> </NoSSR>
    <MainMenu />
    <router-view v-if="!$errorHandler.error" />
    <ErrorPage v-else />

    <div id="update-popup" style="display: none;">
      <p>There is an update ready !</p>
      <button class="btn" @click="refresh">Refresh</button>
    </div>
  </div>
</template>

<script>
import NoSSR from 'vue-no-ssr';
import MainMenu from './components/MainMenu.vue';
import ErrorPage from './components/ErrorPage.vue';

export default {
  components: {
    NoSSR,
    MainMenu,
    ErrorPage,
  },

  head: {
    titleTemplate(title) {
      return title ? `${title} | UVue` : 'UVue';
    },
    htmlAttrs: {
      lang: 'en',
    },
    link: [{ rel: 'manifest', href: '/manifest.json' }],
    meta: [
      { charset: 'utf-8' },
      { name: 'viewport', content: 'width=device-width, initial-scale=1' },
      { name: 'description', content: 'UVue examples website!' },
      { name: 'theme-color', content: '#ffffff' },
    ],
  },

  methods: {
    refresh() {
      window.location.reload(true);
    },
  },
};
</script>

<style lang="stylus">
html {
  font-size: 62.5%;
}

body {
  margin: 0;
  background: #fcfcfc;

  font-size: 1.6rem;
  font-family: 'Nunito', sans-serif;

  color: #666;
}

button,
input {
  font-family: 'Nunito', sans-serif;
  font-size: 1.7rem;
}

* {
  box-sizing: border-box;
}

h1 {
  font-size: 4.8rem;
  font-weight: 300;
  margin: 0;
}

h2 {
  font-size: 2.4rem;
  font-weight: 300;
  margin: 0;
}

.btn {
  display: inline-block;
  text-decoration: none;

  background: #38465e;
  color: #fff;
  padding: 1rem 2rem;
  margin: 1rem;
  border-radius: 0.7rem;

  border: 0;
  cursor: pointer;
  border-bottom: 0.3rem solid darken(#38465e, 10%);

  transition: background-color 0.2s ease-in-out;
  transition-property: background-color, border-color;

  &:hover,
  &:focus,
  &:active {
    outline: none;
    background: darken(#00ab6c, 5%);
    border-bottom-color: darken(#00ab6c, 15%);
  }
}

.notif {
  padding: 2rem 2rem;
  margin-bottom: 1rem;
  background: lighten(#38465e, 60%);
  border-radius: 2rem;

  &.error {
    background: lighten(#c4382c, 40%);
  }
}

#update-popup {
  position: fixed;
  z-index: 10000;
  right: 3rem;
  bottom: 3rem;
  padding: 2rem 6rem;
  text-align: center;
  background: #fff;
  box-shadow: 0 0 1rem rgba(0, 0, 0, 0.15);

  p {
    margin-bottom: 0;
  }
}
</style>
