<script setup>
import { onMounted } from 'vue';
import { useData } from 'vitepress';

onMounted(async () => {
  if (!import.meta.env.SSR) {
    await import("./header.js")
  }
});

const {theme} = useData();
</script>

<style>
@import url('./header.css');
.VPNav {
  pointer-events: all !important;
}
</style>

<template>
  <!-- Header -->
  <div id="desp-header-container">
    <div id="desp-header-inner-container">

      <!-- Left container -->
      <div id="left-container">
        <a href="https://<WEB_PORTAL_URL>">
          <img id="eu-flag-de" alt="destine platform home" src="/assets/destine/destination_earth_logo.svg">
        </a>
        <a href="#">
          <img id="service-logo" alt="service-home" :src="theme.logo">
        </a>
      </div>

      <!-- Central container -->
      <div id="central-container">
        <a
          v-for="nav in theme.nav"
          class="header-link"
          :href="nav.link"
        >
          {{ nav.text }}
        </a>
      </div>

      <!-- Right container -->
      <div id="right-container">
        <div id="info-container">
          <div id="info-button">
            <i data-feather="info" id="info-icon"></i>
          </div>

          <!-- Info Menu -->
          <div id="info-frame">
            <a class="frame-link" href="https://gtif-cerulean.github.io/deside-page/">About DESIDE</a>
            <a class="frame-link" href="https://eodash.github.io/eodash/">eodash Documentation</a>
          </div>

        </div>
        <div id="user-container">
          <div id="login-div">
            <a class="login-a not-logged" href="https://workspace.deside.hub-otc.eox.at/">
                <!-- <i data-feather="log-in" class="login-icon not-logged"></i> -->
                <p class="login-text not-logged">Request User Workspace</p>
            </a>
            <!-- <a class="login-a logged">
                <i data-feather="user" class="login-icon logged"></i>
                <p class="login-text logged">[LOGGED_USER_NAME]</p>
            </a> -->
          </div>

          <!-- User Menu -->
          <!-- <div id="user-frame" class="logged">
            <a class="frame-link" href="https://<IAM_URL>/realms/desp/account/">Account Settings</a>
            <a class="frame-link" href="#">Logout</a>
          </div> -->

        </div>

        <!-- Mobile menu icon -->
        <div id="menu-icon-container">
          <i data-feather="menu" id="menu-icon"></i>
        </div>
      </div>
    </div>
  </div>

  <!-- Mobile Menu Container -->
  <div id="dropdown-menu-container">
    <div
      v-for="nav in theme.nav"
      class="dropdown-link"
    >
      <a :href="nav.link">{{ nav.text }}</a>
    </div>
  </div>
</template>