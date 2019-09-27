<template>
  <div id="employee-form">
    <form @submit.prevent="handleSubmit">
      <label>Employee name</label>
      <input ref="first" v-model="employee.name" type="text" />
      <label>Employee Email</label>
      <input v-model="employee.email" type="text" />
      <button>Add Employee</button>
    </form>
  </div>
</template>

<script>
  export default {
    name: 'employee-form',
    data() {
      return {
        employee: {
          name: '',
          email: '',
        }
      }
    },
    methods: {
        handleSubmit() {
            console.log('Sending the data to parent');
            this.$emit('add:employee', this.employee);
            this.employee.name=""; this.employee.email="";
            this.$refs.first.focus();
        }
    }
  }
</script>

<style scoped>
  form {
    margin-bottom: 2rem;
  }
</style>