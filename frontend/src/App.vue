<template>
  <div>
    <h1>{{ message }}</h1>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return { message: "" };
  },
  mounted() {
    axios.get("/api/message")  // Proxy to FastAPI
      .then(response => { this.message = response.data.message; })
      .catch(error => { console.error(error); });
  }
};
</script>
