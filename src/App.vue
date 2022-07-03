<template>
  <div>
    <header>
      <h1>Get a Good Advice</h1>
      <button @click="getAdvice">Get Advice</button>
    </header>
    <main>
      <h2>{{ advice }}</h2>
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      advice: "",
    };
  },
  methods: {
    async getAdvice() {
      const res = await fetch("https://api.adviceslip.com/advice");
      const data = await res.json();
      this.advice = data.slip.advice;
    },
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

body {
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #343a40;
  color: #e03131;
  font-family: "Finlandica", sans-serif;
}

header {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  gap: 32px;
  margin-top: 100px;
  margin-bottom: 50px;
}

h1 {
  box-shadow: rgba(50, 50, 93, 0.25) 0px 6px 12px -2px,
    rgba(0, 0, 0, 0.3) 0px 3px 7px -3px;
  border: 2px solid #f03e3e;
  border-radius: 12px;
  padding: 12px 24px;
}

button {
  color: #f03e3e;
  background: none;
  padding: 8px 12px;
  border-radius: 12px;
  border: 2px solid #f03e3e;
}

button:hover {
  opacity: 0.8;
  cursor: pointer;
}

main {
  max-width: 400px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
