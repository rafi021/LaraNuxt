<template>
<div class="container">
    <div class="row">
        <div class="col-md-6 offset-3">
            <div class="card">
                <div class="card-header">
                    Login Page
                </div>
                <div class="card-body">
                    <form @submit.prevent="userLogin">
                        <div class="form-group mb-3">
                            <label for="">User Email</label>
                            <input type="email" class="form-control" v-model="login.email" />
                        </div>
                        <div class="form-group mb-3">
                            <label>Password</label>
                            <input type="password" class="form-control" v-model="login.password" />
                        </div>
                        <div class="form-group">
                            <button type="submit" class="btn btn-primary">Submit</button>
                        </div>
                    </form>
                </div>
            </div>
        </div>
    </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      login: {
        email: 'admin@gmail.com',
        password: '12345678'
      }
    }
  },
  methods: {
    async userLogin() {
      try {
        let response = await this.$auth.loginWith('local', { data: this.login })
        console.log(response)
      } catch (err) {
        console.log(err)
      }
    }
  }
}
</script>