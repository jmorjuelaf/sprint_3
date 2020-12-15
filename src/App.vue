<template>
  <div id="app">
    <div class="header">
      <h1>PayDay</h1>
      <nav>
        <button v-on:click="init" v-if="is_auth">Inicio</button>
        <button v-on:click="getBalance" v-if="is_auth">Ingresos</button>
        <button v-if="is_auth">Egresos</button>
        <button v-if="is_auth">Ahorro</button>
      </nav>
    </div>

    <div class="main-component">
      <router-view> </router-view>
    </div>

    <div class="footer">
      <h2>2020</h2>
    </div>
  </div>
</template>
    <!-- Comentario de prueba Representa el js (Comportamiento) -->
<script>
export default {
  name: "App",
  components: {},
  data: function () {
    return {
      is_auth: localStorage.getItem("isAuth") || false,
    };
  },

  methods: {
    init: function () {
      if (this.$route.name != "user") {
        let username = localStorage.getItem("current_username");
        this.$router.push({ name: "user", params: { username: username } });
      }
    },

    getBalance: function () {
      if (this.$route.name != "user_balance") {
        let username = localStorage.getItem("current_username");
        this.$router.push({
          name: "user_balance",
          params: { username: username },
        });
      }
    },
  },

  beforeCreate: function () {
    localStorage.setItem("current_username", "1");
    localStorage.setItem("isAuth", true);
    this.$router.push({ name: "user" });
  },
};
</script>

    <!-- // Representa el css (estilo) -->
<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@700&display=swap");
body {
  margin: 0 0 0 0;
  font-family: roboto, sans-serif;
}

.header {
  margin: 0%;
  padding: 0;
  width: 100%;
  height: 10vh;
  min-height: 100px;
  background-color: #073331;
  color: #e5e7e9;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.header h1 {
  width: 20%;
  text-align: center;
  font-family: Roboto, sans-serif;
}

.header nav {
  height: 100%;
  width: 45%;
  display: flex;
  justify-content: space-around;
  align-items: center;
  font-size: 20px;
  font-family: roboto, sans-serif;
}
button {
  font-family: roboto, sans-serif;
}

.header nav button {
  color: #e5e7e9;
  background: #073331;
  border: 1px solid #e5e7e9;
  border-radius: 5px;
  padding: 10px 20px;
}

.header nav button:hover {
  color: #073331;
  background: #e5e7e9;
  border: 1px solid #e5e7e9;
}

.main-component {
  height: 75vh;
  margin: 0%;
  padding: 0%;
  background: #fdfefe;
}

.footer {
  margin: 0;
  padding: 0;
  width: 100%;
  height: 10vh;
  background-color: #073331;
  color: #e5e7e9;
}

.footer h2 {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>