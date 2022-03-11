<template>
  <div class="flex-box el-marg">
    <div>Диапазон {{ rangeidx + 1 }}</div>
    <div class="flex-box">
      <div>от</div>
      <input type="text" class="el-side-marg"/>
    </div>
    <div class="flex-box">
      <div>до</div>
      <input type="text" class="el-side-marg"/>
    </div>
    <div class="deleteComp" v-on:click="removeran()">
      &#10006;
    </div>
  </div>
</template>

<script>
export default {
  name: "Term_2",
  props: ["removeran", "rangeidx"],
  data() {
    return {
      items: [],
      termOptions: [
        "Возраст респондента",
        "Тип карты лояльности",
        "Статус карты лояльности"
      ],
      cardOptions: ["Gold", "Silver", "Bronze"],
      statusOptions: ["Активна", "Неактивна"],
      selectedTerm: "",
      selectedCard: null,
      selectedStatus: null
    };
  },
  mounted() {
    this.addRange();
  },
  methods: {
    addRange() {
      this.items.push([]);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
