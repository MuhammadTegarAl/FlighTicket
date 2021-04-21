<template>
  <section>
    <h3 class="subtitle">Login</h3>
    <b-field>
      <b-input placeholder="Username" type="text" icon="account"> </b-input>
    </b-field>

    <b-field>
      <b-input placeholder="Email" v-model="email" type="email" icon="email">
      </b-input>
    </b-field>

    <b-button type="is-primary">Log-In</b-button>
    <p>Dont have Account Yet? <a href="/register">Register Here</a></p>
  </section>
</template>

<script>
export default {
  data() {
    return {
      email: '',
    }
  },
  methods: {},
}
</script>
