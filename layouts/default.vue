<template>
  <div>
    <nav
      class="navbar header has-shadow is-primary"
      role="navigation"
      aria-label="main navigation"
    >
      <template>
        <div class="navbar-brand">
          <a class="navbar-item" href="/">
            <b>FlighTicket</b>
          </a>
        </div>
      </template>
      <template>
        <b-navbar-item tag="div">
          <div class="buttons">
            <a class="button is-light" href="login"> Log in </a>
          </div>
        </b-navbar-item>
      </template>
    </nav>

    <section class="main-content columns">
      <aside class="column is-2 section">
        <p class="menu-label is-hidden-touch">General</p>
        <ul class="menu-list">
          <li v-for="(item, key) of items" :key="key">
            <nuxt-link :to="item.to" exact-active-class="is-active">
              <b-icon :icon="item.icon" /> {{ item.title }}
            </nuxt-link>
          </li>
        </ul>
      </aside>

      <div class="container column is-10">
        <nuxt />
      </div>
    </section>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        {
          title: 'Home',
          icon: 'airplane',
          to: { name: 'index' },
        },
        {
          title: 'Your Ticket',
          icon: 'ticket-confirmation',
          to: { name: 'your-ticket/1' },
        },
      ],
    }
  },
}
</script>
