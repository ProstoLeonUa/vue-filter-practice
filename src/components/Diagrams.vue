<template>
  <div class="diagrams">
    <div v-for="diagram in dataDiagram" :key="diagram.id" class="diagrams__item">
      {{diagram.name}}
      <span
        v-bind:style="{ background: diagram.color, height: diagram.height + 'px'}"
      ></span>
      <input
        type="range"
        min="100"
        max="300"
        v-model="diagram.height"
        @input="setStore(diagram.name, $event)"
      />
    </div>
    <button @click="filter">Фильтр</button>
  </div>
</template>


<script>
export default {
  methods: {
    setStore(name, newHeight) {
      localStorage[name] = newHeight.target.value;
    },
    filter() {
      this.sorted();
      localStorage.filter = true;
    },
    sorted() {
      this.dataDiagram.sort((a, b) => a.height - b.height);
    },
  },
  mounted() {
    for (let data of this.dataDiagram) {
      if (localStorage[data.name]) {
        data.height = +localStorage[data.name];
      }
    }
    if (localStorage.filter) {
      this.sorted();
    }
  },
  data() {
    return {
      dataDiagram: [
        {
          name: "Диаграма 1",
          color: "grey",
          height: 100,
          id: 1,
        },
        {
          name: "Диаграма 2",
          color: "green",
          height: 100,
          id: 2,
        },
        {
          name: "Диаграма 3",
          color: "yellow",
          height: 100,
          id: 3,
        },
        {
          name: "Диаграма 4",
          color: "black",
          height: 100,
          id: 4,
        },
        {
          name: "Диаграма 5",
          color: "purple",
          height: 100,
          id: 5,
        },
        {
          name: "Диаграма 6",
          color: "brown",
          height: 100,
          id: 6,
        },
        {
          name: "Диаграма 7",
          color: "blue",
          height: 100,
          id: 7,
        },
      ],
    };
  },
};
</script>

<style lang="scss">
.diagrams {
  display: flex;
  align-items: flex-end;
  height: 300px;
  &__item {
    border: 1px solid red;
    display: flex;
    flex-direction: column;
    justify-content: flex-end;
  }
}
</style>