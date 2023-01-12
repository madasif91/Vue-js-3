<script>

export default{
  data(){
    return{
      listsuhu: [],
    }
  },
  methods:{
    async ambildata() {
    // Simple GET request using fetch
    const response = await fetch("http://127.0.0.5:80/getlist");
    const data = await response.json();
    this.listsuhu = data.sensor_suhu;
    },
  },
};

</script>

<template>
  <table class="p-10">
    <tr>
      <td>Waktu</td>
      <td>Suhu</td>
    </tr>
    <tr v-for="item in listsuhu">
      <td>{{ item.waktu}}</td>
      <td>{{ item.suhu}}</td>
    </tr>
  </table>
  <div>
    <button class="rounded-3xl p-5 bg-orange-200 text-white" @click="ambildata()">Ambil Data</button>
    <button class="rounded-3xl p-5 bg-orange-800 text-white" @click="ambildata()">Ambil Data</button>
  </div>

</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
