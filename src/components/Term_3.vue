<template>
  <div class="flex-box el-marg">
    <div>Тип {{ typeidx + 1 }}</div>
    <div>
      <select>
        <option v-for="(list, idx) in cardOptions" v-bind:key="idx">{{
          list
        }}</option>
      </select>
    </div>
    <div class="deleteComp" v-on:click="removetype()">
      &#10006;
    </div>
  </div>
</template>

<script>
export default {
  name: "Term_3",
  props: ["removetype", "typeidx"],
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
    this.addType();
  },
  methods: {
    addType() {
      this.items.push([]);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
