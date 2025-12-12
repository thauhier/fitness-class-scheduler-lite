<template>
  <div id="app">
    <AddSessionForm @add-session="addSession" />
    <SessionList :sessions="sessions" @delete-session="deleteSession" />
  </div>
</template>

<script>
import AddSessionForm from "./components/AddSessionForm.vue";
import SessionList from "./components/SessionList.vue";

export default {
  name: "App",
  components: { 
    AddSessionForm, 
    SessionList },
  data() {
    return { sessions: [] };
  },
  methods: {
    addSession(session) {
      this.sessions.push(session);
    },
    deleteSession(index) {
      this.sessions.splice(index, 1);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
