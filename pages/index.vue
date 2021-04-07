<template>
  <div class="indexRoot">
    <div class="top">
      <div class="topWrap">
        <h1>{{ planets.data.header }}</h1>
        <small>{{ planets.data.podnadpis }}</small>
      </div>
    </div>
    <div class="container-fluid middle">
      <div class="row">
        <div class="col-md-5 offset-md-1">
          <ul>
            <li v-for="planet in planets.data.repeater" :key="planet.data">
              {{ planet.nazev }}
            </li>
          </ul>
        </div>
      </div>
    </div>

    <img
      :src="`http://localhost:8055/assets/${planets.data.fotka}?height=100&width=100`"
    />
    <button @click="$fetch">Refresh</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      planets: [],
    }
  },
  async fetch() {
    this.planets = await fetch(
      'http://localhost:8055/items/index'
    ).then((res) => res.json())
  },
}
</script>
<style lang="scss">
body {
  background-color: #484ba3;
  color: #fff;

  ul {
    list-style: none;
    padding: 0;
  }
}
</style>
