<template>
  <nav id="nav">
    <router-link to="/">
      <p class="logo">The Vue Travel App</p>
    </router-link>
    <ul class="nav-links">
      <li class="links">
        <router-link to="/">
          Home
        </router-link>
      </li>
      <li
        v-for="destination in destinations"
        :key="destination.name"
        class="links">
        <router-link :to="{
            name: 'DestinationDetails',
            params: { slug: destination.slug },
          }">
           {{ destination.name  }}
        </router-link>
      </li>
    </ul>
  </nav>
</template>

<script>
import store from "@/store";
export default {
  data() {
    return {
      destinations: store.destinations
    };
  }
};
</script>

<style scoped>
#nav {
  display: flex;
  justify-content: flex-start;
  position: sticky;
  top: 0;
  background-color: #fff;
  border-bottom: 1px solid gray;
  z-index: 1;
}

#nav a {
  color: #2c3e50;
  text-decoration: none;
  font-weight: bold;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

.nav-links {
  display: flex;
  align-content: center;
}

.links {
  padding-right: 20px;
  list-style: none;
  display: flex;
  align-content: center;
  margin: auto;
}

.links:hover {
  text-decoration: underline;
}

.logo {
  font-size: 20px;
  color: #42b983;
  font-weight: bold;
}
</style>
