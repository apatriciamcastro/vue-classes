<template>
  <div id="dashboard">
    <h1>That's the dashboard!</h1>
    <p>You should only get here if you're authenticated!</p>
    <p>Your email address:{{email}}</p>
  </div>
</template>
<script>
import axios from "axios";

export default {
  data() {
    return {
      email: ""
    };
  },
  created() {
    axios
      .get("/users.json")
      .then(res => {
        console.log(res);
        const data = res.data; //extracting the data from the response
        const users = [];

        for (let key in data) { //loop through the keys to store it in an array
          const user = data[key]; //extract user data

          user.id = key; //assign an ID to each user
          users.push(user); //add user to the created array
        }
        console.log(users);
        this.email = users[0].email;
      })
      .catch(error => console.log(error));
  }
};
</script>

<style scoped>
h1,
p {
  text-align: center;
}

p {
  color: red;
}
</style>