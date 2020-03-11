<template>
  <div id="pdct">
    <h1>{{name}}</h1>
    <form @submit.prevent="addName">
      <input type="text" placeholder="Enter name" v-model="inp" />
      <br />
      <label for="c">
        <input type="checkbox" v-model="checked" id="c" />check me
      </label>
    </form>
    <h5>{{inp}}</h5>
    <h3 :class="toggleClass()">{{age}}</h3>
    <button @click="addAge">add</button>
    <button @click="remAge">rem</button>
    <h3 v-if="age >= 18">of legal age</h3>
    <h3 v-else-if="age>= 0 && age < 18">Not of legal age</h3>
    <h3 v-else>yo dead</h3>
    <ul>
      <li v-for="(name, id) in names" :key="id" :class="{hov:active}">{{id}}. {{name}}</li>
    </ul>
  </div>
</template>
<script>
export default {
  name: "Product",
  data() {
    return {
      name: "Jimmy",
      inp: "",
      checked: false,
      age: 0,
      names: [],
      active: true
    };
  },
  methods: {
    addAge() {
      return (this.age += 1);
    },
    remAge() {
      return (this.age -= 1);
    },
    toggleClass() {
      return this.age >= 0 && this.age < 18
        ? "age"
        : this.age >= 18
        ? "age-high"
        : "age-low";
    },
    addName() {
      this.names = [...this.names, `${this.inp}: ${this.checked}`];
      this.inp = "";
      this.checked = false;
    }
  }
};
</script>
<style scoped>
#pdct {
  border: 1px solid;
}

.hov:hover {
  color: red;
  text-decoration: underline;
  cursor: pointer;
  font-weight: 900;
}

.age-low {
  color: red;
  border: 1px solid red;
  width: 10%;
  margin: 10px auto;
}
.age {
  color: rgb(95, 255, 103);
  border: 1px solid rgb(29, 255, 40);
  width: 10%;
  margin: 10px auto;
}
.age-high {
  color: rgb(36, 1, 236);
  border: 1px solid rgb(58, 127, 255);
  width: 10%;
  margin: 10px auto;
}

input[type="text"] {
  border-radius: 5px;
  border: 1px solid black;
  padding: 5px;
}
</style>