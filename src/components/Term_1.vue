<template>
  <div>
    <form v-for="(list, idx) in terms" v-bind:key="idx">
      <div class="flex-box el-marg">
        <div>Условие {{ termidx + 1 }}</div>
        <div>
          <select v-model="selectedTerm">
            <option v-for="(list, idx) in termOptions" v-bind:key="idx">{{
              list
            }}</option>
          </select>
        </div>
        <div class="deleteComp" v-on:click="removefn()">
          &#10006;
        </div>
      </div>
      <div v-if="selectedTerm === 'Возраст респондента'">
        <div
          v-for="(range, idx) in rangesArr"
          :key="idx"
          :is="range"
          :rangeidx="idx"
          :removeran="deleteRange"
        ></div>
        <button type="button" v-on:click="addRange()" class="el-marg">
          Добавить диапазон
        </button>
      </div>
      <div v-if="selectedTerm === 'Тип карты лояльности'">
        <div
          v-for="(type, idx) in typesArr"
          :key="idx"
          :is="type"
          :removetype="deleteType"
          :typeidx="idx"
        ></div>
        <button type="button" v-on:click="addType()" class="el-marg">
          Добавить тип
        </button>
      </div>
      <div v-if="selectedTerm === 'Статус карты лояльности'">
        <div
          v-for="(stat, idx) in statusArr"
          :key="idx"
          :is="stat"
          :removestat="deleteStat"
          :statidx="idx"
        ></div>
        <button type="button" v-on:click="addStat()" class="el-marg">
          Добавить статус
        </button>
      </div>
    </form>
  </div>
</template>

<script>
import Term_2 from "./Term_2.vue";
import Term_3 from "./Term_3.vue";
import Term_4 from "./Term_4.vue";

export default {
  name: "Term_1",
  components: {
    Term_2,
    Term_3,
    Term_4
  },
  props: ["removefn", "termidx"],
  data() {
    return {
      rangesArr: [],
      typesArr: [],
      statusArr: [],
      terms: [],
      termOptions: [
        "Возраст респондента",
        "Тип карты лояльности",
        "Статус карты лояльности"
      ],
      cardOptions: ["Gold", "Silver", "Bronze"],
      statusOptions: ["Активна", "Неактивна"],
      selectedTerm: null,
      selectedCard: null,
      selectedStatus: null
    };
  },
  mounted() {
    this.addTerm();
    this.addRange();
    this.addType();
    this.addStat();
  },
  methods: {
    addRange() {
      this.rangesArr.push(Term_2);
    },
    deleteRange(rangesArr, range) {
      let number = this.rangesArr.indexOf(range);
      this.rangesArr.splice(number, 1);
    },
    addType() {
      this.typesArr.push(Term_3);
    },
    deleteType(typesArr, type) {
      let number = this.typesArr.indexOf(type);
      this.typesArr.splice(number, 1);
    },
    addStat() {
      this.statusArr.push(Term_4);
    },
    deleteStat(statusArr, stat) {
      let number = this.statusArr.indexOf(stat);
      this.statusArr.splice(number, 1);
    },
    addTerm() {
      this.terms.push("");
    },
    deleteTerm(terms, list) {
      let number = terms.indexOf(list);
      terms.splice(number, 1);
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>
