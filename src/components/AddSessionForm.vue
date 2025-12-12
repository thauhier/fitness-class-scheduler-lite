<template>
  <div class="add-session-form">
    <h2>Add New Session</h2>
    <form @submit.prevent="submitForm">
      <div class="form-group">
        <label>Session Name</label>
        <input type="text" v-model="session.name" />
        <span v-if="errors.name" class="error">{{ errors.name }}</span>
      </div>

      <div class="form-group">
        <label>Coach</label>
        <input type="text" v-model="session.coach" />
        <span v-if="errors.coach" class="error">{{ errors.coach }}</span>
      </div>

      <div class="form-group">
        <label>Date</label>
        <input type="date" v-model="session.date" />
        <span v-if="errors.date" class="error">{{ errors.date }}</span>
      </div>

      <div class="form-group">
        <label>Time</label>
        <input type="time" v-model="session.time" />
        <span v-if="errors.time" class="error">{{ errors.time }}</span>
      </div>

      <div class="form-group">
        <label>Capacity</label>
        <input type="number" v-model.number="session.capacity" min="1" />
        <span v-if="errors.capacity" class="error">{{ errors.capacity }}</span>
      </div>

      <button type="submit">Add Session</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "AddSessionForm",
  data() {
    return {
      session: { name: "", coach: "", date: "", time: "", capacity: null },
      errors: {},
    };
  },
  methods: {
    validateForm() {
      this.errors = {};
      if (!this.session.name) this.errors.name = "Session name is required.";
      if (!this.session.coach) this.errors.coach = "Coach name is required.";
      if (!this.session.date) this.errors.date = "Date is required.";
      if (!this.session.time) this.errors.time = "Time is required.";
      if (!this.session.capacity || this.session.capacity < 1)
        this.errors.capacity = "Capacity must be at least 1.";
      return Object.keys(this.errors).length === 0;
    },
    submitForm() {
      if (this.validateForm()) {
        this.$emit("add-session", { ...this.session });
        this.session = { name: "", coach: "", date: "", time: "", capacity: null };
      }
    },
  },
};
</script>


<style scoped>
.add-session-form {
  max-width: 500px;
  margin: 1rem auto;
  padding: 1.5rem;
  border: 1px solid #ddd;
  border-radius: 8px;
  background: #fafafa;
}

h2 {
  margin-bottom: 1rem;
  color: #333;
}

.form-group {
  margin-bottom: 1rem;
}

label {
  display: block;
  margin-bottom: 0.3rem;
  font-weight: 600;
}

input {
  width: 100%;
  padding: 0.5rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}

button {
  background-color: #42b983;
  color: white;
  border: none;
  padding: 0.6rem 1rem;
  cursor: pointer;
  border-radius: 4px;
  font-weight: 600;
}

button:hover {
  background-color: #369870;
}

.error {
  color: #e74c3c;
  font-size: 0.85rem;
}
</style>
