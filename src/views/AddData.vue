<template>
  <div id="add-user">
    <h1>Add Data</h1>
    <table class="table">
      <thead>
        <tr>
          <th>Name</th>
          <th>Surname</th>
          <th>Email</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="user in users" :key="user.id">
          <td>
            {{user.FirstName}}
          </td>
          <td>
            {{user.lname}}
          </td>
          <td>
            {{user.email}}
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      users: [],
      user: {
        FirstName: null,
        LastName: null,
        Email: null
      },
    }
  },
}
</script>

<style scoped>
form {
  position: fixed;
  top: 0;
  left: 0;
}
form input {

}
</style>
