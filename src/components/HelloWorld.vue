<template>
	<div class="hello">
		<h1>Random Fact</h1>
		<button @click="fetchData">Click Me!</button>
	</div>
</template>
<script>
export default {
	name: 'HelloWorld',
	props: {
		msg: String
	},
  methods: {
    fetchData() {
      fetch('https://facts-by-api-ninjas.p.rapidapi.com/v1/facts', {
        method: "GET",
        headers: {
          "X-RapidAPI-Key": 'your-api-key',
          "X-RapidAPI-Host": 'facts-by-api-ninjas.p.rapidapi.com',
        },
      })
        .then((response) => {
          response.json().then((data) => {
            this.fact = data[0].fact;
          });
        })
        .catch((err) => {
          console.error(err);
        });
    },
  },
};
</script>
<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
button {
	padding: 12px 32px;
	font-size: 16px;
	border-radius: 8px;
}
</style>