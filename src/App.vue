<template>
  <div id="app" class="container">
    <h1>Number Multiples Generator</h1>
    
    <div class="input-section">
      <label for="number-input">Enter a number:</label>
      <input
        id="number-input"
        type="number"
        v-model.number="inputNumber"
        placeholder="Enter a number"
        min="1"
      />
    </div>

    <div v-if="multiples.length > 0" class="results-section">
      <h2>Multiples of {{ inputNumber }}:</h2>
      <ul class="multiples-list">
        <li v-for="(multiple, index) in multiples" :key="index">
          {{ multiple }}
        </li>
      </ul>
    </div>

    <div v-else-if="inputNumber && inputNumber > 0" class="no-results">
      <p>Enter a number to see its multiples</p>
    </div>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      inputNumber: null,
      maxMultiples: 20,
    };
  },
  computed: {
    multiples() {
      if (!this.inputNumber || this.inputNumber <= 0) {
        return [];
      }
      const result = [];
      for (let i = 1; i <= this.maxMultiples; i++) {
        result.push(this.inputNumber * i);
      }
      return result;
    },
  },
};
</script>

<style>
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
}

#app {
  min-height: 100vh;
  padding: 2rem;
  background: linear-gradient(135deg, #ff8c42 0%, #d28d1e 100%);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

.container {
  max-width: 600px;
  width: 100%;
  background: white;
  border-radius: 12px;
  padding: 2rem;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
}

h1 {
  margin-top: 0;
  color: #8b4513;
  text-align: center;
  font-size: 2rem;
}

.input-section {
  margin-bottom: 2rem;
}

label {
  display: block;
  margin-bottom: 0.5rem;
  color: #4e2c13;
  font-weight: 500;
}

input[type="number"] {
  width: 100%;
  padding: 0.75rem;
  font-size: 1.1rem;
  border: 2px solid #e0e0e0;
  border-radius: 8px;
  transition: border-color 0.3s;
}

input[type="number"]:focus {
  outline: none;
  border-color: #ff8c42;
}

.results-section {
  margin-top: 1.5rem;
}

h2 {
  color: #8b4513;
  font-size: 1.3rem;
  margin-bottom: 1rem;
}

.multiples-list {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 0.5rem;
  list-style: none;
  padding: 0;
  margin: 0;
}

.multiples-list li {
  background: #ffe4cc;
  padding: 0.75rem;
  text-align: center;
  border-radius: 6px;
  font-weight: 500;
  color: #8b4513;
  transition: background-color 0.2s;
  border: 1px solid #ff8c42;
}

.multiples-list li:hover {
  background: #ffd4a3;
}

.no-results {
  text-align: center;
  color: #999;
  margin-top: 1rem;
}
</style>
