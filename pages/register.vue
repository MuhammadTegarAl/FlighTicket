<template>
  <section>
    <b-field label="Name">
      <b-input v-model="name"></b-input>
    </b-field>

    <b-field label="Email">
      <b-input type="email" value="" maxlength="30"> </b-input>
    </b-field>

    <b-field label="Username">
      <b-input value="" maxlength="30"></b-input>
    </b-field>

    <b-field label="Password">
      <b-input type="password" value="" password-reveal> </b-input>
    </b-field>

    <b-button type="is-primary">Register</b-button>
  </section>
</template>
<script>
export default {
  data() {
    return {
      name: '',
    }
  },
}
</script>
