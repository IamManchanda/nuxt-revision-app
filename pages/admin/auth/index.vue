<template>
  <div class="box">
    <b-tabs v-model="auth_tab_type">
      <b-tab-item :label="login_label">
        <app-admin-auth :label="login_label" :user_log_details="user_log_details" />
      </b-tab-item>
      <b-tab-item :label="signup_label">
        <app-admin-auth :label="signup_label" :user_log_details="user_log_details" />
      </b-tab-item>
    </b-tabs>
  </div>
</template>

<script>
import user_log_details from "~/fixtures/user_log_details";
import AppAdminAuth from "~/components/app-admin-auth";

export default {
  layout: "auth",
  components: { AppAdminAuth },
  data() {
    return {
      user_log_details,
      auth_tab_type: 0,
      login_label: "Log in",
      signup_label: "Sign up",
    };
  },
  computed: {
    auth_seo_title() {
      if (this.auth_tab_type === 0) {
        return `${this.login_label} to your Account`;
      }
      if (this.auth_tab_type === 1) {
        return `${this.signup_label} to your Account`;
      }
      return "Your Account";
    }
  },
  head() {
    return {
      title: this.auth_seo_title
    };
  }
};
</script>
