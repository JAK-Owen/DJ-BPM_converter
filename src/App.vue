<script>
export default {
  data() {
    return {
      straightBPM: null,
      tripletBPM: null,
      result: '',
      currentConverter: 'Straight to Triplet'
    };
  },
  methods: {
    convertToTriplet() {
      if (!isNaN(this.straightBPM)) {
        const tripletBPM = this.straightBPM * 3 / 2;
        this.result = `Triplet Feel BPM: ${tripletBPM.toFixed(2)}`;
      } else {
        this.result = 'Invalid input. Please enter a valid BPM.';
      }
    },
    convertToStraight() {
      if (!isNaN(this.tripletBPM)) {
        const straightBPM = this.tripletBPM * 2 / 3;
        this.result = `Straight Feel BPM: ${straightBPM.toFixed(2)}`;
      } else {
        this.result = 'Invalid input. Please enter a valid BPM.';
      }
    },
    toggleConverter() {
      this.currentConverter = this.currentConverter === 'Straight to Triplet' ? 'Triplet to Straight' : 'Straight to Triplet';
      this.result = '';
    }
  }
};
</script>


<template>
  <div class="container">
    <h1>Triplet / Straight - BPM Converter</h1>
    
    <div class="converter-container">
      <button @click="toggleConverter" class="toggle-button">{{ currentConverter }}</button>
    </div>

    <div class="input-container">
      <div v-if="currentConverter === 'Straight to Triplet'">
        <input v-model="straightBPM" type="number" id="straightBPM" placeholder="e.g., 120">
        <button @click="convertToTriplet">Convert to Triplet Feel</button>
      </div>

      <div v-else>
        <input v-model="tripletBPM" type="number" id="tripletBPM" placeholder="e.g., 100">
        <button @click="convertToStraight">Convert to Straight Feel</button>
      </div>
    </div>

    <p v-if="result">{{ result }}</p>
  </div>
</template>



<style>

h1 {
  padding: 40px;
}

.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  text-align: center;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.converter-container {
  margin-bottom: 20px;
}

.toggle-button {
  background-color: #ffffff;
  color: #333333;
  border: none;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 18px;
}

.input-container {
  display: flex;
  flex-direction: column;
  align-items: center;
}

input {
  background-color: #333333;
  color: #ffffff;
  border: 1px solid #ffffff;
  margin: 10px 0;
  padding: 10px;
  
  border-radius: 5px;
  width: 150px;
}

button {
  background-color: #333333;
  color: #ffffff;
  border: 1px solid #ffffff;
  padding: 10px 20px;
  border-radius: 5px;
  cursor: pointer;
  font-size: 16px;
}

p {
  margin: 20px 0;
  font-size: 18px;
}
</style>
