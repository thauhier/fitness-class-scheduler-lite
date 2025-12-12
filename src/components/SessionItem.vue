<template>
  <li class="session-item">
    <strong>{{ session.name }}</strong> with {{ session.coach }}
    on {{ session.date }} at {{ session.time }}
    (Capacity: {{ session.capacity }})
    <button @click="$emit('delete')">Delete</button>
  </li>
</template>

<script>
export default {
  name: "SessionItem",
  props: {
    session: { type: Object, 
        required: true },
  },
};
</script>

<style scoped>
.session-item {
  margin-bottom: 0.8rem;
  background: #f9f9f9;
  padding: 0.8rem;
  border-radius: 6px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.session-item strong {
  color: #333;
}

button {
  background-color: #e74c3c;
  color: white;
  border: none;
  padding: 0.4rem 0.8rem;
  border-radius: 4px;
  cursor: pointer;
  font-size: 0.85rem;
}

button:hover {
  background-color: #c0392b;
}
</style>