<template>
  <div id="app">
    <div class="el-marg">Добавить опрос</div>
    <div
      v-for="(component, idx) in componentsArr"
      :key="idx"
      :is="component"
      :removefn="deleteComp"
      :termidx="idx"
    ></div>
    <button type="button" v-on:click="addComp()" class="el-marg">
      Добавить условие
    </button>
  </div>
</template>

<script>
import Term_1 from "./components/Term_1.vue";
import Term_2 from "./components/Term_2.vue";
import Term_3 from "./components/Term_3.vue";
import Term_4 from "./components/Term_4.vue";

export default {
  name: "App",
  data() {
    return {
      componentsArr: []
    };
  },
  components: {
    Term_1,
    Term_2,
    Term_3,
    Term_4
  },
  methods: {
    addComp() {
      this.componentsArr.push(Term_1);
    },
    deleteComp(component) {
      let number = this.componentsArr.indexOf(component);
      this.componentsArr.splice(number, 1);
    }
  }
};
</script>

<style></style>
