<template>
  <div class="wrapper">
    <side-bar>
      <template slot="links">
        <sidebar-link to="/dashboard" name="Dashboard" icon="ti-panel"/>
        <!-- <sidebar-link to="/profile" name="User Profile" icon="ti-user"/> -->
        <sidebar-link to="/history" name="Submission History" icon="ti-view-list-alt"/>
        <!-- <sidebar-link to="/submission/1" name="Submission Detail" icon="ti-info-alt"/> -->
        <sidebar-link to="/info" name="Info Page" icon="ti-help-alt"/>
        <sidebar-link to="/logout" name="Log Out" icon="ti-arrow-left"/>
      </template>
    </side-bar>
    <div class="main-panel">
      <top-navbar></top-navbar>

      <dashboard-content @click.native="toggleSidebar">

      </dashboard-content>

      <content-footer></content-footer>
    </div>
  </div>
</template>

<style lang="scss">
</style>

<script>
import TopNavbar from "./TopNavbar.vue";
import ContentFooter from "./ContentFooter.vue";
import DashboardContent from "./Content.vue";
import MobileMenu from "./MobileMenu";

export default {
  components: {
    TopNavbar,
    ContentFooter,
    DashboardContent,
    MobileMenu
  },

  methods: {
    toggleSidebar() {
      if (this.$sidebar.showSidebar) {
        this.$sidebar.displaySidebar(false);
      }
    }
  },

  beforeCreate: function () {
    if (!this.$session.exists()) {
      this.$router.push('/auth/login');
    }
  }

};
</script>
