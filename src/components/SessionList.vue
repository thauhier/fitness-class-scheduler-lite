<template>
  <div class="sessions-list">
    <h3>Sessions</h3>
    <div v-if="sessions.length === 0" class="no-sessions">
       No sessions yet — add your first one above!
    </div>
    <ul v-else>
      <SessionItem
        v-for="(s, index) in sessions"
        :key="index"
        :session="s"
        @delete="deleteSession(index)"
      />
    </ul>
  </div>
</template>

<script>
import SessionItem from "./SessionItem.vue";

export default {
  name: "SessionList",
  props: {
    sessions: { type: Array, required: true },
  },
  components: { 
    SessionItem 
},
  methods: {
    deleteSession(index) {
      this.$emit("delete-session", index);
    },
  },
};
</script>

<style scoped>
.sessions-list {
  max-width: 500px;
  margin: 2rem auto;
  padding: 1rem;
}

h3 {
  margin-bottom: 1rem;
  color: #333;
}

.no-sessions {
  font-style: italic;
  color: #666;
  padding: 0.8rem;
  background: #f0f0f0;
  border-radius: 6px;
  text-align: center;
}
ul {
  list-style: none;
  padding: 0;
}
</style>