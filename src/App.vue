<template>
  <div id="app">
	
	  <Diagrams></Diagrams>
	    <p> При перезагрузке страницы отфильтрованный ряд остается.</p>
  </div>
</template>

<script>
import Diagrams from "@/components/Diagrams";

export default {
  name: "App",
  components: {
    Diagrams: Diagrams,
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
