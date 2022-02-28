<!-- Source:https://www.section.io/engineering-education/how-to-interact-with-an-api-from-a-vuejs-application/  -->
<!-- Source:https://www.boredapi.com/ -->


<template>
  <div v-bind="activity">
      <h1><i>If you are bored...</i></h1>
      <p>{{ activity.activity }}</p>
      <button @click="reloadPage">Something else</button>
  </div>
</template>

<script>
const URL = "http://www.boredapi.com/api/activity/";


export default {
  data() {
    return {
      activity: [],
    };
  },

  methods: {
    reloadPage() {
      window.location.reload();
    },

    async getData() {
      try {
        let response = await fetch(URL);
        this.activity = await response.json();;
      } catch (error) {
        console.log(error);
      }
    },
  },

  created() {
    this.getData();
  },
};
</script>

<style>
  div {
    text-align: center;
    margin-top: 2em;
  }

  p {
    font-size: 25px;
  }

  button {
    font-size: 15px;
    padding: 10px;
    background-color: lightskyblue;
  }

</style>