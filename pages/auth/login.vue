<script>
import {mapActions, mapState} from 'vuex'
import CardTitle from '@/components/Base/Card/CardTitle'

export default {
  components: {
    CardTitle
  },
  head: {
    bodyAttrs: {// class: 'no-context-menu'
    }
  },
  computed: {
    ...mapState('auth', ['user', 'isAuthenticatePending'])
  },
  methods: {
    ...mapActions('auth', ['authenticate']),
    ...mapActions('users', ['create']),

    async login() {
      const credentials = {
        email: this.email,
        password: this.password
      }
       // go the main dashboard
      this.$router.push('/admin')
    },
  },

  watch: {
    user() {
// alert(this.previousRoute)
      if (this.user) this.$router.back()
    }
  },

  data() {
    return {
      email: 'admin@domain.com',
      password: 'admin'
    }
  }

}

</script>
<template>
  <div class="d-flex justify-content-center h-100">
    <b-card no-body>
      <b-card-header class="d-flex">
        <card-title title="Sign In"
                    subTitle="Real login">

          <span class="ml-1"><i class="fab fa-facebook-square"/></span>
          <span class="ml-1"><i class="fab fa-google-plus-square"/></span>
          <span class="ml-1"><i class="fab fa-twitter-square"/></span>

        </card-title>
      </b-card-header>
      <b-card-body class="p-4 m-4">
        <form>
          <div class="input-group form-group">
            <div class="input-group-prepend">
              <span class="input-group-text  bg-primary inverse"><i class="la la-user"/></span>
            </div>
            <input type="text"
                   class="form-control"
                   v-model="email"
                   placeholder="username">

            </input>
          </div>
          <div class="input-group form-group">
            <div class="input-group-prepend">
              <span class="input-group-text  bg-primary inverse"><i class="la la-key"/></span>
            </div>
            <input type="password"
                   class="form-control"
                   v-model="password"
                   placeholder="password">
            </input>
          </div>
          <div class="row align-items-center remember">
            <b-form-checkbox class>
              Remember me
            </b-form-checkbox>
          </div>
          <div class="form-group">
            <input type="submit"
                   @click.prevent="login"
                   value="Login"
                   class="btn  float-right login_btn btn-primary inverse">
            </input></div>
        </form>
      </b-card-body>
      <b-card-footer>
        <div class="text-theme1 d-flex justify-content-center links">
          Don't have an account? <a href="#"
                                    class="font-weight-bold">Sign Up</a>
        </div>
        <div class="text-theme1 d-flex justify-content-center">
          <a href="#">Forgot your password?</a>
        </div>
      </b-card-footer>
    </b-card>
  </div>
</template>


<style lang="scss">
html {
  height: 100%;
}

body.bg-image1 > div,
body.bg-image1 > div > div {
  height: 100%;
}

</style>

<style lang="scss" scoped>
.input-group-text i {
  font-size: 16px;
}

::v-deep .ig-page-wrapper {
  height: 100%;
}

.container {
  height: 100%;
  align-content: center;
}

.card {
  height: 400px;
  margin-top: 10%;
  width: 430px;
}

.card-footer {
  font-size: 0.75rem;
}

.social_icon span {
  font-size: 40px;
  margin-left: 10px;
}

.social_icon span:hover {
  cursor: pointer;
}

.card-header h3 {
  color: rgb(40, 40, 40);
}

.input-group-prepend span {
  width: 40px;
  color: rgb(255, 255, 255);
  border: 0 !important;
}

input:focus {
  outline: 0 0 0 0 !important;
  box-shadow: 0 0 0 0 !important;
}

.remember {
  color: rgb(43, 43, 43);
}

.remember input {
  width: 20px;
  height: 20px;
  margin-left: 15px;
  margin-right: 5px;
}

.login_btn {
  color: #ffffff;
  width: 100px;
}

.links {
  color: rgb(0, 0, 0);
}

.links a {
  margin-left: 4px;
}

.right-bar i {
  color: var(--theme1-mixed-1);
  font-size: 30px;
}

</style>
