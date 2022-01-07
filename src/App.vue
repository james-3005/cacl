<template>
  <div id="app">
    <div class="form">
      <label>Mệnh giá</label>
      <input type="number" v-model="price" style="height: 30px" />
    </div>
    <div class="form">
      <label>Thêm người</label>
      <input type="text" v-model="text" style="height: 30px" />
      <button @click="addPerson">Thêm</button>
    </div>
    <div class="form2" v-for="person in people" :key="person.name">
      <label>{{ `${person.name}: ${person.money}` }}</label>
      <img
        src="./assets/plus.svg"
        alt=""
        @click="() => calc('plus', person.id)"
      />
      <img
        src="./assets/minus.svg"
        alt=""
        @click="() => calc('minus', person.id)"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      price: 2,
      text: '',
      people: [
      ],
    };
  },
  methods: {
    calc(type, id) {
      if (type === "plus") this.people[id].money += parseInt(this.price);
      else this.people[id].money -= parseInt(this.price);
    },
    addPerson(){
      if(this.text)
      this.people.push({id: this.people.length, name: this.text, money: 0})
      this.text = ''
    }
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto&display=swap');
button {
  font-family: 'Roboto';
  outline: none;
  background-color: blanchedalmond;
  border: 1px solid gray;
  height: 100%;
}
label {
  font-family: 'Roboto';
  font-size: 20px;
  display: inline-block;
  width: 300px;
  font-weight: 400;
}
img {
  width: 50px;
  height: 30px;
  font-size: 40px;
}
body {
  padding: 0;
  margin: 0;
}
#app {
  width: 100vw;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
}
.form {
  width: 400px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  padding-bottom: 10px;
  border-bottom: 1px solid gray;
  margin: 10px
}
.form2 {
  width: 400px;
  height: 50px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  border-bottom: 1px solid gray;
}
</style>
